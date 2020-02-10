---
title: 'Tutorial: modelo de classificação de imagem ML.NET de TensorFlow'
description: Saiba como transferir o conhecimento de um modelo TensorFlow existente para um novo modelo de classificação de imagem ML.NET. O modelo TensorFlow foi treinado para classificar imagens em milhares de categorias. O modelo ML.NET usa o aprendizado de transferência para classificar imagens em menos categorias mais amplas.
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: f5ec31f8bfdc089d275588b228c8ce6f28a44201
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092545"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="84934-105">Tutorial: gerar um modelo de classificação de imagem ML.NET de um modelo de TensorFlow pré-treinado</span><span class="sxs-lookup"><span data-stu-id="84934-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="84934-106">Saiba como transferir o conhecimento de um modelo TensorFlow existente para um novo modelo de classificação de imagem ML.NET.</span><span class="sxs-lookup"><span data-stu-id="84934-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="84934-107">O modelo TensorFlow foi treinado para classificar imagens em milhares de categorias.</span><span class="sxs-lookup"><span data-stu-id="84934-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="84934-108">O modelo ML.NET faz uso de parte do modelo TensorFlow em seu pipeline para treinar um modelo para classificar imagens em três categorias.</span><span class="sxs-lookup"><span data-stu-id="84934-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="84934-109">Treinar um modelo de [Classificação de Imagens](https://en.wikipedia.org/wiki/Outline_of_object_recognition) do zero requer a configuração de milhões de parâmetros, uma tonelada de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU).</span><span class="sxs-lookup"><span data-stu-id="84934-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="84934-110">Embora não seja tão eficaz quanto treinar um modelo personalizado do zero, o aprendizado de transferência permite que você ative esse processo trabalhando com milhares de imagens em comparação com milhões de imagens rotuladas e crie um modelo personalizado rapidamente (em uma hora em uma máquina sem GPU).</span><span class="sxs-lookup"><span data-stu-id="84934-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="84934-111">Este tutorial dimensiona o processo ainda mais para cima, usando apenas uma dúzia de imagens de treinamento.</span><span class="sxs-lookup"><span data-stu-id="84934-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="84934-112">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="84934-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="84934-113">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="84934-113">Understand the problem</span></span>
> * <span data-ttu-id="84934-114">Incorporar o modelo de TensorFlow pré-treinado ao pipeline do ML.NET</span><span class="sxs-lookup"><span data-stu-id="84934-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="84934-115">Treinar e avaliar o modelo ML.NET</span><span class="sxs-lookup"><span data-stu-id="84934-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="84934-116">Classificar uma imagem de teste</span><span class="sxs-lookup"><span data-stu-id="84934-116">Classify a test image</span></span>

<span data-ttu-id="84934-117">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="84934-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="84934-118">Observe que, por padrão, a configuração de projeto do .NET para este tutorial se destina ao .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="84934-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="84934-119">O que é o aprendizado por transferência?</span><span class="sxs-lookup"><span data-stu-id="84934-119">What is transfer learning?</span></span>

<span data-ttu-id="84934-120">O aprendizado de transferência é o processo de uso do conhecimento obtido ao resolver um problema e aplicá-lo a um problema diferente, mas relacionado.</span><span class="sxs-lookup"><span data-stu-id="84934-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="84934-121">Para este tutorial, você usa parte de um modelo TensorFlow treinado para classificar imagens em mil categorias – em um modelo ML.NET que classifica imagens em três categorias.</span><span class="sxs-lookup"><span data-stu-id="84934-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84934-122">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="84934-122">Prerequisites</span></span>

