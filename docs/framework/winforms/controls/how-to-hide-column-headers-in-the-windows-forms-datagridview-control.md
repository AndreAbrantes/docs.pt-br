---
title: Ocultar cabeçalhos de coluna no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: d84c93b0ad1c9ef456c73dd29af1de4857778999
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736589"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8ccc3-102">Como ocultar cabeçalhos no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ccc3-102">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8ccc3-103">Às vezes, você vai querer exibir um <xref:System.Windows.Forms.DataGridView> sem cabeçalhos de coluna.</span><span class="sxs-lookup"><span data-stu-id="8ccc3-103">Sometimes you will want to display a <xref:System.Windows.Forms.DataGridView> without column headers.</span></span> <span data-ttu-id="8ccc3-104">No controle <xref:System.Windows.Forms.DataGridView>, o valor da propriedade <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> determina se os cabeçalhos de coluna são exibidos.</span><span class="sxs-lookup"><span data-stu-id="8ccc3-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> property value determines whether the column headers are displayed.</span></span>  
  
### <a name="to-hide-the-column-headers"></a><span data-ttu-id="8ccc3-105">Para ocultar os cabeçalhos de coluna</span><span class="sxs-lookup"><span data-stu-id="8ccc3-105">To hide the column headers</span></span>  
  
- <span data-ttu-id="8ccc3-106">Defina a propriedade <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> como `false`.</span><span class="sxs-lookup"><span data-stu-id="8ccc3-106">Set the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ccc3-107">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="8ccc3-107">Compiling the Code</span></span>  
 <span data-ttu-id="8ccc3-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="8ccc3-108">This example requires:</span></span>  
  
- <span data-ttu-id="8ccc3-109">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="8ccc3-109">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="8ccc3-110">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ccc3-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccc3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ccc3-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8ccc3-112">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ccc3-112">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
