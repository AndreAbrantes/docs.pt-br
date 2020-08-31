---
title: 'Tutorial: inspeção visual automatizada usando o aprendizado de transferência'
description: Este tutorial ilustra como usar o aprendizado de transferência para treinar um modelo de aprendizado profundo do TensorFlow no ML.NET usando a API de detecção de imagem para classificar imagens de superfícies concretas como rachadas ou não rachadas.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 593897b31c86e79db2376dde94f3e5c87fdf8289
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89052817"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="6f6f4-103">Tutorial: inspeção visual automatizada usando o aprendizado de transferência com a API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="6f6f4-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="6f6f4-104">Saiba como treinar um modelo de aprendizado profundo personalizado usando o aprendizado de transferência, um modelo TensorFlow pretreinado e a API de classificação de imagem ML.NET para classificar imagens de superfícies concretas como rachadas ou sem cracking.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="6f6f4-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6f6f4-106">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="6f6f4-106">Understand the problem</span></span>
> - <span data-ttu-id="6f6f4-107">Saiba mais sobre a API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="6f6f4-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="6f6f4-108">Entender o modelo pretreinado</span><span class="sxs-lookup"><span data-stu-id="6f6f4-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="6f6f4-109">Usar o aprendizado de transferência para treinar um modelo de classificação de imagem TensorFlow personalizado</span><span class="sxs-lookup"><span data-stu-id="6f6f4-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="6f6f4-110">Classificar imagens com o modelo personalizado</span><span class="sxs-lookup"><span data-stu-id="6f6f4-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f6f4-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6f6f4-111">Prerequisites</span></span>

- <span data-ttu-id="6f6f4-112">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou posterior ou visual Studio 2017 versão 15,6 ou posterior com a carga de trabalho "desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="6f6f4-113">Visão geral do exemplo de aprendizado de transferência de classificação de imagem</span><span class="sxs-lookup"><span data-stu-id="6f6f4-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="6f6f4-114">Este exemplo é um aplicativo de console C# .NET Core que classifica imagens usando um modelo de TensorFlow de aprendizado profundo pretreinado.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="6f6f4-115">O código para este exemplo pode ser encontrado no [repositório dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="6f6f4-116">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="6f6f4-116">Understand the problem</span></span>

<span data-ttu-id="6f6f4-117">A classificação de imagem é um problema de pesquisa Visual computacional.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="6f6f4-118">A classificação de imagem usa uma imagem como entrada e a categoriza em uma classe prescrita.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="6f6f4-119">Alguns cenários em que a classificação de imagem é útil incluem:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="6f6f4-120">Reconhecimento de rosto</span><span class="sxs-lookup"><span data-stu-id="6f6f4-120">Facial recognition</span></span>
- <span data-ttu-id="6f6f4-121">Detecção de Emoções</span><span class="sxs-lookup"><span data-stu-id="6f6f4-121">Emotion detection</span></span>
- <span data-ttu-id="6f6f4-122">Diagnóstico médico</span><span class="sxs-lookup"><span data-stu-id="6f6f4-122">Medical diagnosis</span></span>
- <span data-ttu-id="6f6f4-123">Detecção de monumentos</span><span class="sxs-lookup"><span data-stu-id="6f6f4-123">Landmark detection</span></span>

<span data-ttu-id="6f6f4-124">Este tutorial treina um modelo de classificação de imagem personalizada para executar a inspeção visual automatizada de decks de ponte para identificar estruturas que estão danificadas por rachaduras.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="6f6f4-125">API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="6f6f4-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="6f6f4-126">O ML.NET fornece várias maneiras de executar a classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="6f6f4-127">Este tutorial aplica-se ao aprendizado de transferência usando a API de classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="6f6f4-128">A API de classificação de imagem usa [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET), uma biblioteca de nível baixo que fornece associações em C# para a API do TensorFlow C++.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="6f6f4-129">O que é a transferência de aprendizado?</span><span class="sxs-lookup"><span data-stu-id="6f6f4-129">What is transfer learning?</span></span>

