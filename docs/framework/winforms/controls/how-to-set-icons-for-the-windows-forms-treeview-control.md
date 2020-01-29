---
title: Definir ícones para controle TreeView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: e3d7fc35c6d9f70822cdd0b69dd12f3d469f4ffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737269"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="7bf48-102">Como definir ícones para o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7bf48-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="7bf48-103">O controle de <xref:System.Windows.Forms.TreeView> de Windows Forms pode exibir ícones ao lado de cada nó.</span><span class="sxs-lookup"><span data-stu-id="7bf48-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="7bf48-104">Os ícones são posicionados imediatamente à esquerda do texto do nó.</span><span class="sxs-lookup"><span data-stu-id="7bf48-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="7bf48-105">Para exibir esses ícones, você deve associar o modo de exibição de árvore a um controle de <xref:System.Windows.Forms.ImageList>.</span><span class="sxs-lookup"><span data-stu-id="7bf48-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="7bf48-106">Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="7bf48-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7bf48-107">Um bug no Microsoft .NET Framework versão 1,1 impede que as imagens apareçam em nós <xref:System.Windows.Forms.TreeView> quando seu aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7bf48-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7bf48-108">Para contornar esse bug, chame <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> no método `Main` imediatamente após chamar <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="7bf48-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="7bf48-109">Esse bug é corrigido no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="7bf48-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="7bf48-110">Para exibir imagens em um modo de exibição de árvore</span><span class="sxs-lookup"><span data-stu-id="7bf48-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="7bf48-111">Defina a propriedade <xref:System.Windows.Forms.TreeView.ImageList%2A> do controle de <xref:System.Windows.Forms.TreeView> como o controle de <xref:System.Windows.Forms.ImageList> existente que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="7bf48-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="7bf48-112">Essas propriedades podem ser definidas no designer com a janela Propriedades ou no código.</span><span class="sxs-lookup"><span data-stu-id="7bf48-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="7bf48-113">Defina as propriedades de <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> e <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> do nó.</span><span class="sxs-lookup"><span data-stu-id="7bf48-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="7bf48-114">A propriedade <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> determina a imagem exibida para os Estados normal e expandido do nó, e a propriedade <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> determina a imagem exibida para o estado selecionado do nó.</span><span class="sxs-lookup"><span data-stu-id="7bf48-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="7bf48-115">Essas propriedades podem ser definidas no código ou no Editor TreeNode.</span><span class="sxs-lookup"><span data-stu-id="7bf48-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="7bf48-116">Para abrir o editor de TreeNode, clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="7bf48-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7bf48-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="7bf48-117">See also</span></span>

- [<span data-ttu-id="7bf48-118">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="7bf48-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="7bf48-119">Como adicionar e remover nós com o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7bf48-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="7bf48-120">Como iterar em todos os nós de um controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7bf48-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="7bf48-121">Como determinar qual nó TreeView foi clicado</span><span class="sxs-lookup"><span data-stu-id="7bf48-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="7bf48-122">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7bf48-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
