---
title: "Como criar um botão que tenha uma imagem"
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
helpviewer_keywords: Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa3aa5454629d53fd8864df6a4f204e22028208f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Como criar um botão que tenha uma imagem
Este exemplo mostra como incluir uma imagem em um <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois <xref:System.Windows.Controls.Button> controles. Um <xref:System.Windows.Controls.Button> contém texto e o outro contém uma imagem. A imagem está em uma pasta chamada dados, que é uma subpasta da pasta de projeto de exemplo. Quando um usuário clica o <xref:System.Windows.Controls.Button> que tem a imagem, o plano de fundo e o texto do outro <xref:System.Windows.Controls.Button> alterar.  
  
 Este exemplo cria <xref:System.Windows.Controls.Button> controla usando marcação, mas usa o código para escrever o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipuladores de eventos.  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Consulte também  
 [Controles](../../../../docs/framework/wpf/controls/index.md)  
 [Biblioteca de controles](../../../../docs/framework/wpf/controls/control-library.md)