<span data-ttu-id="6f6f4-130">O aprendizado de transferência aplica o conhecimento obtido da solução de um problema para outro problema relacionado.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="6f6f4-131">Treinar um modelo de aprendizado profundo do zero exige a definição de vários parâmetros, uma grande quantidade de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU).</span><span class="sxs-lookup"><span data-stu-id="6f6f4-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="6f6f4-132">Usar um modelo pretreinado junto com o aprendizado de transferência permite que você Modele o processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="6f6f4-133">Processo de treinamento</span><span class="sxs-lookup"><span data-stu-id="6f6f4-133">Training process</span></span>

<span data-ttu-id="6f6f4-134">A API de classificação de imagem inicia o processo de treinamento carregando um modelo de TensorFlow pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="6f6f4-135">O processo de treinamento consiste em duas etapas:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="6f6f4-136">Fase de afunilamento</span><span class="sxs-lookup"><span data-stu-id="6f6f4-136">Bottleneck phase</span></span>
2. <span data-ttu-id="6f6f4-137">Fase de treinamento</span><span class="sxs-lookup"><span data-stu-id="6f6f4-137">Training phase</span></span>

![Etapas de treinamento](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="6f6f4-139">Fase de afunilamento</span><span class="sxs-lookup"><span data-stu-id="6f6f4-139">Bottleneck phase</span></span>

<span data-ttu-id="6f6f4-140">Durante a fase de afunilamento, o conjunto de imagens de treinamento é carregado e os valores de pixel são usados como entrada, ou recursos, para as camadas congeladas do modelo pretreinado.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="6f6f4-141">As camadas congeladas incluem todas as camadas na rede neural até a camada penúltima, informalmente conhecida como a camada de afunilamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="6f6f4-142">Essas camadas são referidas como congeladas porque nenhum treinamento ocorrerá nessas camadas e as operações são passagem.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="6f6f4-143">Elas estão nessas camadas congeladas onde os padrões de nível inferior que ajudam um modelo diferenciar entre as diferentes classes são computadas.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="6f6f4-144">Quanto maior o número de camadas, mais intensivamente essa etapa é computada.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="6f6f4-145">Felizmente, como esse é um cálculo único, os resultados podem ser armazenados em cache e usados em execuções posteriores ao experimentar parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="6f6f4-146">Fase de treinamento</span><span class="sxs-lookup"><span data-stu-id="6f6f4-146">Training phase</span></span>

<span data-ttu-id="6f6f4-147">Depois que os valores de saída da fase de afunilamento são computados, eles são usados como entrada para treinar novamente a camada final do modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="6f6f4-148">Esse processo é iterativo e é executado para o número de vezes especificado por parâmetros de modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="6f6f4-149">Durante cada execução, a perda e a precisão são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="6f6f4-150">Em seguida, os ajustes apropriados são feitos para melhorar o modelo com o objetivo de minimizar a perda e maximizar a precisão.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="6f6f4-151">Quando o treinamento for concluído, dois formatos de modelo serão gerados.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="6f6f4-152">Uma delas é a `.pb` versão do modelo e a outra é a `.zip` versão serializada ml.net do modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="6f6f4-153">Ao trabalhar em ambientes com suporte do ML.NET, é recomendável usar a `.zip` versão do modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="6f6f4-154">No entanto, em ambientes em que não há suporte para ML.NET, você tem a opção de usar a `.pb` versão.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="6f6f4-155">Entender o modelo pretreinado</span><span class="sxs-lookup"><span data-stu-id="6f6f4-155">Understand the pretrained model</span></span>

<span data-ttu-id="6f6f4-156">O modelo pretreinado usado neste tutorial é a variante de camada 101 do modelo de rede residual (ResNet) v2.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="6f6f4-157">O modelo original é treinado para classificar imagens em milhares de categorias.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="6f6f4-158">O modelo usa como entrada uma imagem de tamanho 224 x 224 e gera as probabilidades de classe para cada uma das classes em que é treinado.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="6f6f4-159">Parte desse modelo é usada para treinar um novo modelo usando imagens personalizadas para fazer previsões entre duas classes.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="6f6f4-160">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="6f6f4-160">Create console application</span></span>

<span data-ttu-id="6f6f4-161">Agora que você tem uma compreensão geral do aprendizado de transferência e da API de classificação de imagem, é hora de criar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="6f6f4-162">Crie um **aplicativo de console do .NET Core em C#** chamado "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="6f6f4-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="6f6f4-163">Instale o pacote NuGet do **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="6f6f4-163">Install the **Microsoft.ML** NuGet Package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. <span data-ttu-id="6f6f4-164">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="6f6f4-165">Escolha "nuget.org" como a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="6f6f4-166">Selecione a guia **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="6f6f4-167">Marque a caixa de seleção **incluir pré-lançamento** .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="6f6f4-168">Procure **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="6f6f4-169">Selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="6f6f4-170">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="6f6f4-171">Repita essas etapas para os pacotes **Microsoft. ml. Vision**, **SciSharp. TensorFlow. Redist**e **Microsoft. ml. ImageAnalytics** NuGet.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-171">Repeat these steps for the **Microsoft.ML.Vision**, **SciSharp.TensorFlow.Redist**, and **Microsoft.ML.ImageAnalytics** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="6f6f4-172">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="6f6f4-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="6f6f4-173">Os conjuntos de valores para este tutorial são de Maguire, Marc; Dorafshan, Sattar; e Thomas, Robert J., "SDNET2018: um conjunto de imagem de quebra concreta para aplicativos de Machine Learning" (2018).</span><span class="sxs-lookup"><span data-stu-id="6f6f4-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="6f6f4-174">Procurar todos os conjuntos de valores.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-174">Browse all Datasets.</span></span> <span data-ttu-id="6f6f4-175">Papel 48.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-175">Paper 48.</span></span> <https://digitalcommons.usu.edu/all_datasets/48>

<span data-ttu-id="6f6f4-176">SDNET2018 é um conjunto de uma imagem que contém anotações para estruturas concretas rachadas e não rachadas (baralhos de ponte, paredes e Pavement).</span><span class="sxs-lookup"><span data-stu-id="6f6f4-176">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Amostras de baralho da ponte do conjunto de SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="6f6f4-178">Os dados são organizados em três subdiretórios:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-178">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="6f6f4-179">D contém imagens do deck de ponte</span><span class="sxs-lookup"><span data-stu-id="6f6f4-179">D contains bridge deck images</span></span>
- <span data-ttu-id="6f6f4-180">P contém imagens Pavement</span><span class="sxs-lookup"><span data-stu-id="6f6f4-180">P contains pavement images</span></span>
- <span data-ttu-id="6f6f4-181">W contém imagens de parede</span><span class="sxs-lookup"><span data-stu-id="6f6f4-181">W contains wall images</span></span>

<span data-ttu-id="6f6f4-182">Cada um desses subdiretórios contém dois subdiretórios prefixais adicionais:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-182">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="6f6f4-183">C é o prefixo usado para superfícies rachadas</span><span class="sxs-lookup"><span data-stu-id="6f6f4-183">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="6f6f4-184">U é o prefixo usado para superfícies não decifradas</span><span class="sxs-lookup"><span data-stu-id="6f6f4-184">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="6f6f4-185">Neste tutorial, somente imagens de baralho de ponte são usadas.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-185">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="6f6f4-186">Baixe o [conjunto](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) de e descompacte.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-186">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="6f6f4-187">Crie um diretório chamado "ativos" em seu projeto para salvar os arquivos do conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-187">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="6f6f4-188">Copie os subdiretórios *CD* e *UD* do diretório recentemente descompactado para o diretório de *ativos* .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-188">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="6f6f4-189">Criar classes de entrada e saída</span><span class="sxs-lookup"><span data-stu-id="6f6f4-189">Create input and output classes</span></span>

1. <span data-ttu-id="6f6f4-190">Abra o arquivo *Program.cs* e substitua as `using` instruções existentes na parte superior do arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-190">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L1-L7)]

1. <span data-ttu-id="6f6f4-191">Abaixo da `Program` classe em *Program.cs*, crie uma classe chamada `ImageData` .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-191">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="6f6f4-192">Essa classe é usada para representar os dados carregados inicialmente.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-192">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L138-L143)]

    <span data-ttu-id="6f6f4-193">`ImageData` contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-193">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="6f6f4-194">`ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-194">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="6f6f4-195">`Label` é a categoria à qual a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-195">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="6f6f4-196">Esse é o valor a prever.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-196">This is the value to predict.</span></span>

