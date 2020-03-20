---
title: Processamento em lote com .NET para tutorial apache spark
description: Aprenda a fazer processamento em lote usando .NET para Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: 460c37e66c2c0a8a9b197a9abaff9eead842bdeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187562"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Tutorial: Faça processamento em lote com .NET para Apache Spark

Neste tutorial, você aprende a fazer processamento em lote usando .NET para Apache Spark. O processamento em lote é a transformação dos dados em repouso, o que significa que os dados de origem já foram carregados no armazenamento de dados.

O processamento em lote é geralmente realizado em conjuntos de dados grandes e planos que precisam ser preparados para análises posteriores. Processamento de registros e armazenamento de dados são cenários comuns de processamento de lotes. Neste cenário, você analisa informações sobre projetos do GitHub, como o número de vezes que diferentes projetos foram bifurcados ou como projetos recentemente foram atualizados.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Criar e executar um aplicativo .NET para Apache Spark
> * Leia dados em um DataFrame e prepare-os para análise
> * Processe os dados usando o Spark SQL

## <a name="prerequisites"></a>Pré-requisitos

Se esta é a sua primeira vez usando .NET para Apache Spark, confira o tutorial [.NET para Apache Spark](../tutorials/get-started.md) para aprender como preparar seu ambiente e executar o seu primeiro aplicativo .NET para Apache Spark.

## <a name="download-the-sample-data"></a>Baixe os dados de exemplo

[O GHTorrent](http://ghtorrent.org/) monitora todos os eventos públicos do GitHub, como informações sobre projetos, compromissos e observadores, e armazena os eventos e sua estrutura em bancos de dados. Os dados coletados em diferentes períodos de tempo estão disponíveis como arquivos para download. Como os arquivos de despejo são muito grandes, este guia usa uma [versão truncada do arquivo de despejo](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) que pode ser baixado do GitHub.

> [!NOTE]
> O conjunto de dados GHTorrent é distribuído um esquema de licenciamento duplo[(Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)). Para usos não comerciais (incluindo, mas não limitado a, usos educacionais, de pesquisa ou pessoais), o conjunto de dados é distribuído a [licença CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. No prompt de comando, execute os seguintes comandos para criar um novo aplicativo de console:

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   O `dotnet` comando `new` cria uma `console` aplicação de tipo para você. O `-o` parâmetro cria um diretório chamado *mySparkBatchApp* onde seu aplicativo é armazenado e o preenche com os arquivos necessários. O `cd mySparkBatchApp` comando altera o diretório para o diretório de aplicativos que você acabou de criar.

1. Para usar o .NET para Apache Spark em um aplicativo, instale o pacote Microsoft.Spark. No console, execute o seguinte comando:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Criar uma SparkSession

1. Adicione as `using` seguintes instruções adicionais à parte superior do arquivo *Program.cs* no *mySparkBatchApp*.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Adicione o seguinte código ao namespace do projeto. *s_referenceData* é usado mais tarde no programa para filtrar com base na data.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Adicione o seguinte código dentro do seu método Principal para estabelecer uma nova SparkSession. O SparkSession é o ponto de entrada para programar o Spark com a API Dataset e DataFrame. Ao chamar `spark` o objeto, você pode acessar a funcionalidade Spark e DataFrame durante todo o seu programa.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Preparar os dados

1. Leia o arquivo `DataFrame`de entrada em um , que é uma coleta distribuída de dados organizados em colunas nomeadas. Você pode definir as colunas <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>para seus dados através de . Use <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> o método para exibir os dados em seu DataFrame. Certifique-se de atualizar o caminho do arquivo CSV para a localização dos dados do GitHub que você baixou.

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. Use <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> o método para soltar linhas com valores <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> NA (nulos) e o método para remover certas colunas de seus dados. Isso ajuda a evitar erros se você tentar analisar dados nulos ou colunas que não são relevantes para sua análise final.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Analisar os dados

O Spark SQL permite que você faça chamadas SQL em seus dados. É comum combinar funções definidas pelo usuário e Spark SQL para aplicar uma função definida pelo usuário a todas as linhas do dataframe.

Você pode ligar `spark.Sql` especificamente para imitar chamadas SQL padrão vistas em outros tipos de aplicativos. Você também pode chamar <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> métodos como e combinar especificamente, filtrar e executar cálculos em seus dados.

O objetivo deste aplicativo é obter algumas informações sobre os dados dos projetos do GitHub. Adicione os seguintes trechos de código ao seu programa para analisar os dados.

1. Adicione o seguinte bloco de código encontra o número de vezes que cada idioma foi bifurcado. Primeiro, os dados são agrupados por linguagem. Em seguida, o número médio de garfos de cada língua é tomado.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Adicione o seguinte bloco de código para ordenar o número médio de garfos em ordem descendente para ver quais idiomas são os mais bifurcados. Ou seja, o maior número de garfos aparecerá primeiro.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. O próximo bloco de código mostra como os projetos foram atualizados recentemente. Você registra uma nova função definida pelo usuário chamada *MyUDF* e compara-a com uma data, *s_referenceDate*, que foi declarada no início do tutorial. A data para cada projeto é comparada com a data de referência. Em seguida, o Spark SQL é usado para chamar o UDF em cada linha de dados para analisar cada projeto no conjunto de dados.

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);
   cleanedProjects.CreateOrReplaceTempView("dateView");

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. Chamada `spark.Stop()` para acabar com a Sessão de Faíscas.

## <a name="use-spark-submit-to-run-your-app"></a>Use o spark-submit para executar seu aplicativo

1. Use o seguinte comando para criar seu aplicativo .NET:

   ```dotnetcli
   dotnet build
   ```

1. Execute seu `spark-submit`aplicativo com . Certifique-se de atualizar o seguinte comando com os caminhos reais para o arquivo de jarro do Microsoft Spark.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Obter o código

Você pode ver a [solução completa](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) no GitHub.

## <a name="next-steps"></a>Próximas etapas

Avance para o próximo artigo para saber como processar dados de streaming com .NET para Apache Spark.
> [!div class="nextstepaction"]
> [Tutorial: Streaming estruturado com .NET para Apache Spark](streaming.md)
