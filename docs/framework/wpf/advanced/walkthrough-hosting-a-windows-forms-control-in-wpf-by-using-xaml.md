---
title: Hospedar um controle de Windows Forms no WPF usando XAML
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 2c5764ac2dfd9f5747087cc76e3971c002f12b90
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794198"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="8490e-102">Instruções passo a passo: hospedando um controle dos Windows Forms no WPF usando XAML</span><span class="sxs-lookup"><span data-stu-id="8490e-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
<span data-ttu-id="8490e-103">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece muitos controles com um amplo conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="8490e-103">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides many controls with a rich feature set.</span></span> <span data-ttu-id="8490e-104">No entanto, às vezes você pode querer usar controles de Windows Forms em suas páginas de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8490e-104">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="8490e-105">Por exemplo, você pode ter um investimento substancial em controles de Windows Forms existentes ou pode ter um controle de Windows Forms que fornece funcionalidade exclusiva.</span><span class="sxs-lookup"><span data-stu-id="8490e-105">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="8490e-106">Este tutorial mostra como hospedar um Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> controle em uma página [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8490e-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="8490e-107">Para uma listagem de código completa de todas as tarefas mostradas neste passo a passo, veja [Hospedando um controle dos Windows Forms no WPF usando exemplo XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="8490e-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="8490e-108">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8490e-108">Prerequisites</span></span>  

<span data-ttu-id="8490e-109">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="8490e-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="8490e-110">Hospedando o controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8490e-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="8490e-111">Para hospedar o controle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="8490e-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="8490e-112">Crie um projeto de aplicativo WPF chamado `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="8490e-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="8490e-113">Adicione referências aos assemblies a seguir.</span><span class="sxs-lookup"><span data-stu-id="8490e-113">Add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="8490e-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="8490e-114">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="8490e-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="8490e-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="8490e-116">Abra o MainWindow.xaml no WPF Designer.</span><span class="sxs-lookup"><span data-stu-id="8490e-116">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
4. <span data-ttu-id="8490e-117">No elemento <xref:System.Windows.Window>, adicione o seguinte mapeamento de namespace.</span><span class="sxs-lookup"><span data-stu-id="8490e-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="8490e-118">O mapeamento de namespace `wf` estabelece uma referência ao assembly que contém o controle de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8490e-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="8490e-119">No elemento <xref:System.Windows.Controls.Grid>, adicione o XAML a seguir.</span><span class="sxs-lookup"><span data-stu-id="8490e-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="8490e-120">O controle de <xref:System.Windows.Forms.MaskedTextBox> é criado como um filho do controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="8490e-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="8490e-121">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8490e-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8490e-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="8490e-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="8490e-123">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8490e-123">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="8490e-124">Passo a passo: hospedando um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="8490e-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="8490e-125">Passo a passo: hospedando um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="8490e-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="8490e-126">Passo a passo: hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8490e-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="8490e-127">Controles dos Windows Forms e controles WPF equivalentes</span><span class="sxs-lookup"><span data-stu-id="8490e-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="8490e-128">Hospedando um controle dos Windows Forms no WPF usando um exemplo XAML</span><span class="sxs-lookup"><span data-stu-id="8490e-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
