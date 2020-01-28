---
title: Exibir ícones para controle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744509"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Como exibir ícones do controle ListView dos Windows Forms
O controle de <xref:System.Windows.Forms.ListView> de Windows Forms pode exibir ícones de três listas de imagens. Os modos de exibição lista, detalhes e SmallIcon exibem imagens da lista de imagens especificada na propriedade <xref:System.Windows.Forms.ListView.SmallImageList%2A>. A exibição LargeIcon exibe imagens da lista de imagens especificada na propriedade <xref:System.Windows.Forms.ListView.LargeImageList%2A>. Um modo de exibição de lista também pode exibir um conjunto adicional de ícones, definido na propriedade <xref:System.Windows.Forms.ListView.StateImageList%2A>, ao lado dos ícones grandes ou pequenos. Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Para exibir imagens em uma exibição de lista  
  
1. Defina a propriedade apropriada —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>ou <xref:System.Windows.Forms.ListView.StateImageList%2A>— para o componente <xref:System.Windows.Forms.ImageList> existente que você deseja usar.  
  
     Essas propriedades podem ser definidas no designer com a janela Propriedades ou no código.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. Defina a propriedade <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> ou <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> para cada item de lista que tenha um ícone associado.  
  
     Essas propriedades podem ser definidas no código ou no **Editor de coleção ListViewItem**. Para abrir o **Editor de coleção ListViewItem**, clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Items%2A> na janela **Propriedades** .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Veja também

- [Visão geral do controle ListView](listview-control-overview-windows-forms.md)
- [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Como adicionar colunas ao controle ListView do Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Componente ImageList](imagelist-component-windows-forms.md)
