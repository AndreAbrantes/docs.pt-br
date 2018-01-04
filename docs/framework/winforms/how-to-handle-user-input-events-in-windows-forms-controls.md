---
title: "Como manipular eventos de entrada do usuário em controles do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8255d279f6a5e33df696673bae749f62b8ecf2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="41247-102">Como manipular eventos de entrada do usuário em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41247-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="41247-103">Este exemplo demonstra como tratar a maioria dos teclado, mouse, foco e eventos de validação que podem ocorrer em um controle de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="41247-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="41247-104">A caixa de texto denominada `TextBoxInput` recebe os eventos quando ela tem o foco e informações sobre cada evento são gravadas na caixa de texto denominada `TextBoxOutput` na ordem em que os eventos são gerados.</span><span class="sxs-lookup"><span data-stu-id="41247-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="41247-105">O aplicativo também inclui um conjunto de caixas de seleção que pode ser usado para filtrar quais eventos de relatório.</span><span class="sxs-lookup"><span data-stu-id="41247-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41247-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41247-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41247-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="41247-107">Compiling the Code</span></span>  
 <span data-ttu-id="41247-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="41247-108">This example requires:</span></span>  
  
-   <span data-ttu-id="41247-109">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="41247-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="41247-110">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="41247-110">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="41247-111">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="41247-111">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="41247-112">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="41247-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41247-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41247-113">See Also</span></span>  
 [<span data-ttu-id="41247-114">Entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41247-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
