---
title: Calcular métricas para avaliar a qualidade do modelo de machine learning
description: Saiba como calcular métricas para avaliar e verificar a qualidade do modelo de machine learning com o ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73975836"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="90446-103">Calcular métricas para avaliar a qualidade do modelo de machine learning</span><span class="sxs-lookup"><span data-stu-id="90446-103">Calculate metrics to evaluate machine learning model quality</span></span>

> [!NOTE]
> <span data-ttu-id="90446-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="90446-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="90446-105">Para mais informações, visite a página [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="90446-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="90446-106">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="90446-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="90446-107">Para obter mais informações, consulte as notas de versão no [repo Dotnet/Machinelearning GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="90446-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="90446-108">Como avaliar a qualidade depois de treinar o modelo?</span><span class="sxs-lookup"><span data-stu-id="90446-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="90446-109">Cada tarefa de aprendizado de máquina expõe métricas de avaliação da qualidade.</span><span class="sxs-lookup"><span data-stu-id="90446-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="90446-110">Você pode usar o 'contexto' correspondente da tarefa para avaliar o modelo, como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="90446-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