1. <span data-ttu-id="6f6f4-197">Criar classes para os dados de entrada e saída</span><span class="sxs-lookup"><span data-stu-id="6f6f4-197">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="6f6f4-198">Abaixo da `ImageData` classe, defina o esquema dos dados de entrada em uma nova classe chamada `ModelInput` .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-198">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L145-L154)]

        <span data-ttu-id="6f6f4-199">`ModelInput` contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-199">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="6f6f4-200">`Image` é a `byte[]` representação da imagem.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-200">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="6f6f4-201">O modelo espera que os dados de imagem sejam desse tipo para treinamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-201">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="6f6f4-202">`LabelAsKey` é a representação numérica do `Label` .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-202">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="6f6f4-203">`ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-203">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="6f6f4-204">`Label` é a categoria à qual a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-204">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="6f6f4-205">Esse é o valor a prever.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-205">This is the value to predict.</span></span>

        <span data-ttu-id="6f6f4-206">Somente `Image` e `LabelAsKey` são usados para treinar o modelo e fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-206">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="6f6f4-207">As `ImagePath` `Label` Propriedades e são mantidas por conveniência para acessar o nome e a categoria do arquivo de imagem original.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-207">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="6f6f4-208">Em seguida, abaixo da `ModelInput` classe, defina o esquema dos dados de saída em uma nova classe chamada `ModelOutput` .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-208">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L156-L163)]

        <span data-ttu-id="6f6f4-209">`ModelOutput` contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-209">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="6f6f4-210">`ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-210">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="6f6f4-211">`Label` é a categoria original à qual a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-211">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="6f6f4-212">Esse é o valor a prever.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-212">This is the value to predict.</span></span>
        - <span data-ttu-id="6f6f4-213">`PredictedLabel` é o valor previsto pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-213">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="6f6f4-214">Semelhante a `ModelInput` , somente o `PredictedLabel` é necessário para fazer previsões, pois ela contém a previsão feita pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-214">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="6f6f4-215">As `ImagePath` `Label` Propriedades e são retidas para facilitar o acesso ao nome e à categoria do arquivo de imagem original.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-215">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="6f6f4-216">Criar diretório de espaço de trabalho</span><span class="sxs-lookup"><span data-stu-id="6f6f4-216">Create workspace directory</span></span>

