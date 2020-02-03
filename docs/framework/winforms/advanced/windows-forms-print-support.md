---
title: Suporte de impressão
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732496"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="b24b8-102">Suporte à impressão no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b24b8-102">Windows Forms Print Support</span></span>
<span data-ttu-id="b24b8-103">A impressão nos Windows Forms consiste principalmente em usar o [Componente PrintDocument](../controls/printdocument-component-windows-forms.md) para permitir que o usuário imprima e o [Controle PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md), o [Componente PrintDialog](../controls/printdialog-component-windows-forms.md) e o [Componente PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) para fornecer uma interface gráfica familiar aos usuários acostumados com o sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="b24b8-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="b24b8-104">Normalmente, você cria uma nova instância do componente <xref:System.Drawing.Printing.PrintDocument>, define as propriedades que descrevem o que imprimir usando as classes <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings> e chama o método <xref:System.Drawing.Printing.PrintDocument.Print%2A> para realmente imprimir o documento.</span><span class="sxs-lookup"><span data-stu-id="b24b8-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="b24b8-105">Durante a impressão de um aplicativo baseado no Windows, o componente <xref:System.Drawing.Printing.PrintDocument> mostrará uma caixa de diálogo anular impressão para alertar os usuários sobre o fato de que a impressão está ocorrendo e para permitir que o trabalho de impressão seja cancelado.</span><span class="sxs-lookup"><span data-stu-id="b24b8-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b24b8-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b24b8-106">In This Section</span></span>  
 [<span data-ttu-id="b24b8-107">Como Criar Trabalhos de Impressão Padrão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b24b8-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="b24b8-108">Explica como usar o componente <xref:System.Drawing.Printing.PrintDocument> para imprimir de um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="b24b8-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="b24b8-109">Como Capturar a Entrada do Usuário de um PrintDialog em Tempo de Execução</span><span class="sxs-lookup"><span data-stu-id="b24b8-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="b24b8-110">Explica como modificar as opções de impressão selecionadas programaticamente usando o componente <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="b24b8-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="b24b8-111">Como Escolher as Impressoras Conectadas ao Computador de um Usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b24b8-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="b24b8-112">Descreve como alterar a impressora para imprimir usando o componente <xref:System.Windows.Forms.PrintDialog> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b24b8-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="b24b8-113">Como Imprimir Elementos Gráficos nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b24b8-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="b24b8-114">Descreve o envio de elementos gráficos para a impressora.</span><span class="sxs-lookup"><span data-stu-id="b24b8-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="b24b8-115">Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b24b8-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="b24b8-116">Descreve o envio de texto para a impressora.</span><span class="sxs-lookup"><span data-stu-id="b24b8-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="b24b8-117">Como Concluir Trabalhos de Impressão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b24b8-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="b24b8-118">Explica como alertar usuários para a conclusão de um trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="b24b8-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="b24b8-119">Como imprimir um Windows Form</span><span class="sxs-lookup"><span data-stu-id="b24b8-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="b24b8-120">Mostra como imprimir uma cópia do formulário atual.</span><span class="sxs-lookup"><span data-stu-id="b24b8-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="b24b8-121">Como imprimir nos Windows Forms usando Visualização de Impressão</span><span class="sxs-lookup"><span data-stu-id="b24b8-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="b24b8-122">Mostra como usar um <xref:System.Windows.Forms.PrintPreviewDialog> para imprimir um documento.</span><span class="sxs-lookup"><span data-stu-id="b24b8-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b24b8-123">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="b24b8-123">Related Sections</span></span>  
 [<span data-ttu-id="b24b8-124">Componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="b24b8-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="b24b8-125">Explica o uso do componente <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="b24b8-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="b24b8-126">Componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="b24b8-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="b24b8-127">Explica o uso do componente <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="b24b8-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="b24b8-128">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="b24b8-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="b24b8-129">Explica o uso do controle de <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="b24b8-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="b24b8-130">Componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="b24b8-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="b24b8-131">Explica o uso do componente <xref:System.Windows.Forms.PageSetupDialog>.</span><span class="sxs-lookup"><span data-stu-id="b24b8-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="b24b8-132">Descreve as classes no namespace <xref:System.Drawing.Printing>.</span><span class="sxs-lookup"><span data-stu-id="b24b8-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
