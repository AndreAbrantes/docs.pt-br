---
title: 'Tutorial: Categorize flores de íris - agrupamento k-significa'
description: Saiba como usar o ML.NET em um cenário de clustering
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: fe9c3eb1313fbacf512710f6872c543dca281b17
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607422"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Tutorial: Categorize flores de íris usando agrupamento de meios k com ML.NET

Este tutorial ilustra como usar o ML.NET para criar um [modelo de clustering](../resources/tasks.md#clustering) para o [conjunto de dados de flor Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Compreender o problema
> - Selecionar a tarefa de aprendizado de máquina apropriada
> - Preparar os dados
> - Carregar e transformar os dados
> - Escolher um algoritmo de aprendizado
> - Treinar o modelo
> - Usar o modelo para previsões

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou posterior ou Visual Studio 2017 versão 15.6 ou posterior com a carga de trabalho ".NET Core cross-platform development" instalada.

## <a name="understand-the-problem"></a>Compreender o problema

Esse problema abrange como dividir o conjunto de flores Iris em grupos diferentes com base nas características da flor. Essas características são o comprimento e largura de uma sépala e o comprimento e a largura de uma pétala. Para este tutorial, considere que o tipo de cada flor é desconhecido. Você deseja conhecer a estrutura de um conjunto de dados por meio de suas características e prever como uma instância de dados se encaixa nessa estrutura.

## <a name="select-the-appropriate-machine-learning-task"></a>Selecionar a tarefa de aprendizado de máquina apropriada

Como você não sabe a qual grupo cada flor pertence, escolha a tarefa [aprendizado de máquina não supervisionado](../resources/glossary.md#unsupervised-machine-learning). Para dividir um conjunto de dados em grupos de forma que os elementos no mesmo grupo sejam mais semelhantes uns aos outros do que aos elementos de outros grupos, use a tarefa de aprendizado de máquina [clustering](../resources/tasks.md#clustering).

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. Abra o Visual Studio. Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus. Na caixa de diálogo **Novo Projeto**, selecione o nó **Visual C#** seguido pelo nó **.NET Core**. Em seguida, selecione o modelo de projeto **Aplicativo de console (.NET Core)**. Na caixa de texto **Nome**, digite "IrisFlowerClustering" e, em seguida, selecione o botão **OK**.

1. Crie um diretório chamado *Dados* em seu projeto para armazenar o conjunto de dados e arquivos de modelo:

    No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Nova Pasta**. Digite "Dados" e pressione Enter.

1. Instale o pacote **Microsoft.ML** NuGet:

    No **Gerenciador de Soluções**, clique com o botão direito no projeto e escolha **Gerenciar Pacotes NuGet**. Escolha "nuget.org" como a origem do pacote, selecione a guia **Procurar,** procure **Microsoft.ML** e selecione o botão **Instalar.** Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.

## <a name="prepare-the-data"></a>Preparar os dados

1. Baixe o conjunto de dados [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) e salve-o na pasta *Dados* que você criou na etapa anterior. Para obter mais informações sobre o conjunto de dados Iris, confira a página da Wikipédia [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) (Conjunto de dados de flor Iris) e a página [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) (Conjunto de dados Iris), que é a fonte do conjunto de dados.

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *iris.data* e selecione **Propriedades**. Em **Avançado,** altere o valor de **Copiar para Diretório de Saída** para Copiar se mais **novo**.

O arquivo *iris.data* contém cinco colunas que representam:

- comprimento do sepápal em centímetros
- largura do sepal em centímetros
- comprimento pétala em centímetros
- largura pétala em centímetros
- o tipo de flor Iris

Para exemplificar o clustering, este tutorial ignora a última coluna.

## <a name="create-data-classes"></a>Criar classes de dados

Crie classes para os dados de entrada e as previsões:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *IrisData.cs*. Em seguida, selecione o botão **Adicionar**.
1. Adicione a seguinte diretiva `using` ao novo arquivo:

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

Remova a definição de classe existente e adicione o código a seguir, que define as classes `IrisData` e `ClusterPrediction`, para o arquivo *IrisData.cs*:

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

`IrisData` é a classe de dados de entrada e tem definições de cada característica provenientes do conjunto de dados. Use o atributo [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) para especificar os índices das colunas de origem no arquivo de conjunto de dados.

A classe `ClusterPrediction` representa a saída do modelo de clustering aplicado a uma instância de `IrisData`. Use o atributo [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) para associar os campos `PredictedClusterId` e `Distances` às colunas **PredictedLabel** e **Score**, respectivamente. No caso da tarefa clustering, essas colunas têm o seguinte significado:

- A coluna **PredictedLabel** contém a ID do cluster previsto.
- A coluna **Score** contém uma matriz com as distâncias euclidianas quadradas para os centroides de cluster. O comprimento da matriz é igual ao número de clusters.

> [!NOTE]
> Use o tipo `float` para representar valores de ponto flutuante nas classes de dados de entrada e previsão.

## <a name="define-data-and-model-paths"></a>Definir dados e caminhos de modelo

Volte para o arquivo *Program.cs* e adicione dois campos para armazenar os caminhos no arquivo de conjunto de dados e no arquivo para salvar o modelo:

- `_dataPath` contém o caminho para o arquivo com o conjunto de dados usado para treinar o modelo.
- `_modelPath` contém o caminho para o arquivo em que o modelo treinado está armazenado.

Adicione o seguinte código logo acima do método `Main` para especificar estes caminhos:

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

Para fazer com que o código anterior seja compilado, adicione as seguintes diretivas `using` ao início do arquivo *Program.cs*:

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Criar o contexto de ML

Adicione as seguintes diretivas `using` adicionais ao início do arquivo *Program.cs*:

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

No método `Main`, substitua a linha `Console.WriteLine("Hello World!");` pelo seguinte código:

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

A classe <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> representa o ambiente de aprendizado de máquina e fornece mecanismos para pontos de entrada e de log para carregamento de dados, treinamento do modelo, previsão e outras tarefas. Isso é comparável conceitualmente ao uso de `DbContext` no Entity Framework.

## <a name="set-up-data-loading"></a>Configurar o carregamento de dados

Adicione o seguinte `Main` código ao método para configurar a maneira de carregar dados:

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

O método de [ `MLContext.Data.LoadFromTextFile` extensão](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) genérico infere o `IrisData` esquema do <xref:Microsoft.ML.IDataView> conjunto de dados do tipo fornecido e retorna que pode ser usado como entrada para transformadores.

## <a name="create-a-learning-pipeline"></a>Criar um pipeline de aprendizado

Para este tutorial, o pipeline de aprendizado da tarefa de clustering consiste nas duas seguintes etapas:

- concatenar colunas carregadas em uma coluna **Recursos**, que é usada por um treinador de clustering;
- usar um treinador <xref:Microsoft.ML.Trainers.KMeansTrainer> para treinar o modelo usando o algoritmo de cluster K-means++.

Adicione o seguinte código ao método `Main`:

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

O código especifica que o conjunto de dados deve ser dividido em três clusters.

## <a name="train-the-model"></a>Treinar o modelo

As etapas adicionadas nas seções anteriores prepararam o pipeline para treinamento, no entanto, nenhuma foi executada. Adicione a seguinte linha ao método `Main` para executar o carregamento de dados e o treinamento do modelo:

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Salvar o modelo

Neste ponto, você tem um modelo que pode ser integrado em qualquer um dos seus aplicativos .NET existentes ou novos. Para salvar o modelo em um arquivo .zip, adicione o seguinte código ao método `Main`:

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Usar o modelo para previsões

Para fazer previsões, use a classe <xref:Microsoft.ML.PredictionEngine%602> que usa instâncias do tipo de entrada por meio do pipeline transformador e produz instâncias do tipo de saída. Adicione a seguinte linha ao método `Main` para criar uma instância dessa classe:

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite realizar uma previsão em uma única instância de dados. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca. É aceitável usar em ambientes de um único fio ou protótipo. Para melhorar o desempenho e a segurança `PredictionEnginePool` dos fios nos [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ambientes de produção, use o serviço, que cria um objeto para uso em toda a sua aplicação. Consulte este guia sobre como [usar `PredictionEnginePool` em uma API web ASP.NET.](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)

> [!NOTE]
> A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.

Crie a classe `TestIrisData` para hospedar as instâncias de dados de teste:

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.
1. Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *TestIrisData.cs*. Em seguida, selecione o botão **Adicionar**.
1. Modifique a classe para ser estática, como no exemplo a seguir:

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

Este tutorial apresenta uma instância de dados de Iris dentro dessa classe. Você pode adicionar outros cenários para fazer experimentos com o modelo. Adicione o seguinte código à classe `TestIrisData`:

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

Para descobrir a qual cluster o item especificado pertence, volte para o arquivo *Program.cs* e adicione o seguinte código no método `Main`:

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

Execute o programa para ver qual cluster contém a instância de dados especificada e a distância quadrada daquela instância aos centroides do cluster. Os resultados devem ser semelhantes aos seguintes:

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Parabéns! Você agora construiu um modelo de aprendizado de máquina para clustering de Iris e o usou para fazer previsões. Encontre o código-fonte deste tutorial no repositório do GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a:
> [!div class="checklist"]
>
> - Compreender o problema
> - Selecionar a tarefa de aprendizado de máquina apropriada
> - Preparar os dados
> - Carregar e transformar os dados
> - Escolher um algoritmo de aprendizado
> - Treinar o modelo
> - Usar o modelo para previsões

Confira nosso repositório GitHub para continuar aprendendo e encontrar mais amostras.
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/)