<span data-ttu-id="6f6f4-217">Quando os dados de treinamento e validação não são alterados com frequência, é uma boa prática armazenar em cache os valores de afunilamento computados para execuções posteriores.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-217">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="6f6f4-218">Em seu projeto, crie um novo diretório chamado *espaço de trabalho* para armazenar os valores de afunilamento computados e `.pb` a versão do modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-218">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="6f6f4-219">Definir caminhos e inicializar variáveis</span><span class="sxs-lookup"><span data-stu-id="6f6f4-219">Define paths and initialize variables</span></span>

1. <span data-ttu-id="6f6f4-220">Dentro do `Main` método, defina o local de seus ativos, os valores de afunilamento computados e `.pb` a versão do modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-220">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L15-L17)]

1. <span data-ttu-id="6f6f4-221">Inicialize a `mlContext` variável com uma nova instância de [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="6f6f4-221">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L19)]

    <span data-ttu-id="6f6f4-222">A classe [MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações de ml.net, e a inicialização de MLContext cria um novo ambiente ml.NET que pode ser compartilhado entre os objetos de fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-222">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="6f6f4-223">Ele é semelhante, conceitualmente, a `DbContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-223">It's similar, conceptually, to `DbContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="6f6f4-224">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="6f6f4-224">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="6f6f4-225">Criar método de utilitário de carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="6f6f4-225">Create data loading utility method</span></span>

<span data-ttu-id="6f6f4-226">As imagens são armazenadas em dois subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-226">The images are stored in two subdirectories.</span></span> <span data-ttu-id="6f6f4-227">Antes de carregar os dados, eles precisam ser formatados em uma lista de `ImageData` objetos.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-227">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="6f6f4-228">Para fazer isso, crie o `LoadImagesFromDirectory` método abaixo do `Main` método.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-228">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="6f6f4-229">Dentro do `LoadImagesFromDirectory` , adicione o seguinte código para obter todos os caminhos de arquivo dos subdiretórios:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-229">Inside the `LoadImagesFromDirectory`, add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L105-L106)]

