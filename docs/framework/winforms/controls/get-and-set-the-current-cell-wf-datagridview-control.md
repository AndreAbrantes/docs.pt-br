---
title: Obter e definir a célula atual no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0fb01d5392e02b53e0e5bf905c872dbeeb22fad9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745669"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2db27-102">Como obter e definir a célula atual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2db27-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2db27-103">A interação com o <xref:System.Windows.Forms.DataGridView> geralmente exige que você descubra programaticamente qual célula está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="2db27-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="2db27-104">Talvez você precise alterar a célula atual.</span><span class="sxs-lookup"><span data-stu-id="2db27-104">You may also need to change the current cell.</span></span> <span data-ttu-id="2db27-105">Você pode executar essas tarefas com a propriedade <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.</span><span class="sxs-lookup"><span data-stu-id="2db27-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2db27-106">Não é possível definir a célula atual em uma linha ou coluna que tenha sua propriedade <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="2db27-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="2db27-107">Dependendo do modo de seleção do controle de <xref:System.Windows.Forms.DataGridView>, alterar a célula atual pode alterar a seleção.</span><span class="sxs-lookup"><span data-stu-id="2db27-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="2db27-108">Para obter mais informações, veja [Modos de seleção do controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2db27-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="2db27-109">Para obter a célula atual de forma programática</span><span class="sxs-lookup"><span data-stu-id="2db27-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="2db27-110">Use a propriedade <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> do controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="2db27-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="2db27-111">Para definir a célula atual de forma programática</span><span class="sxs-lookup"><span data-stu-id="2db27-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="2db27-112">Defina a propriedade <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> do controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="2db27-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="2db27-113">No exemplo de código a seguir, a célula atual é definida como linha 0, coluna 1.</span><span class="sxs-lookup"><span data-stu-id="2db27-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2db27-114">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="2db27-114">Compiling the Code</span></span>  
 <span data-ttu-id="2db27-115">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2db27-115">This example requires:</span></span>  
  
- <span data-ttu-id="2db27-116"><xref:System.Windows.Forms.Button> controles chamados `getCurrentCellButton` e `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="2db27-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="2db27-117">No Visual C#, você deve anexar os eventos de <xref:System.Windows.Forms.Control.Click> para cada botão ao manipulador de eventos associado no código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="2db27-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="2db27-118">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="2db27-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="2db27-119">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2db27-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db27-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="2db27-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2db27-121">Recursos básicos de coluna, linha e célula no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2db27-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="2db27-122">Modos de seleção no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2db27-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
