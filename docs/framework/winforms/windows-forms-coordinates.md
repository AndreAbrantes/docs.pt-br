---
title: Coordenadas
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: c95888f31bfc867e9c028d53072ab3d710256708
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734668"
---
# <a name="windows-forms-coordinates"></a>Coordenadas do Windows Forms
O sistema de coordenadas para um Windows Form é baseado nas coordenadas de dispositivo e a unidade básica de medida de desenho no Windows Forms é a unidade do dispositivo (normalmente, o pixel). Pontos na tela são descritos por pares de coordenadas x e y, com as coordenadas x aumentando para a direita e coordenadas y aumentando de cima para baixo. O local de origem, em relação à tela, variará dependendo se você está especificando as coordenadas de tela ou de cliente.  
  
## <a name="screen-coordinates"></a>Coordenadas de tela  
 Um Aplicativo do Windows Forms especifica a posição de uma janela na tela em coordenadas de tela. Para coordenadas de tela, a origem é o canto superior esquerdo da tela. A posição completa de uma janela geralmente é descrita por uma estrutura de <xref:System.Drawing.Rectangle> que contém as coordenadas de tela de dois pontos que definem os cantos superior esquerdo e inferior direito da janela.  
  
## <a name="client-coordinates"></a>Coordenadas de cliente  
 Um Aplicativo do Windows Forms especifica a posição dos pontos em um formulário ou controle usando coordenadas de cliente. A origem das coordenadas de cliente é o canto superior esquerdo da área de cliente do controle ou formulário. Coordenadas de cliente garantem que um aplicativo pode usar valores de coordenadas consistentes ao desenhar em um formulário ou controle, independentemente da posição do formulário ou controle na tela.  
  
 As dimensões da área do cliente também são descritas por uma estrutura de <xref:System.Drawing.Rectangle> que contém as coordenadas do cliente para a área. Em todos os casos, a coordenada superior esquerda do retângulo está incluída na área de cliente, enquanto a coordenada inferior direita é excluída. Operações de elementos gráficos não incluem bordas direita e inferiores de uma área de cliente. Por exemplo, o método <xref:System.Drawing.Graphics.FillRectangle%2A> preencherá a borda direita e inferior do retângulo especificado, mas não incluirá essas bordas.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Mapeamento de um tipo de coordenada para outro  
 Ocasionalmente, pode ser recomendável mapear das coordenadas de tela para as coordenadas de cliente. Você pode fazer isso facilmente usando os métodos <xref:System.Windows.Forms.Control.PointToClient%2A> e <xref:System.Windows.Forms.Control.PointToScreen%2A> disponíveis na classe <xref:System.Windows.Forms.Control>. Por exemplo, a propriedade <xref:System.Windows.Forms.Control.MousePosition%2A> de <xref:System.Windows.Forms.Control> é relatada em coordenadas da tela, mas talvez você queira convertê-las em coordenadas do cliente.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