1. <span data-ttu-id="6f6f4-230">Em seguida, Itere em cada um dos arquivos usando uma `foreach` instrução.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-230">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="6f6f4-231">Dentro da `foreach` instrução, verifique se as extensões de arquivo têm suporte.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-231">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="6f6f4-232">A API de classificação de imagem dá suporte aos formatos JPEG e PNG.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-232">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L110-L111)]

1. <span data-ttu-id="6f6f4-233">Em seguida, obtenha o rótulo para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-233">Then, get the label for the file.</span></span> <span data-ttu-id="6f6f4-234">Se o `useFolderNameAsLabel` parâmetro for definido como `true` , o diretório pai onde o arquivo é salvo será usado como o rótulo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-234">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="6f6f4-235">Caso contrário, ele espera que o rótulo seja um prefixo do nome do arquivo ou o próprio nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-235">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L113-L127)]

1. <span data-ttu-id="6f6f4-236">Por fim, crie uma nova instância do `ModelInput` .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-236">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L129-L133)]

### <a name="prepare-the-data"></a><span data-ttu-id="6f6f4-237">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="6f6f4-237">Prepare the data</span></span>

1. <span data-ttu-id="6f6f4-238">De volta ao `Main` método, use o `LoadImagesFromDirectory` método utilitário para obter a lista de imagens usadas para treinamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-238">Back in the `Main` method, use the `LoadImagesFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L22)]

1. <span data-ttu-id="6f6f4-239">Em seguida, carregue as imagens em um [`IDataView`](xref:Microsoft.ML.IDataView) usando o [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) método.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-239">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L24)]

1. <span data-ttu-id="6f6f4-240">Os dados são carregados na ordem em que foram lidos dos diretórios.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-240">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="6f6f4-241">Para balancear os dados, use a ordem aleatória usando o [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) método.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-241">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L26)]

1. <span data-ttu-id="6f6f4-242">Os modelos de aprendizado de máquina esperam que a entrada esteja em formato numérico.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-242">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="6f6f4-243">Portanto, algum pré-processamento precisa ser feito nos dados antes do treinamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-243">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="6f6f4-244">Crie um [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) composto das [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` transformações e.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-244">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="6f6f4-245">A `MapValueToKey` transformação usa o valor categórico na `Label` coluna, converte-o em um valor numérico `KeyType` e o armazena em uma nova coluna chamada `LabelAsKey` .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-245">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="6f6f4-246">O `LoadImages` pega os valores da `ImagePath` coluna junto com o `imageFolder` parâmetro para carregar imagens para treinamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-246">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L28-L34)]

1. <span data-ttu-id="6f6f4-247">Use o [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) método para aplicar os dados ao `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) seguido pelo [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) método, que retorna um [`IDataView`](xref:Microsoft.ML.IDataView) que contém os dados pré-processados.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L36-L38)]

