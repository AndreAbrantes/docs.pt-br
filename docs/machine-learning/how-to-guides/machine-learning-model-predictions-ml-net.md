---
title: Fazer previsões com um modelo treinado
description: Aprenda a fazer previsões usando um modelo treinado
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977041"
---
# <a name="make-predictions-with-a-trained-model"></a>Fazer previsões com um modelo treinado

Saiba como usar um modelo treinado para fazer previsões

## <a name="create-data-models"></a>Criar modelo de dados

### <a name="input-data"></a>Dados de entrada

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="output-data"></a>Dados de saída

Como os nomes de coluna de entrada `Features` e `Label`, do ML.NET tem nomes padrão para as colunas de valor previsto produzidas por um modelo. Dependendo da tarefa, o nome pode diferir.

Como o algoritmo usado nesta amostra é um algoritmo de regressão `Score` linear, o [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) nome padrão `PredictedPrice` da coluna de saída é o que é definido pelo atributo na propriedade.

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a>Configurar um pipeline de previsão

Seja fazendo uma previsão única ou em lotes, o pipeline de previsão precisa ser carregado no aplicativo. Esse pipeline contém as transformações de pré-processamento de dados, bem como o modelo treinado. O snippet de código a seguir carrega o pipeline de previsão de um arquivo chamado `model.zip`.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Previsão única

Para fazer uma única [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) previsão, crie um utilizando o pipeline de previsão carregado.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Em seguida, [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) use o método e passe seus dados de entrada como parâmetro. Observe que [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) o uso do método não [`IDataView`](xref:Microsoft.ML.IDataView)requer que a entrada seja um ). Isso ocorre porque ele internaliza convenientemente a manipulação do tipo de dados de entrada para que você possa passar um objeto do tipo de dados de entrada. Além disso, uma vez que `CurrentPrice` é o destino ou o rótulo que você está tentando prever usando novos dados, supõe-se não há nenhum valor para ele no momento.

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

Se você acessar a propriedade `Score` do objeto `prediction`, deverá obter um valor semelhante ao `150079`.

## <a name="multiple-predictions"></a>Múltiplas previsões

Dado os seguintes dados, carregue-os em um [`IDataView`](xref:Microsoft.ML.IDataView). Neste caso, o nome [`IDataView`](xref:Microsoft.ML.IDataView) `inputData`do é. Uma vez que `CurrentPrice` é o destino ou o rótulo que você está tentando prever usando novos dados, supõe-se que não há valor para ele no momento.

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

Em seguida, [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) use o método para aplicar as transformações de dados e gerar previsões.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Inspecione os valores [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) previstos usando o método.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Os valores previstos da coluna de pontuação devem ser semelhantes aos seguintes:

| Observação | Previsão |
|---|---|
| 1 | 144638,2 |
| 2 | 150079,4 |
| 3 | 107789,8 |
