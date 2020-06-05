---
title: 'Como: mostrar portas seriais disponíveis'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: e7a9166f1879ed0850ca893bed307a0318298bbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401817"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="739e0-102">Como mostrar portas seriais disponíveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="739e0-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="739e0-103">Este tópico descreve como usar `My.Computer.Ports` para mostrar as portas seriais do computador disponíveis em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="739e0-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="739e0-104">Para permitir que um usuário selecione qual porta usar, os nomes das portas seriais são colocados em um controle <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="739e0-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="739e0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="739e0-105">Example</span></span>  

 <span data-ttu-id="739e0-106">Este exemplo faz um loop em todas as cadeias de caracteres que a propriedade `My.Computer.Ports.SerialPortNames` retorna.</span><span class="sxs-lookup"><span data-stu-id="739e0-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="739e0-107">Essas cadeias de caracteres são os nomes das portas seriais disponíveis no computador.</span><span class="sxs-lookup"><span data-stu-id="739e0-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="739e0-108">Normalmente, um usuário seleciona qual porta serial o aplicativo deve usar na lista de portas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="739e0-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="739e0-109">Neste exemplo, os nomes das portas seriais são armazenados em um controle <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="739e0-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="739e0-110">Para saber mais, veja [Controle ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="739e0-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="739e0-111">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="739e0-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="739e0-112">No selecionador de snippet de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="739e0-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="739e0-113">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="739e0-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="739e0-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="739e0-114">Compiling the Code</span></span>  

 <span data-ttu-id="739e0-115">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="739e0-115">This example requires:</span></span>  
  
- <span data-ttu-id="739e0-116">Uma referência de projeto ao System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="739e0-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="739e0-117">Acesso aos membros do namespace <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="739e0-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="739e0-118">Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="739e0-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="739e0-119">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="739e0-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="739e0-120">Que seu formulário tenha um controle <xref:System.Windows.Forms.ListBox> chamado `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="739e0-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="739e0-121">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="739e0-121">Robust Programming</span></span>  

 <span data-ttu-id="739e0-122">Você não precisa usar o controle <xref:System.Windows.Forms.ListBox> para exibir os nomes das portas seriais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="739e0-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="739e0-123">Em vez disso, você pode usar um <xref:System.Windows.Forms.ComboBox> ou outro controle.</span><span class="sxs-lookup"><span data-stu-id="739e0-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="739e0-124">Se o aplicativo não precisa de uma resposta do usuário, você pode usar um controle <xref:System.Windows.Forms.TextBox> para exibir as informações.</span><span class="sxs-lookup"><span data-stu-id="739e0-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="739e0-125">Os nomes das portas retornados por `My.Computer.Ports.SerialPortNames` podem estar incorretos quando executados no Windows 98.</span><span class="sxs-lookup"><span data-stu-id="739e0-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="739e0-126">Para evitar erros de aplicativo, use o tratamento de exceções, como a instrução `Try...Catch...Finally` ou a instrução `Using`, ao usar os nomes de portas para abrir portas.</span><span class="sxs-lookup"><span data-stu-id="739e0-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="739e0-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="739e0-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="739e0-128">Como: discar modems anexados a portas seriais</span><span class="sxs-lookup"><span data-stu-id="739e0-128">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="739e0-129">Como: enviar cadeias de caracteres para portas seriais</span><span class="sxs-lookup"><span data-stu-id="739e0-129">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="739e0-130">Como: receber cadeias de caracteres de portas seriais</span><span class="sxs-lookup"><span data-stu-id="739e0-130">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
