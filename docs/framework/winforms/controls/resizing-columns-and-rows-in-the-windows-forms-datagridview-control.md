---
title: Redimensionar colunas e linhas no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8f8394a837ccc11c469f9ad4feeb60464d0014fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742418"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7963a-102">Redimensionando colunas e linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7963a-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7963a-103">O controle `DataGridView` fornece diversas opções para personalizar o comportamento de dimensionamento de suas colunas e linhas.</span><span class="sxs-lookup"><span data-stu-id="7963a-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="7963a-104">Normalmente, células `DataGridView` não são redimensionados com base em seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7963a-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="7963a-105">Em vez disso, elas cortam qualquer valor de exibição maior do que a célula.</span><span class="sxs-lookup"><span data-stu-id="7963a-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="7963a-106">Se o conteúdo puder ser exibido como uma cadeia de caracteres, a célula o exibirá em uma dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="7963a-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="7963a-107">Por padrão, os usuários poderão arrastar os divisores de linha, coluna e cabeçalho com o mouse para mostrar mais informações.</span><span class="sxs-lookup"><span data-stu-id="7963a-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="7963a-108">Os usuários também podem clicar duas vezes em um divisor para redimensionar automaticamente a faixa da linha, coluna ou cabeçalho associado ao conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7963a-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="7963a-109">O controle `DataGridView` fornece propriedades, métodos e eventos que permitem personalizar ou desabilitar todos esses comportamentos causados voltados para o usuário.</span><span class="sxs-lookup"><span data-stu-id="7963a-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="7963a-110">Além disso, é possível redimensionar linhas, colunas e cabeçalhos com programação para ajustar o conteúdo ou configurá-los para redimensionarem a si próprios automaticamente sempre que seu conteúdo mudar.</span><span class="sxs-lookup"><span data-stu-id="7963a-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="7963a-111">Você também pode configurar colunas para dividir automaticamente a largura disponível do controle em proporções especificadas.</span><span class="sxs-lookup"><span data-stu-id="7963a-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7963a-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7963a-112">In This Section</span></span>  
 <span data-ttu-id="7963a-113">[Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7963a-113">[Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md)</span></span>  
 <span data-ttu-id="7963a-114">Descreve as opções para dimensionar linhas, colunas e cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="7963a-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="7963a-115">Também fornece detalhes sobre os métodos e propriedades relacionados ao dimensionamento e descreve os cenários comuns de uso.</span><span class="sxs-lookup"><span data-stu-id="7963a-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="7963a-116">Modo de preenchimento de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7963a-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7963a-117">Descreve o modo de preenchimento de coluna em detalhes e fornece código de demonstração que pode ser usado para experimentar o modo de preenchimento de coluna e outros modos.</span><span class="sxs-lookup"><span data-stu-id="7963a-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="7963a-118">Como definir os modos de dimensionamento do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7963a-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7963a-119">Descreve como configurar os modos de dimensionamento para fins comuns.</span><span class="sxs-lookup"><span data-stu-id="7963a-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="7963a-120">Como redimensionar de forma programática as células para ajustar o conteúdo no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7963a-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="7963a-121">Fornece código de demonstração que pode ser usado para experimentar o redimensionamento com programação.</span><span class="sxs-lookup"><span data-stu-id="7963a-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="7963a-122">Como redimensionar automaticamente células quando o conteúdo é alterado no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7963a-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="7963a-123">Fornece código de demonstração que pode ser usado para experimentar os modos de dimensionamento automáticos.</span><span class="sxs-lookup"><span data-stu-id="7963a-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7963a-124">Referência</span><span class="sxs-lookup"><span data-stu-id="7963a-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="7963a-125">Fornece documentação de referência para o controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7963a-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7963a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7963a-126">See also</span></span>

- [<span data-ttu-id="7963a-127">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="7963a-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