1. <span data-ttu-id="6f6f4-248">Para treinar um modelo, é importante ter um conjunto de um de treinamento, bem como um conjunto de uma validação.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="6f6f4-249">O modelo é treinado no conjunto de treinamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-249">The model is trained on the training set.</span></span> <span data-ttu-id="6f6f4-250">O quão bem ele faz previsões sobre dados não vistos é medido pelo desempenho em relação ao conjunto de validação.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="6f6f4-251">Com base nos resultados desse desempenho, o modelo faz ajustes no que ele aprendeu em um esforço para melhorar.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="6f6f4-252">O conjunto de validação pode vir de uma divisão do conjunto de seus conjuntos de seus originais ou de outra fonte que já tenha sido reservada para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="6f6f4-253">Nesse caso, o conjunto de valores previamente processados é dividido em conjuntos de treinamento, validação e teste.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L40-L41)]

    <span data-ttu-id="6f6f4-254">O exemplo de código acima executa duas divisões.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-254">The code sample above performs two splits.</span></span> <span data-ttu-id="6f6f4-255">Primeiro, os dados previamente processados são divididos e 70% é usado para treinamento enquanto os 30% restantes são usados para validação.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="6f6f4-256">Em seguida, o conjunto de validação de 30% é mais dividido em conjuntos de validação e de teste em que 90% é usado para validação e 10% é usado para teste.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="6f6f4-257">Uma maneira de pensar sobre a finalidade dessas partições de dados é fazer um exame.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="6f6f4-258">Ao estudar um exame, você examina suas notas, livros ou outros recursos para entender os conceitos que estão no exame.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="6f6f4-259">É para isso que se trata o conjunto de treinamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-259">This is what the train set is for.</span></span> <span data-ttu-id="6f6f4-260">Em seguida, você pode fazer um exame fictício para validar seu conhecimento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="6f6f4-261">É aí que o conjunto de validação é útil.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="6f6f4-262">Você quer verificar se tem uma boa noção dos conceitos antes de pegar o exame real.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="6f6f4-263">Com base nesses resultados, anote o que você obteve errado ou não entendeu bem e incorpore suas alterações ao examinar o exame real.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="6f6f4-264">Por fim, você assume o exame.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-264">Finally, you take the exam.</span></span> <span data-ttu-id="6f6f4-265">É para isso que o conjunto de testes é usado.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-265">This is what the test set is used for.</span></span> <span data-ttu-id="6f6f4-266">Você nunca viu as perguntas que estão no exame e agora usa o que aprendeu do treinamento e da validação para aplicar seu conhecimento à tarefa em questão.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="6f6f4-267">Atribua as partições seus respectivos valores para os dados de treinamento, validação e teste.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L43-L45)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="6f6f4-268">Definir o pipeline de treinamento</span><span class="sxs-lookup"><span data-stu-id="6f6f4-268">Define the training pipeline</span></span>

<span data-ttu-id="6f6f4-269">O treinamento de modelo consiste em algumas etapas.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="6f6f4-270">Primeiro, a API de classificação de imagem é usada para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="6f6f4-271">Em seguida, os rótulos codificados na `PredictedLabel` coluna são convertidos de volta para seu valor categórico original usando a `MapKeyToValue` transformação.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="6f6f4-272">Crie uma nova variável para armazenar um conjunto de parâmetros obrigatórios e opcionais para um `ImageClassificationTrainer` .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-272">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L47-L58)]

    <span data-ttu-id="6f6f4-273">Um `ImageClassificationTrainer` aceita vários parâmetros opcionais:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-273">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="6f6f4-274">`FeatureColumnName` é a coluna usada como entrada para o modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-274">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="6f6f4-275">`LabelColumnName` é a coluna para o valor a prever.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-275">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="6f6f4-276">`ValidationSet` é o [`IDataView`](xref:Microsoft.ML.IDataView) que contém os dados de validação.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-276">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="6f6f4-277">`Arch` define qual das arquiteturas de modelo pretreinados usar.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-277">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="6f6f4-278">Este tutorial usa a variante de camada 101 do modelo ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-278">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="6f6f4-279">`MetricsCallback` associa uma função para acompanhar o progresso durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-279">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="6f6f4-280">`TestOnTrainSet` informa o modelo para medir o desempenho em relação ao conjunto de treinamento quando nenhum conjunto de validação estiver presente.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-280">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="6f6f4-281">`ReuseTrainSetBottleneckCachedValues` informa ao modelo se os valores armazenados em cache devem ser usados da fase de afunilamento nas execuções subsequentes.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-281">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="6f6f4-282">A fase de afunilamento é uma computação de passagem única que é computacionalmente intensiva na primeira vez em que é executada.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-282">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="6f6f4-283">Se os dados de treinamento não forem alterados e você quiser experimentar o uso de um número diferente de épocas ou do tamanho do lote, usar os valores armazenados em cache reduz significativamente o tempo necessário para treinar um modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-283">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="6f6f4-284">`ReuseValidationSetBottleneckCachedValues` é semelhante `ReuseTrainSetBottleneckCachedValues` apenas ao que, nesse caso, é para o conjunto de conjuntos de validação.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-284">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="6f6f4-285">`WorkspacePath` define o diretório onde armazenar os valores de afunilamento computados e `.pb` a versão do modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-285">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="6f6f4-286">Defina o [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline de treinamento que consiste no `mapLabelEstimator` e no `ImageClassificationTrainer` .</span><span class="sxs-lookup"><span data-stu-id="6f6f4-286">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L60-L61)]

