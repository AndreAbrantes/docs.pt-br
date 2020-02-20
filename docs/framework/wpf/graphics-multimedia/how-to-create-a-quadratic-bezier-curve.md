---
title: Como criar uma curva de Bézier quadrática
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452065"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>Como criar uma curva de Bézier quadrática
Este exemplo mostra como criar uma curva de Bézier quadrática.  Para criar uma curva de Bézier quadrática, use as classes <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>e <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
## <a name="example"></a>Exemplo  
 Nos exemplos a seguir, uma curva de Bezier quadrática é desenhada de (10.100) para (300.100). A curva tem um ponto de controle de (200.200).  
  
 XAML  
  
 No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], você pode usar a sintaxe de atributo para descrever um caminho.  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 XAML  
  
 (Observe que essa sintaxe de atributo, na verdade, cria uma <xref:System.Windows.Media.StreamGeometry>, uma versão de peso mais leve de um <xref:System.Windows.Media.PathGeometry>. Para obter mais informações, consulte a página [sintaxe de marcação de caminho](path-markup-syntax.md) .)  
  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode desenhar uma curva de Bezier quadrática usando a sintaxe do elemento de objeto. O seguinte é equivalente ao exemplo de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior.  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Este exemplo faz parte de um exemplo maior; para ver o exemplo completo, confira o [Exemplo de geometrias](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Confira também

- [Criar um arco elíptico](how-to-create-an-elliptical-arc.md)
- [Criar uma curva de Bézier cúbica](how-to-create-a-cubic-bezier-curve.md)
