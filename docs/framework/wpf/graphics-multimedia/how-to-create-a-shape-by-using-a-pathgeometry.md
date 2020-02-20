---
title: Como criar uma forma usando um PathGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452039"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="1ac31-102">Como criar uma forma usando um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="1ac31-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="1ac31-103">Este exemplo mostra como criar uma forma usando a classe <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="1ac31-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="1ac31-104"><xref:System.Windows.Media.PathGeometry> objetos são compostos de um ou mais objetos de <xref:System.Windows.Media.PathFigure>; cada <xref:System.Windows.Media.PathFigure> representa uma "figura" ou forma diferente.</span><span class="sxs-lookup"><span data-stu-id="1ac31-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="1ac31-105">Cada <xref:System.Windows.Media.PathFigure> é composta de um ou mais objetos <xref:System.Windows.Media.PathSegment>, cada um representando uma parte conectada da figura ou forma.</span><span class="sxs-lookup"><span data-stu-id="1ac31-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="1ac31-106">Os tipos de segmento incluem <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>e <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="1ac31-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ac31-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ac31-107">Example</span></span>  
 <span data-ttu-id="1ac31-108">O exemplo a seguir usa um <xref:System.Windows.Media.PathGeometry> para criar um triângulo.</span><span class="sxs-lookup"><span data-stu-id="1ac31-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="1ac31-109">O <xref:System.Windows.Media.PathGeometry> é exibido usando um elemento <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="1ac31-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="1ac31-110">A ilustração a seguir mostra a forma criada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1ac31-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="1ac31-111">![Uma PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="1ac31-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="1ac31-112">Um triângulo criado com um PathGeometry</span><span class="sxs-lookup"><span data-stu-id="1ac31-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="1ac31-113">O exemplo anterior mostrou como criar uma forma relativamente simples: um triângulo.</span><span class="sxs-lookup"><span data-stu-id="1ac31-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="1ac31-114">Um <xref:System.Windows.Media.PathGeometry> também pode ser usado para criar formas mais complexas, incluindo arcos e curvas.</span><span class="sxs-lookup"><span data-stu-id="1ac31-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="1ac31-115">Para obter exemplos, veja [Criar um arco elíptico](how-to-create-an-elliptical-arc.md), [Criar uma curva de Bézier cúbica](how-to-create-a-cubic-bezier-curve.md) e [Criar uma curva de Bézier quadrática](how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="1ac31-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="1ac31-116">Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="1ac31-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac31-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ac31-117">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="1ac31-118">Visão geral de geometria</span><span class="sxs-lookup"><span data-stu-id="1ac31-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="1ac31-119">Exemplo de geometrias</span><span class="sxs-lookup"><span data-stu-id="1ac31-119">Geometries Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