1. <span data-ttu-id="6f6f4-287">Use o [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) método para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-287">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L63)]

## <a name="use-the-model"></a><span data-ttu-id="6f6f4-288">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="6f6f4-288">Use the model</span></span>

<span data-ttu-id="6f6f4-289">Agora que você treinou seu modelo, é hora de usá-lo para classificar imagens.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-289">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="6f6f4-290">Abaixo do `Main` método, crie um novo método de utilitário chamado `OutputPrediction` para exibir informações de previsão no console do.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-290">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L97-L101)]

### <a name="classify-a-single-image"></a><span data-ttu-id="6f6f4-291">Classificar uma única imagem</span><span class="sxs-lookup"><span data-stu-id="6f6f4-291">Classify a single image</span></span>

1. <span data-ttu-id="6f6f4-292">Adicione um novo método chamado `ClassifySingleImage` abaixo do `Main` método para fazer e gerar uma previsão de imagem única.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-292">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="6f6f4-293">Crie um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dentro do `ClassifySingleImage` método.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-293">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="6f6f4-294">O [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você passe e execute uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-294">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L74)]

1. <span data-ttu-id="6f6f4-295">Para acessar uma única `ModelInput` instância, converta-a `data` [`IDataView`](xref:Microsoft.ML.IDataView) em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) usando o [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) método e obtenha a primeira observação.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-295">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L76)]

1. <span data-ttu-id="6f6f4-296">Use o [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) método para classificar a imagem.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-296">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L78)]

1. <span data-ttu-id="6f6f4-297">Gere a previsão para o console com o `OutputPrediction` método.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-297">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L80-L81)]

1. <span data-ttu-id="6f6f4-298">Dentro do `Main` método, chame `ClassifySingleImage` usando o conjunto de teste de imagens.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-298">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L65)]

### <a name="classify-multiple-images"></a><span data-ttu-id="6f6f4-299">Classificar várias imagens</span><span class="sxs-lookup"><span data-stu-id="6f6f4-299">Classify multiple images</span></span>

1. <span data-ttu-id="6f6f4-300">Adicione um novo método chamado `ClassifyImages` abaixo do `ClassifySingleImage` método para fazer e gerar várias previsões de imagem.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-300">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="6f6f4-301">Crie um [`IDataView`](xref:Microsoft.ML.IDataView) contendo as previsões usando o [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) método.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-301">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="6f6f4-302">Adicione o seguinte código dentro do método `ClassifyImages`.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-302">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L86)]

