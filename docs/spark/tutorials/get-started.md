---
title: Introdução ao .NET para Apache Spark
description: Descubra como executar um .NET para Apache Spark aplicativo usando o .NET Core no Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577003"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Tutorial: Introdução ao .NET para Apache Spark

Este tutorial ensina como executar um .NET para Apache Spark aplicativo usando o .NET Core no Windows.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
> * Preparar seu ambiente do Windows para .NET para Apache Spark
> * Baixe o **Microsoft. Spark. Worker**
> * Compilar e executar um aplicativo .NET simples para Apache Spark

## <a name="prepare-your-environment"></a>Preparar seu ambiente

Antes de começar, verifique se você pode executar `dotnet` `mvn`, `java`,, `spark-shell` da linha de comando. Se seu ambiente já estiver preparado, você poderá pular para a próxima seção. Se você não puder executar um ou todos os comandos, siga as etapas abaixo.

1. Baixe e instale o [SDK do .NET Core 2.1 x](https://dotnet.microsoft.com/download/dotnet-core/2.1). A instalação do SDK adiciona `dotnet` o ferramentas ao seu caminho. Use o comando `dotnet --version` do PowerShell para verificar a instalação.

2. Instale o [visual studio 2017](https://www.visualstudio.com/downloads/) ou o [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) com as atualizações mais recentes. Você pode usar o Community, o Professional ou o Enterprise. A versão da Comunidade é gratuita.

   Escolha as seguintes cargas de trabalho durante a instalação:
      * Desenvolvimento de área de trabalho do .NET
          * Todos os componentes necessários
          * Ferramentas de desenvolvimento do .NET Framework 4.6.1
      * Desenvolvimento de plataforma cruzada do .NET Core
          * Todos os componentes necessários

3. Instale o [Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

    * Selecione a versão apropriada para seu sistema operacional. Por exemplo, selecione **JDK-8u201-Windows-x64. exe** para um computador x64 do Windows.
    * Use o comando `java -version` do PowerShell para verificar a instalação.

4. Instale o [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi).
    * Baixe o [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).
    * Extrair para um diretório local. Por exemplo, `c:\bin\apache-maven-3.6.0\`.
    * Adicione o Apache Maven à sua [variável de ambiente path](https://www.java.com/en/download/help/path.xml). Se você tiver extraído para `c:\bin\apache-maven-3.6.0\`o, você adicionaria `c:\bin\apache-maven-3.6.0\bin` ao seu caminho.
    * Use o comando `mvn -version` do PowerShell para verificar a instalação.

5. Instale o [Apache Spark 2.3 +](https://spark.apache.org/downloads.html). Não há suporte para o Apache Spark 2.4 +.
    * Baixe [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) e extraia-o em uma pasta local usando uma ferramenta como [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/). Por exemplo, você pode extraí-lo `c:\bin\spark-2.3.2-bin-hadoop2.7\`para.
    * Adicione Apache Spark à [variável de ambiente path](https://www.java.com/en/download/help/path.xml). Se você tiver extraído para `c:\bin\spark-2.3.2-bin-hadoop2.7\`o, você adicionaria `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` ao seu caminho.
    * Adicione uma [nova variável](https://www.java.com/en/download/help/path.xml) de ambiente `SPARK_HOME`chamada. Se você tiver extraído `C:\bin\spark-2.3.2-bin-hadoop2.7\`para `C:\bin\spark-2.3.2-bin-hadoop2.7\` , use para o **valor da variável**.
    * Verifique se você pode executar `spark-shell` a partir da linha de comando.

6. Configurar o [WinUtils](https://github.com/steveloughran/winutils).
    * Baixe o binário **winutils. exe** do [repositório winutils](https://github.com/steveloughran/winutils). Selecione a versão do Hadoop com a qual a distribuição do Spark foi compilada. Por exemplo, você usa o **Hadoop-2.7.1** para o **Spark 2.3.2**. A versão do Hadoop é anotada no final do nome da pasta de instalação do Spark.
    * Salve o binário **winutils. exe** em um diretório de sua escolha. Por exemplo, `c:\hadoop\bin`.
    * Defina `HADOOP_HOME` para refletir o diretório com **winutils. exe** sem `bin`. Por exemplo, `c:\hadoop`.
    * Defina a variável de ambiente PATH como `%HADOOP_HOME%\bin`include.

Verifique se você `dotnet`pode executar `mvn`, `java`,, `spark-shell` da linha de comando antes de passar para a próxima seção.

## <a name="download-the-microsoftsparkworker-release"></a>Baixe a versão Microsoft. Spark. Worker

1. Baixe a versão [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) do .net para Apache Spark página de versões do GitHub para seu computador local. Por exemplo, você pode baixá-lo no caminho, `c:\bin\Microsoft.Spark.Worker\`.

2. Crie uma [nova variável](https://www.java.com/en/download/help/path.xml) de ambiente `DotnetWorkerPath` chamada e defina-a para o diretório em que você baixou e extraiu o **Microsoft. Spark. Worker**. Por exemplo, `c:\bin\Microsoft.Spark.Worker`.

## <a name="clone-the-net-for-apache-spark-github-repo"></a>Clonar o .NET para Apache Spark repositório GitHub

Use o comando [GitBash](https://gitforwindows.org/) a seguir para clonar o .net para Apache Spark repositório em seu computador.

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>Gravar um aplicativo .NET para Apache Spark

1. Abra o **Visual Studio** e navegue até **arquivo > criar novo projeto > aplicativo de console (.NET Core)** . Nomeie o aplicativo **HelloSpark**.

2. Instale o [pacote NuGet do Microsoft. Spark](https://www.nuget.org/profiles/spark). Para obter mais informações sobre como instalar pacotes NuGet, consulte [diferentes maneiras de instalar um pacote NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).

3. No **Gerenciador de soluções**, abra **Program.cs** e escreva o código C# a seguir:

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. Compile a solução.

## <a name="run-your-net-for-apache-spark-app"></a>Execute seu .NET para Apache Spark aplicativo

1. Abra o **PowerShell** e altere o diretório para a pasta onde seu aplicativo está armazenado.

   ```powershell
   cd <your-app-output-directory>
   ```

2. Crie um arquivo chamado **People. JSON** com o seguinte conteúdo:

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. Use o seguinte comando do PowerShell para executar seu aplicativo:

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

Parabéns! Você criou e executou com êxito um .NET para Apache Spark aplicativo.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> * Preparar seu ambiente do Windows para .NET para Apache Spark
> * Baixe o **Microsoft. Spark. Worker**
> * Compilar e executar um aplicativo .NET simples para Apache Spark

Confira a página de recursos para saber mais.
> [!div class="nextstepaction"]
> [.NET para recursos Apache Spark](../resources/index.md)