---
title: Como animar em um estilo
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 0b29648bf15f0046adcdee610f9565f7deb24972
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744885"
---
# <a name="how-to-animate-in-a-style"></a>Como animar em um estilo

Este exemplo mostra como animar propriedades em um estilo. Ao animar em um estilo, somente o elemento de estrutura para o qual o estilo está definido pode ser alvo diretamente. Para direcionar um objeto freezable, é preciso fazer a "marcação" de uma propriedade do elemento.

No exemplo a seguir, várias animações são definidas dentro de um estilo e aplicadas a uma <xref:System.Windows.Controls.Button>. Quando o usuário move o mouse sobre o botão, ele passa de opaco a parcialmente translúcido e repete o processo. Quando o usuário move o mouse para fora do botão, este fica completamente opaco. Quando o botão é clicado, sua cor da tela de fundo muda de laranja para branco e volta a cor original. Como o <xref:System.Windows.Media.SolidColorBrush> usado para pintar o botão não pode ser direcionado diretamente, ele é acessado com o pontilhamento da propriedade <xref:System.Windows.Controls.Control.Background%2A> do botão.

## <a name="example"></a>{1&gt;Exemplo&lt;1}

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Observe que ao animar dentro de um estilo, é possível segmentar objetos que não existem. Por exemplo, suponha que seu estilo use uma <xref:System.Windows.Media.SolidColorBrush> para definir a propriedade de plano de fundo de um botão, mas em algum momento o estilo é substituído e o plano de fundo do botão é definido com um <xref:System.Windows.Media.LinearGradientBrush>.  Tentar animar a <xref:System.Windows.Media.SolidColorBrush> não gerará uma exceção; a animação simplesmente falhará silenciosamente.

Para obter mais informações sobre a sintaxe de direcionamento de storyboard, consulte a [visão geral de storyboards](storyboards-overview.md). Para mais informações sobre animação, consulte [Visão Geral de Animação](animation-overview.md). Para mais informações sobre estilos, consulte [Estilos e Modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md).