* <span data-ttu-id="84934-123">[Visual Studio 2017 versão 15,6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="84934-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="84934-124">O arquivo .ZIP do diretório de recursos do tutorial</span><span class="sxs-lookup"><span data-stu-id="84934-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="84934-125">O modelo de machine learning do InceptionV1</span><span class="sxs-lookup"><span data-stu-id="84934-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="84934-126">Selecione a tarefa de aprendizado de máquina correta</span><span class="sxs-lookup"><span data-stu-id="84934-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="84934-127">Aprendizado</span><span class="sxs-lookup"><span data-stu-id="84934-127">Deep learning</span></span>

<span data-ttu-id="84934-128">[Aprendizado profundo](https://en.wikipedia.org/wiki/Deep_learning) é um subconjunto do aprendizado de máquina, que está revolucionando áreas como Pesquisa Visual Computacional e Reconhecimento de Fala.</span><span class="sxs-lookup"><span data-stu-id="84934-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="84934-129">Os modelos de aprendizado profundo são treinados usando grandes conjuntos de [dados rotulados](https://en.wikipedia.org/wiki/Labeled_data) e [redes neurais](https://en.wikipedia.org/wiki/Artificial_neural_network) que contêm várias camadas de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="84934-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="84934-130">Aprendizado profundo:</span><span class="sxs-lookup"><span data-stu-id="84934-130">Deep learning:</span></span>

* <span data-ttu-id="84934-131">Funciona melhor em algumas tarefas como a Pesquisa Visual Computacional.</span><span class="sxs-lookup"><span data-stu-id="84934-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="84934-132">Requer enormes quantidades de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="84934-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="84934-133">A classificação de imagem é uma tarefa Machine Learning comum que nos permite classificar automaticamente as imagens em categorias como:</span><span class="sxs-lookup"><span data-stu-id="84934-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="84934-134">Detectar uma face humana em uma imagem ou não.</span><span class="sxs-lookup"><span data-stu-id="84934-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="84934-135">Detectando gatos vs. cachorros.</span><span class="sxs-lookup"><span data-stu-id="84934-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="84934-136">Ou como nas imagens a seguir, determinando se uma imagem é um (n) comida, Toy ou dispositivo:</span><span class="sxs-lookup"><span data-stu-id="84934-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="84934-137">![imagem de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![imagem de ursinho de pelúcia](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![imagem de torradeira](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="84934-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="84934-138">As imagens anteriores pertencem ao Wikimedia Commons e são atribuídas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="84934-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="84934-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="84934-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="84934-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="84934-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="84934-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="84934-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="84934-142">O `Inception model` é treinado para classificar imagens em uma categoria de milhares, mas, para este tutorial, você precisa classificar imagens em um conjunto de categorias menor e apenas essas categorias.</span><span class="sxs-lookup"><span data-stu-id="84934-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="84934-143">Digite a parte `transfer` de `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="84934-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="84934-144">Você pode transferir a capacidade de `Inception model` de reconhecer e classificar imagens para as novas categorias limitadas do seu classificador de imagens personalizadas.</span><span class="sxs-lookup"><span data-stu-id="84934-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="84934-145">Alimentos</span><span class="sxs-lookup"><span data-stu-id="84934-145">Food</span></span>
* <span data-ttu-id="84934-146">Brinquedos</span><span class="sxs-lookup"><span data-stu-id="84934-146">Toy</span></span>
* <span data-ttu-id="84934-147">Dispositivos</span><span class="sxs-lookup"><span data-stu-id="84934-147">Appliance</span></span>

<span data-ttu-id="84934-148">Este tutorial usa o modelo de aprendizado profundo de [modelo](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) de TensorFlow, um modelo de reconhecimento de imagem popular treinado no conjunto de `ImageNet` DataSet.</span><span class="sxs-lookup"><span data-stu-id="84934-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="84934-149">O modelo TensorFlow classifica imagens inteiras em milhares de classes, como "abrangência", "Jersey" e "dishwasher".</span><span class="sxs-lookup"><span data-stu-id="84934-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="84934-150">Como o `Inception model` já foi pré-treinado em milhares de imagens diferentes, internamente ele contém os [recursos de imagem](https://en.wikipedia.org/wiki/Feature_(computer_vision)) necessários para a identificação da imagem.</span><span class="sxs-lookup"><span data-stu-id="84934-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="84934-151">Podemos fazer uso desses recursos de imagem interna no modelo para treinar um novo modelo com muito menos classes.</span><span class="sxs-lookup"><span data-stu-id="84934-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="84934-152">Conforme mostrado no diagrama a seguir, você adiciona uma referência aos pacotes ML.NET NuGet em seus aplicativos .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84934-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="84934-153">Nos bastidores, ML.NET inclui e faz referência à biblioteca nativa de `TensorFlow` que permite que você escreva código que carregue um arquivo de modelo treinado `TensorFlow` existente.</span><span class="sxs-lookup"><span data-stu-id="84934-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Diagrama de arco da transformação do TensorFlow do ML.NET](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="84934-155">Classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="84934-155">Multiclass classification</span></span>

<span data-ttu-id="84934-156">Depois de usar o modelo de criação de TensorFlow para extrair recursos adequados como entrada para um algoritmo de aprendizado de máquina clássico, adicionamos um [classificador de várias classes](../resources/tasks.md#multiclass-classification)ml.net.</span><span class="sxs-lookup"><span data-stu-id="84934-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="84934-157">O treinador específico usado nesse caso é o [algoritmo de regressão logística multinomial](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="84934-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="84934-158">O algoritmo implementado por esse instrutor tem um bom desempenho em problemas com um grande número de recursos, que é o caso de um modelo de aprendizado profundo operando em dados de imagem.</span><span class="sxs-lookup"><span data-stu-id="84934-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="84934-159">data</span><span class="sxs-lookup"><span data-stu-id="84934-159">Data</span></span>

<span data-ttu-id="84934-160">Há duas fontes de dados: o arquivo `.tsv` e os arquivos de imagem.</span><span class="sxs-lookup"><span data-stu-id="84934-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="84934-161">O arquivo `tags.tsv` contém duas colunas: a primeira é definida como `ImagePath` e a segunda é a `Label` correspondente à imagem.</span><span class="sxs-lookup"><span data-stu-id="84934-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="84934-162">O arquivo de exemplo a seguir não possui uma linha de cabeçalho e tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="84934-162">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="84934-163">As imagens de treinamento e teste estão localizadas nas pastas de recursos que você baixará em um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="84934-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="84934-164">Essas imagens pertencem ao Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="84934-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="84934-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), o repositório de mídia gratuito.*</span><span class="sxs-lookup"><span data-stu-id="84934-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="84934-166">Recuperado 10:48, 17 de outubro de 2018 de: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="84934-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="84934-167">Instalação</span><span class="sxs-lookup"><span data-stu-id="84934-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="84934-168">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="84934-168">Create a project</span></span>

1. <span data-ttu-id="84934-169">Criar um **Aplicativo de Console .NET Core** chamado "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="84934-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="84934-170">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="84934-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="84934-171">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="84934-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="84934-172">Escolha "nuget.org" como a fonte do pacote, selecione a guia Browse, procure por **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="84934-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="84934-173">Clique no menu suspenso **versão** , selecione o pacote **1.4.0** na lista e selecione o botão **instalar** .</span><span class="sxs-lookup"><span data-stu-id="84934-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="84934-174">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** .</span><span class="sxs-lookup"><span data-stu-id="84934-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="84934-175">Selecione o botão **aceito** na caixa de diálogo de **aceitação da licença** se você concordar com os termos de licença dos pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="84934-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="84934-176">Repita essas etapas para **Microsoft. ml. ImageAnalytics v 1.4.0**, **SciSharp. TensorFlow. Redist v 1.15.0** e **Microsoft. ml. TensorFlow v 1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="84934-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="84934-177">Baixar ativos</span><span class="sxs-lookup"><span data-stu-id="84934-177">Download assets</span></span>

1. <span data-ttu-id="84934-178">Baixe o [arquivo zip do diretório de materiais do projeto](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip) e descompacte.</span><span class="sxs-lookup"><span data-stu-id="84934-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="84934-179">Copie o diretório`assets` no diretório do projeto *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="84934-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="84934-180">Este diretório e seus subdiretórios contêm os arquivos de dados e de suporte (exceto o modelo Concepção, que você irá baixar e adicionar na próxima etapa) necessários para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="84934-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="84934-181">Baixe o [modelo Concepção](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) e descompacte-o.</span><span class="sxs-lookup"><span data-stu-id="84934-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="84934-182">Copie o conteúdo do diretório `inception5h` apenas descompactado em seu diretório de projeto *TransferLearningTF*`assets/inception`.</span><span class="sxs-lookup"><span data-stu-id="84934-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="84934-183">Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="84934-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Conteúdo do diretório de concepção](./media/image-classification/inception-files.png)

1. <span data-ttu-id="84934-185">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos no diretório e nos subdiretórios do ativo e selecione**Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="84934-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="84934-186">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="84934-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="84934-187">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="84934-187">Create classes and define paths</span></span>

1. <span data-ttu-id="84934-188">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="84934-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="84934-189">Adicione o seguinte código à linha à direita acima do método `Main` para especificar os caminhos de ativo:</span><span class="sxs-lookup"><span data-stu-id="84934-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="84934-190">Crie classes para os dados de entrada e previsões.</span><span class="sxs-lookup"><span data-stu-id="84934-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="84934-191">`ImageData` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="84934-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="84934-192">`ImagePath` contém o nome do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="84934-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="84934-193">`Label` contém um valor para o rótulo da imagem.</span><span class="sxs-lookup"><span data-stu-id="84934-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="84934-194">Adicione uma nova classe ao seu projeto para `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="84934-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="84934-195">`ImagePrediction` é a classe de previsão de imagem e possui os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="84934-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="84934-196">`Score` contém a porcentagem de confiança para uma determinada classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="84934-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="84934-197">`PredictedLabelValue` contém um valor para o rótulo de classificação de imagem previsto.</span><span class="sxs-lookup"><span data-stu-id="84934-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="84934-198">`ImagePrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="84934-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="84934-199">Tem um `string` (`ImagePath`) para o demarcador da imagem.</span><span class="sxs-lookup"><span data-stu-id="84934-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="84934-200">O `Label` é usado para reutilizar e treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="84934-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="84934-201">O `PredictedLabelValue` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="84934-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="84934-202">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="84934-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="84934-203">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="84934-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="84934-204">Inicialize a variável `mlContext` com uma nova instância de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="84934-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="84934-205">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="84934-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="84934-206">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="84934-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="84934-207">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="84934-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="84934-208">Criar uma estrutura para parâmetros de modelo de criação</span><span class="sxs-lookup"><span data-stu-id="84934-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="84934-209">O modelo de início tem vários parâmetros que você precisa passar.</span><span class="sxs-lookup"><span data-stu-id="84934-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="84934-210">Crie um struct para mapear os valores de parâmetro para nomes amigáveis com o seguinte código, logo após o método de `Main()`:</span><span class="sxs-lookup"><span data-stu-id="84934-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="84934-211">Criar um método de utilitário de exibição</span><span class="sxs-lookup"><span data-stu-id="84934-211">Create a display utility method</span></span>

<span data-ttu-id="84934-212">Uma vez que você exibirá os dados de imagem e as previsões relacionadas mais de uma vez, crie um método de utilitário de exibição para lidar com a exibição dos resultados de imagem e previsão.</span><span class="sxs-lookup"><span data-stu-id="84934-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="84934-213">Crie o método `DisplayResults()`, logo após o struct `InceptionSettings`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="84934-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="84934-214">Preencha o corpo do método de `DisplayResults`:</span><span class="sxs-lookup"><span data-stu-id="84934-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="84934-215">Criar um método de utilitário de arquivo .tsv</span><span class="sxs-lookup"><span data-stu-id="84934-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="84934-216">Crie o método `ReadFromTsv()`, logo após o método `DisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="84934-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="84934-217">Preencha o corpo do método de `ReadFromTsv`:</span><span class="sxs-lookup"><span data-stu-id="84934-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="84934-218">O código analisa por meio do arquivo `tags.tsv` para adicionar o caminho do arquivo ao nome do arquivo de imagem para a propriedade `ImagePath` e carregá-lo e o `Label` em um objeto `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="84934-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="84934-219">Criar um método para fazer uma previsão</span><span class="sxs-lookup"><span data-stu-id="84934-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="84934-220">Crie o método `ClassifySingleImage()`, logo antes do método `DisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="84934-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="84934-221">Crie um objeto `ImageData` que contenha o caminho totalmente qualificado e o nome do arquivo de imagem para o `ImagePath`único.</span><span class="sxs-lookup"><span data-stu-id="84934-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="84934-222">Adicione o seguinte código como as próximas linhas no método `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="84934-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="84934-223">Faça uma única previsão adicionando o seguinte código como a próxima linha no método de `ClassifySingleImage`:</span><span class="sxs-lookup"><span data-stu-id="84934-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="84934-224">Para obter a previsão, use o método [Predict ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) .</span><span class="sxs-lookup"><span data-stu-id="84934-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="84934-225">O [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você execute uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="84934-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="84934-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="84934-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="84934-227">É aceitável usar em ambientes de protótipo ou de thread único.</span><span class="sxs-lookup"><span data-stu-id="84934-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="84934-228">Para melhorar o desempenho e a segurança de thread em ambientes de produção, use o serviço `PredictionEnginePool`, que cria uma [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de objetos [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para uso em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84934-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="84934-229">Consulte este guia sobre como [usar `PredictionEnginePool` em uma API Web do ASP.NET Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="84934-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="84934-230">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="84934-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="84934-231">Exiba o resultado da previsão como a próxima linha de código no método `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="84934-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="84934-232">Construir o pipeline de modelo ML.NET</span><span class="sxs-lookup"><span data-stu-id="84934-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="84934-233">Um pipeline de modelo ML.NET é uma cadeia de estimadores.</span><span class="sxs-lookup"><span data-stu-id="84934-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="84934-234">Observe que nenhuma execução ocorre durante a construção do pipeline.</span><span class="sxs-lookup"><span data-stu-id="84934-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="84934-235">Os objetos do estimador são criados, mas não são executados.</span><span class="sxs-lookup"><span data-stu-id="84934-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="84934-236">Adicionar um método para gerar o modelo</span><span class="sxs-lookup"><span data-stu-id="84934-236">Add a method to generate the model</span></span>

    <span data-ttu-id="84934-237">Esse método é o coração do tutorial.</span><span class="sxs-lookup"><span data-stu-id="84934-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="84934-238">Ele cria um pipeline para o modelo e treina o pipeline para produzir o modelo ML.NET.</span><span class="sxs-lookup"><span data-stu-id="84934-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="84934-239">Ele também avalia o modelo em relação a alguns dados de teste não vistos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="84934-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="84934-240">Crie o método `GenerateModel()` logo após o struct `InceptionSettings` e antes do método `DisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="84934-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="84934-241">Adicione os estimadores para carregar, redimensionar e extrair os pixels dos dados da imagem:</span><span class="sxs-lookup"><span data-stu-id="84934-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="84934-242">Os dados da imagem precisam ser processados no formato esperado pelo modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="84934-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="84934-243">Nesse caso, as imagens são carregadas na memória, redimensionadas para um tamanho consistente e os pixels são extraídos em um vetor numérico.</span><span class="sxs-lookup"><span data-stu-id="84934-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="84934-244">Adicione o estimador para carregar o modelo TensorFlow e pontua-lo:</span><span class="sxs-lookup"><span data-stu-id="84934-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="84934-245">Esse estágio no pipeline carrega o modelo TensorFlow na memória e, em seguida, processa o vetor de valores de pixel por meio da rede do modelo TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="84934-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="84934-246">Aplicar entradas a um modelo de aprendizado profundo e gerar uma saída usando o modelo é conhecido como **Pontuação**.</span><span class="sxs-lookup"><span data-stu-id="84934-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="84934-247">Ao usar o modelo em sua totalidade, a pontuação faz uma inferência ou previsão.</span><span class="sxs-lookup"><span data-stu-id="84934-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="84934-248">Nesse caso, você usa todo o modelo TensorFlow, exceto a última camada, que é a camada que faz a inferência.</span><span class="sxs-lookup"><span data-stu-id="84934-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="84934-249">A saída da camada penúltima é rotulada `softmax_2_preactivation`.</span><span class="sxs-lookup"><span data-stu-id="84934-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="84934-250">A saída dessa camada é efetivamente um vetor de recursos que caracteriza as imagens de entrada originais.</span><span class="sxs-lookup"><span data-stu-id="84934-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="84934-251">Esse vetor de recurso gerado pelo modelo TensorFlow será usado como entrada para um algoritmo de treinamento ML.NET.</span><span class="sxs-lookup"><span data-stu-id="84934-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="84934-252">Adicione o estimador para mapear os rótulos de cadeia de caracteres nos dados de treinamento para valores de chave de inteiro:</span><span class="sxs-lookup"><span data-stu-id="84934-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="84934-253">O treinador ML.NET que é acrescentado em seguida requer que seus rótulos estejam no formato `key` em vez de cadeias de caracteres arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="84934-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="84934-254">Uma chave é um número que tem um mapeamento de um para um para um valor de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="84934-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="84934-255">Adicione o algoritmo de treinamento ML.NET:</span><span class="sxs-lookup"><span data-stu-id="84934-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="84934-256">Adicione o estimador para mapear o valor de chave previsto de volta para uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="84934-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="84934-257">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="84934-257">Train the model</span></span>

1. <span data-ttu-id="84934-258">Carregue os dados de treinamento usando o wrapper [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) .</span><span class="sxs-lookup"><span data-stu-id="84934-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="84934-259">Adicione o seguinte código ao método `GenerateModel()` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="84934-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="84934-260">Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="84934-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="84934-261">`IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto).</span><span class="sxs-lookup"><span data-stu-id="84934-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="84934-262">Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="84934-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="84934-263">Treine o modelo com os dados carregados acima:</span><span class="sxs-lookup"><span data-stu-id="84934-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="84934-264">O método `Fit()` treina seu modelo aplicando o conjunto de os de treinamento ao pipeline.</span><span class="sxs-lookup"><span data-stu-id="84934-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="84934-265">Avaliar a precisão do modelo</span><span class="sxs-lookup"><span data-stu-id="84934-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="84934-266">Carregue e transforme os dados de teste, adicionando o seguinte código à próxima linha do método de `GenerateModel`:</span><span class="sxs-lookup"><span data-stu-id="84934-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="84934-267">Há algumas imagens de exemplo que você pode usar para avaliar o modelo.</span><span class="sxs-lookup"><span data-stu-id="84934-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="84934-268">Assim como os dados de treinamento, eles precisam ser carregados em um `IDataView`, para que possam ser transformados pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="84934-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="84934-269">Adicione o seguinte código ao método `GenerateModel()` para avaliar o modelo:</span><span class="sxs-lookup"><span data-stu-id="84934-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="84934-270">Depois de determinar a previsão, o método [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A):</span><span class="sxs-lookup"><span data-stu-id="84934-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="84934-271">Avalia o modelo (compara os valores previstos com o conjunto de `labels`de teste).</span><span class="sxs-lookup"><span data-stu-id="84934-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="84934-272">Retorna as métricas de desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="84934-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="84934-273">Exibir as métricas de precisão do modelo</span><span class="sxs-lookup"><span data-stu-id="84934-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="84934-274">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="84934-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="84934-275">As seguintes métricas são avaliadas para classificação de imagem:</span><span class="sxs-lookup"><span data-stu-id="84934-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="84934-276">`Log-loss` - confira [Perda de log](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="84934-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="84934-277">Convém que a Perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="84934-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="84934-278">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="84934-278">`Per class Log-loss`.</span></span> <span data-ttu-id="84934-279">Convém que a Perda de log por classe seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="84934-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="84934-280">Adicione o seguinte código para retornar o modelo treinado como a próxima linha:</span><span class="sxs-lookup"><span data-stu-id="84934-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="84934-281">Execute o aplicativo!</span><span class="sxs-lookup"><span data-stu-id="84934-281">Run the application!</span></span>

1. <span data-ttu-id="84934-282">Adicione a chamada para `GenerateModel` no método `Main` após a criação da classe MLContext:</span><span class="sxs-lookup"><span data-stu-id="84934-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="84934-283">Adicione a chamada ao método `ClassifySingleImage()` como a próxima linha de código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="84934-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="84934-284">Execute o aplicativo de console (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="84934-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="84934-285">O resultado deverá ser semelhante à seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="84934-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="84934-286">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="84934-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

<span data-ttu-id="84934-287">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="84934-287">Congratulations!</span></span> <span data-ttu-id="84934-288">Agora você criou com êxito um modelo de aprendizado de máquina para classificação de imagem aplicando o aprendizado de transferência a um modelo de `TensorFlow` no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="84934-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="84934-289">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="84934-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="84934-290">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="84934-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="84934-291">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="84934-291">Understand the problem</span></span>
> * <span data-ttu-id="84934-292">Incorporar o modelo de TensorFlow pré-treinado ao pipeline do ML.NET</span><span class="sxs-lookup"><span data-stu-id="84934-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="84934-293">Treinar e avaliar o modelo ML.NET</span><span class="sxs-lookup"><span data-stu-id="84934-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="84934-294">Classificar uma imagem de teste</span><span class="sxs-lookup"><span data-stu-id="84934-294">Classify a test image</span></span>

<span data-ttu-id="84934-295">Conferir o repositório GitHub de Amostras de Aprendizado de Máquina para explorar uma amostra de classificação de imagem expandida.</span><span class="sxs-lookup"><span data-stu-id="84934-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="84934-296">dotnet/machinelearning-samples GitHub repository</span><span class="sxs-lookup"><span data-stu-id="84934-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
