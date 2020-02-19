---
title: Como pintar uma área com um gradiente linear
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 76c491632911c48db34d932ba3895278591378a5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452760"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="215e9-102">Como pintar uma área com um gradiente linear</span><span class="sxs-lookup"><span data-stu-id="215e9-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="215e9-103">Este exemplo mostra como usar a classe <xref:System.Windows.Media.LinearGradientBrush> para pintar uma área com um gradiente linear.</span><span class="sxs-lookup"><span data-stu-id="215e9-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="215e9-104">No exemplo a seguir, a <xref:System.Windows.Shapes.Shape.Fill%2A> de um <xref:System.Windows.Shapes.Rectangle> é pintada com um gradiente linear diagonal que faz a transição de amarelo para vermelho para azul para verde-limão.</span><span class="sxs-lookup"><span data-stu-id="215e9-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="215e9-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="215e9-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="215e9-106">A ilustração a seguir mostra o gradiente criado pelo exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="215e9-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="215e9-107">![Gradiente linear diagonal](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="215e9-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="215e9-108">Para criar um gradiente linear horizontal, altere o <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> do <xref:System.Windows.Media.LinearGradientBrush> para (0, 0.5) e (1, 0.5).</span><span class="sxs-lookup"><span data-stu-id="215e9-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="215e9-109">No exemplo a seguir, uma <xref:System.Windows.Shapes.Rectangle> é pintada com um gradiente linear horizontal.</span><span class="sxs-lookup"><span data-stu-id="215e9-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="215e9-110">A ilustração a seguir mostra o gradiente criado pelo exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="215e9-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="215e9-111">![Um gradiente linear horizontal](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="215e9-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="215e9-112">Para criar um gradiente linear vertical, altere o <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> do <xref:System.Windows.Media.LinearGradientBrush> para (0.5, 0) e (0.5, 1).</span><span class="sxs-lookup"><span data-stu-id="215e9-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="215e9-113">No exemplo a seguir, uma <xref:System.Windows.Shapes.Rectangle> é pintada com um gradiente linear vertical.</span><span class="sxs-lookup"><span data-stu-id="215e9-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="215e9-114">A ilustração a seguir mostra o gradiente criado pelo exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="215e9-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="215e9-115">![Gradiente linear vertical](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="215e9-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="215e9-116">Os exemplos neste tópico usam o sistema de coordenadas padrão para definir pontos de início e pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="215e9-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="215e9-117">O sistema de coordenadas padrão é relativo a uma caixa delimitadora: 0 indica 0% da caixa delimitadora e 1 indica 100% da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="215e9-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="215e9-118">Você pode alterar esse sistema de coordenadas definindo a propriedade <xref:System.Windows.Media.GradientBrush.MappingMode%2A> para o valor <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="215e9-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="215e9-119">Um sistema de coordenadas absoluto não é relativo a uma caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="215e9-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="215e9-120">Os valores são interpretados diretamente no espaço local.</span><span class="sxs-lookup"><span data-stu-id="215e9-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="215e9-121">Para obter exemplos adicionais, veja [Exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="215e9-121">For additional examples, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="215e9-122">Para obter mais informações sobre gradientes e outros tipos de pincéis, veja [Visão geral de pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="215e9-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
