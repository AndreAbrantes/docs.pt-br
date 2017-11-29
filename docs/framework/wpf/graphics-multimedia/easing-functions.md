---
title: "Funções de easing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 198ec8b8cb0b27e009f01f8e60a47e8086a7dbc7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="easing-functions"></a><span data-ttu-id="6d170-102">Funções de easing</span><span class="sxs-lookup"><span data-stu-id="6d170-102">Easing Functions</span></span>
<span data-ttu-id="6d170-103">As funções easing permitem aplicar fórmulas matemáticas personalizadas às suas animações.</span><span class="sxs-lookup"><span data-stu-id="6d170-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="6d170-104">Por exemplo, talvez você queira que um objeto ricocheteie de modo realista ou comporte-se como se estivesse em uma mola.</span><span class="sxs-lookup"><span data-stu-id="6d170-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="6d170-105">Você pode usar o Quadro Chave ou até mesmo as animações De/Para/Por para aproximar esses efeitos, mas isso exigiria uma quantidade significativa de trabalho e a animação seria menos precisa do que usando uma fórmula matemática.</span><span class="sxs-lookup"><span data-stu-id="6d170-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="6d170-106">Além de criar sua própria função de atenuação personalizada herdando de <xref:System.Windows.Media.Animation.EasingFunctionBase>, você pode usar uma das várias funções de atenuação fornecidas pelo tempo de execução para criar efeitos comuns.</span><span class="sxs-lookup"><span data-stu-id="6d170-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="6d170-107"><xref:System.Windows.Media.Animation.BackEase>: Retira o movimento de uma animação um pouco antes de começar a animar no caminho indicado.</span><span class="sxs-lookup"><span data-stu-id="6d170-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="6d170-108"><xref:System.Windows.Media.Animation.BounceEase>: Cria um efeito saltitante.</span><span class="sxs-lookup"><span data-stu-id="6d170-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="6d170-109"><xref:System.Windows.Media.Animation.CircleEase>: Cria uma animação que acelera e/ou será desacelerado usando uma função circular.</span><span class="sxs-lookup"><span data-stu-id="6d170-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="6d170-110"><xref:System.Windows.Media.Animation.CubicEase>: Cria uma animação que acelera e/ou será desacelerado usando a fórmula *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="6d170-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="6d170-111"><xref:System.Windows.Media.Animation.ElasticEase>: Cria uma animação que se parece com um spring oscilatórios e para trás até que se trata de rest.</span><span class="sxs-lookup"><span data-stu-id="6d170-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="6d170-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Cria uma animação que acelera e/ou será desacelerado usando uma fórmula exponencial.</span><span class="sxs-lookup"><span data-stu-id="6d170-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="6d170-113"><xref:System.Windows.Media.Animation.PowerEase>: Cria uma animação que acelera e/ou será desacelerado usando a fórmula *f*(*t*) = *t*<sup>p</sup> onde p é igual a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6d170-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="6d170-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Cria uma animação que acelera e/ou será desacelerado usando a fórmula *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="6d170-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="6d170-115"><xref:System.Windows.Media.Animation.QuarticEase>: Cria uma animação que acelera e/ou será desacelerado usando a fórmula *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="6d170-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="6d170-116"><xref:System.Windows.Media.Animation.QuinticEase>: Criar uma animação que acelera e/ou será desacelerado usando a fórmula *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="6d170-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="6d170-117"><xref:System.Windows.Media.Animation.SineEase>: Cria uma animação que acelera e/ou será desacelerado usando uma fórmula de seno.</span><span class="sxs-lookup"><span data-stu-id="6d170-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="6d170-118">Você pode explorar o comportamento dessas funções de easing com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d170-118">You can explore the behavior of these easing functions with the following sample.</span></span>  
  
 [<span data-ttu-id="6d170-119">Executar esta amostra</span><span class="sxs-lookup"><span data-stu-id="6d170-119">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 <span data-ttu-id="6d170-120">Para aplicar uma função de easing uma animação, use o `EasingFunction` propriedade da animação especificar a função de easing para aplicar a animação.</span><span class="sxs-lookup"><span data-stu-id="6d170-120">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="6d170-121">O exemplo a seguir aplica-se um <xref:System.Windows.Media.Animation.BounceEase> facilitando a função para um <xref:System.Windows.Media.Animation.DoubleAnimation> para criar um efeito saltitante.</span><span class="sxs-lookup"><span data-stu-id="6d170-121">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [<span data-ttu-id="6d170-122">Executar esta amostra</span><span class="sxs-lookup"><span data-stu-id="6d170-122">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="6d170-123">No exemplo anterior, a função de easing foi aplicada a uma animação De/Para/Por.</span><span class="sxs-lookup"><span data-stu-id="6d170-123">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="6d170-124">Você também pode aplicar essas funções de easing a animações de Quadro-Chave.</span><span class="sxs-lookup"><span data-stu-id="6d170-124">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="6d170-125">O exemplo a seguir mostra como usar quadros-chave com as funções de easing associadas a eles para criar uma animação de um retângulo que se contrai para cima, desacelera e então expande-se para baixo (como se estivesse caindo) e então ricocheteia até parar.</span><span class="sxs-lookup"><span data-stu-id="6d170-125">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [<span data-ttu-id="6d170-126">Executar esta amostra</span><span class="sxs-lookup"><span data-stu-id="6d170-126">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="6d170-127">Você pode usar o <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> alteração de propriedade para alterar como a função de easing se comporta, ou seja, como a animação interpola.</span><span class="sxs-lookup"><span data-stu-id="6d170-127">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="6d170-128">Há três valores possíveis, você pode fornecer para <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="6d170-128">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="6d170-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolação segue a fórmula matemática associada à função de easing.</span><span class="sxs-lookup"><span data-stu-id="6d170-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="6d170-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolação segue interpolação de 100% menos a saída da fórmula associada à função de easing.</span><span class="sxs-lookup"><span data-stu-id="6d170-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="6d170-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Usa interpolação <xref:System.Windows.Media.Animation.EasingMode.EaseIn> para a primeira metade da animação e <xref:System.Windows.Media.Animation.EasingMode.EaseOut> para a segunda metade.</span><span class="sxs-lookup"><span data-stu-id="6d170-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="6d170-132">Os gráficos a seguir demonstram os diferentes valores de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> onde *f*(*x*) representa o progresso de animação e *t* representa a hora.</span><span class="sxs-lookup"><span data-stu-id="6d170-132">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="6d170-133">![Grafos de EasingMode BackEase.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-133">![BackEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="6d170-134">![Grafos de EasingMode BounceEase.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-134">![BounceEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="6d170-135">![Grafos de EasingMode CircleEase.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-135">![CircleEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="6d170-136">![Grafos de EasingMode CubicEase.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-136">![CubicEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="6d170-137">![ElasticEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-137">![ElasticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="6d170-138">![ExponentialEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-138">![ExponentialEase graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="6d170-139">![QuarticEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-139">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="6d170-140">![QuadraticEase com grafos de diferentes easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-140">![QuadraticEase with graphs of different easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="6d170-141">![QuarticEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-141">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="6d170-142">![QuinticEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-142">![QuinticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="6d170-143">![SineEase para diferentes valores de EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="6d170-143">![SineEase for different EasingMode values](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d170-144">Você pode usar <xref:System.Windows.Media.Animation.PowerEase> para criar o mesmo comportamento que <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, e <xref:System.Windows.Media.Animation.QuinticEase> usando o <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6d170-144">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="6d170-145">Por exemplo, se você quiser usar <xref:System.Windows.Media.Animation.PowerEase> para substituir <xref:System.Windows.Media.Animation.CubicEase>, especifique um <xref:System.Windows.Media.Animation.PowerEase.Power%2A> valor 3.</span><span class="sxs-lookup"><span data-stu-id="6d170-145">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="6d170-146">Além de usar as funções de atenuação incluídas no tempo de execução, você pode criar suas próprias funções personalizadas de atenuação herdando de <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="6d170-146">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="6d170-147">O exemplo a seguir demonstra como criar uma função de easing personalizada simples.</span><span class="sxs-lookup"><span data-stu-id="6d170-147">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="6d170-148">Você pode adicionar sua própria lógica de matemática para como a função de easing se comporta, substituindo o <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6d170-148">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>  
  
 [<span data-ttu-id="6d170-149">Executar esta amostra</span><span class="sxs-lookup"><span data-stu-id="6d170-149">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
