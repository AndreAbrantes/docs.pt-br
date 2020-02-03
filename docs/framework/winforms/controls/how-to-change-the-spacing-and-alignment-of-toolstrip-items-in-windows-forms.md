---
title: Como alterar o espaçamento e o alinhamento de itens ToolStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746555"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Como alterar o espaçamento e o alinhamento de itens ToolStrip nos Windows Forms
O controle de <xref:System.Windows.Forms.ToolStrip> dá suporte total a recursos de layout, como o dimensionamento, o espaçamento de <xref:System.Windows.Forms.ToolStripItem> controles relativos entre si, a disposição dos controles na <xref:System.Windows.Forms.ToolStrip>e o espaçamento de controles relativos à <xref:System.Windows.Forms.ToolStrip>.  
  
 Como o valor padrão da propriedade <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> é `true`, os controles são dimensionados automaticamente, a menos que você defina a propriedade <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> como `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Para dimensionar manualmente um ToolStripItem  
  
1. Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> como `false` para o controle associado.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Size%2A> da maneira desejada para o <xref:System.Windows.Forms.ToolStripItem>associado.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Para definir o espaçamento de um ToolStripItem  
  
1. Insira os valores desejados, em pixels, na propriedade <xref:System.Windows.Forms.ToolStripItem.Margin%2A> do controle associado.  
  
     Os valores da propriedade <xref:System.Windows.Forms.ToolStripItem.Margin%2A> especificam o espaçamento entre o item e os itens adjacentes nesta ordem: esquerda, superior, direita e inferior.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Para alinhar um ToolStripItem à direita de ToolStrip  
  
1. Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> como <xref:System.Windows.Forms.ToolStripItemAlignment.Right> para o controle associado. Por padrão, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é definido como <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, que alinha os controles ao lado esquerdo da <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Para organizar itens de ToolStrip no ToolStrip  
  
- Defina a propriedade <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> como o valor de <xref:System.Windows.Forms.ToolStripLayoutStyle> que você deseja.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle do ToolStrip](toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
