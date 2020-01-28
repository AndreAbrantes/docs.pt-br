---
title: Adicionar e remover itens com controle ListView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: cab40c556d9e5d21ce15bcd3d4da367bc08f33ab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732303"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="b0069-102">Como adicionar e remover itens com o componente ListView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="b0069-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="b0069-103">O processo de adicionar um item a um controle de <xref:System.Windows.Forms.ListView> de Windows Forms consiste principalmente em especificar o item e atribuir propriedades a ele.</span><span class="sxs-lookup"><span data-stu-id="b0069-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="b0069-104">A adição ou remoção de itens de lista pode ser feita a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="b0069-104">Adding or removing list items can be done at any time.</span></span>

<span data-ttu-id="b0069-105">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="b0069-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="b0069-106">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b0069-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="b0069-107">Para adicionar ou remover itens usando o designer</span><span class="sxs-lookup"><span data-stu-id="b0069-107">To add or remove items using the designer</span></span>

1. <span data-ttu-id="b0069-108">Selecione o controle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="b0069-108">Select the <xref:System.Windows.Forms.ListView> control.</span></span>

2. <span data-ttu-id="b0069-109">Na janela **Propriedades** , clique nas **reticências** (![botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.ListView.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0069-109">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="b0069-110">O **Editor de coleção de ListViewItem** é exibido.</span><span class="sxs-lookup"><span data-stu-id="b0069-110">The **ListViewItem Collection Editor** appears.</span></span>

3. <span data-ttu-id="b0069-111">Para adicionar um item, clique no botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b0069-111">To add an item, click the **Add** button.</span></span> <span data-ttu-id="b0069-112">Em seguida, você pode definir as propriedades do novo item, como as propriedades <xref:System.Windows.Forms.ListView.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0069-112">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

4. <span data-ttu-id="b0069-113">Para remover um item, selecione-o e clique no botão **Remover**.</span><span class="sxs-lookup"><span data-stu-id="b0069-113">To remove an item, select it and click the **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0069-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="b0069-114">See also</span></span>

- [<span data-ttu-id="b0069-115">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="b0069-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="b0069-116">Como adicionar colunas ao controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0069-116">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b0069-117">Como Exibir Subitens em Colunas com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0069-117">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b0069-118">Como Exibir Ícones do Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0069-118">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b0069-119">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b0069-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="b0069-120">Como agrupar itens em um controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0069-120">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
