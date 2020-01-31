---
title: Como acessar coleções com chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 717ba9cc8605da08701de1bd13d6bc6da1c9b758
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739619"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Como acessar coleções indexadas por chave no Windows Forms

- Você pode acessar itens de coleção individuais por chave. Essa funcionalidade foi adicionada a muitas classes de coleção que normalmente são usadas por aplicativos dos Windows Forms. A lista a seguir exibe algumas das classes de coleção que têm coleções acessíveis por chave:  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Normalmente, a chave associada a um item em uma coleção é o nome do item. Os procedimentos a seguir mostram como usar classes de coleção para executar tarefas comuns.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Para localizar e colocar em foco um controle aninhado em uma coleção de controles  
  
- Use os métodos <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> e <xref:System.Windows.Forms.Control.Focus%2A> para especificar o nome do controle para localizar e dar o foco.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Para acessar uma imagem em uma coleção de imagens  
  
- Use a propriedade <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> para especificar o nome da imagem que você deseja acessar.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Para definir uma página da guia como a guia selecionada  
  
- Use a propriedade <xref:System.Windows.Forms.TabControl.SelectedTab%2A> junto com a propriedade <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> para especificar o nome da página da guia a ser definida como a guia selecionada.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Veja também

- [Introdução ao Windows Forms](getting-started-with-windows-forms.md)
- [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