1. <span data-ttu-id="6f6f4-303">Para iterar as previsões, converta-o `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) usando o [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) método e, em seguida, obtenha as 10 primeiras observações.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-303">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L88)]

1. <span data-ttu-id="6f6f4-304">Itere e gere os rótulos original e previsto para as previsões.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-304">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L90-L94)]

1. <span data-ttu-id="6f6f4-305">Por fim, dentro do `Main` método, chame `ClassifyImages` usando o conjunto de teste de imagens.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-305">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L67)]

## <a name="run-the-application"></a><span data-ttu-id="6f6f4-306">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="6f6f4-306">Run the application</span></span>

<span data-ttu-id="6f6f4-307">Execute o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-307">Run your console app.</span></span> <span data-ttu-id="6f6f4-308">A saída deve ser semelhante à mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-308">The output should be similar to that below.</span></span> <span data-ttu-id="6f6f4-309">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-309">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="6f6f4-310">Para resumir, a saída foi condensada.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-310">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="6f6f4-311">**Fase de afunilamento**</span><span class="sxs-lookup"><span data-stu-id="6f6f4-311">**Bottleneck phase**</span></span>

<span data-ttu-id="6f6f4-312">Nenhum valor é impresso para o nome da imagem porque as imagens são carregadas como um `byte[]` , portanto, não há nenhum nome de imagem a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-312">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="6f6f4-313">**Fase de treinamento**</span><span class="sxs-lookup"><span data-stu-id="6f6f4-313">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="6f6f4-314">**Classificar saída de imagens**</span><span class="sxs-lookup"><span data-stu-id="6f6f4-314">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="6f6f4-315">Após a inspeção da imagem de *7001-220.jpg* , você pode ver que, na verdade, ela não está quebrada.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-315">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Imagem do conjunto de SDNET2018 usado para previsão](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="6f6f4-317">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="6f6f4-317">Congratulations!</span></span> <span data-ttu-id="6f6f4-318">Agora você criou com êxito um modelo de aprendizado profundo para classificar imagens.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-318">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="6f6f4-319">Melhorar o modelo</span><span class="sxs-lookup"><span data-stu-id="6f6f4-319">Improve the model</span></span>

<span data-ttu-id="6f6f4-320">Se você não estiver satisfeito com os resultados do modelo, poderá tentar melhorar seu desempenho experimentando algumas das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="6f6f4-320">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="6f6f4-321">**Mais dados**: quanto mais exemplos um modelo aprende, melhor é o desempenho.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-321">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="6f6f4-322">Baixe o [conjunto de SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) completo e use-o para treinar.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-322">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="6f6f4-323">**Aumentar os dados**: uma técnica comum para adicionar uma variedade aos dados é aumentar os dados, tirando uma imagem e aplicando transformações diferentes (girar, virar, deslocar, cortar).</span><span class="sxs-lookup"><span data-stu-id="6f6f4-323">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="6f6f4-324">Isso adiciona exemplos mais variados para o modelo a ser aprendedo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-324">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="6f6f4-325">**Treine por mais tempo**: quanto mais longo for o treinamento, mais ajustado será o modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-325">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="6f6f4-326">Aumentar o número de épocas pode melhorar o desempenho do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-326">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="6f6f4-327">**Experimente os hiperparâmetros**: além dos parâmetros usados neste tutorial, outros parâmetros podem ser ajustados para melhorar potencialmente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-327">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="6f6f4-328">Alterar a taxa de aprendizado, que determina a magnitude das atualizações feitas ao modelo depois que cada época pode melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-328">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="6f6f4-329">**Use uma arquitetura de modelo diferente**: dependendo de como seus dados se parecem, o modelo que pode aprender melhor seus recursos pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-329">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="6f6f4-330">Se você não estiver satisfeito com o desempenho do seu modelo, tente alterar a arquitetura.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-330">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="6f6f4-331">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="6f6f4-331">Additional Resources</span></span>

- <span data-ttu-id="6f6f4-332">[Aprendizado profundo versus Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="6f6f4-332">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6f6f4-333">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6f6f4-333">Next steps</span></span>

<span data-ttu-id="6f6f4-334">Neste tutorial, você aprendeu a criar um modelo de aprendizado profundo personalizado usando o aprendizado de transferência, um modelo TensorFlow de classificação de imagem previamente treinado e a API de classificação de imagem ML.NET para classificar imagens de superfícies concretas como rachadas ou sem cracking.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-334">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="6f6f4-335">Avance para o próximo tutorial para saber mais.</span><span class="sxs-lookup"><span data-stu-id="6f6f4-335">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6f6f4-336">Detecção de objetos</span><span class="sxs-lookup"><span data-stu-id="6f6f4-336">Object Detection</span></span>](object-detection-onnx.md)
