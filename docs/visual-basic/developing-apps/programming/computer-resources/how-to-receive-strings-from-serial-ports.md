---
title: 'Como: receber cadeias de caracteres de portas seriais'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 93b6b47d89d05331c85a6459bba7d6fd5e2e3377
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401830"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="a53f4-102">Como receber cadeias de caracteres de portas seriais no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a53f4-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="a53f4-103">Este tópico descreve como usar o `My.Computer.Ports` para receber cadeias de caracteres de portas seriais do computador em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a53f4-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="a53f4-104">Para receber cadeias de caracteres da porta serial</span><span class="sxs-lookup"><span data-stu-id="a53f4-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="a53f4-105">Inicialize a cadeia de caracteres de retorno.</span><span class="sxs-lookup"><span data-stu-id="a53f4-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="a53f4-106">Determine qual porta serial deve fornecer as cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a53f4-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="a53f4-107">Este exemplo assume que é `COM1`.</span><span class="sxs-lookup"><span data-stu-id="a53f4-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="a53f4-108">Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta.</span><span class="sxs-lookup"><span data-stu-id="a53f4-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="a53f4-109">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a53f4-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="a53f4-110">O bloco `Try...Catch...Finally` permite que o aplicativo feche a porta serial mesmo que ele gere uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a53f4-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="a53f4-111">Todo o código que manipula a porta serial deve aparecer dentro deste bloco.</span><span class="sxs-lookup"><span data-stu-id="a53f4-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="a53f4-112">Crie um loop de `Do` para ler linhas do texto até que não haja mais linhas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a53f4-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="a53f4-113">Use o método <xref:System.IO.Ports.SerialPort.ReadLine> para ler a próxima linha de texto disponível da porta serial.</span><span class="sxs-lookup"><span data-stu-id="a53f4-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="a53f4-114">Use uma instrução `If` para determinar se o método <xref:System.IO.Ports.SerialPort.ReadLine> retorna `Nothing` (o que significa que não há mais texto disponível).</span><span class="sxs-lookup"><span data-stu-id="a53f4-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="a53f4-115">Se ele retornar `Nothing`, saia do loop de `Do`.</span><span class="sxs-lookup"><span data-stu-id="a53f4-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="a53f4-116">Adicione um bloco `Else` à instrução `If` para lidar com o caso se a cadeia de caracteres for realmente lida.</span><span class="sxs-lookup"><span data-stu-id="a53f4-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="a53f4-117">O bloco acrescenta a cadeia de caracteres da porta serial à cadeia de caracteres de retorno.</span><span class="sxs-lookup"><span data-stu-id="a53f4-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="a53f4-118">Retorne a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a53f4-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="a53f4-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a53f4-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="a53f4-120">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a53f4-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a53f4-121">No selecionador de snippet de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="a53f4-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="a53f4-122">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a53f4-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a53f4-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a53f4-123">Compiling the Code</span></span>  

 <span data-ttu-id="a53f4-124">Este exemplo pressupõe que o computador esteja usando a `COM1`.</span><span class="sxs-lookup"><span data-stu-id="a53f4-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a53f4-125">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="a53f4-125">Robust Programming</span></span>  

 <span data-ttu-id="a53f4-126">Este exemplo pressupõe que o computador esteja usando a `COM1`.</span><span class="sxs-lookup"><span data-stu-id="a53f4-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="a53f4-127">Para obter mais flexibilidade, o código deve permitir que o usuário selecione a porta serial desejada na lista de portas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a53f4-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="a53f4-128">Para obter mais informações, consulte [Como mostrar portas seriais disponíveis](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="a53f4-128">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="a53f4-129">Este exemplo usa um bloco `Try...Catch...Finally` para garantir que o aplicativo feche a porta e capture quaisquer exceções de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a53f4-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="a53f4-130">Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a53f4-130">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a53f4-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="a53f4-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="a53f4-132">Como: discar modems anexados a portas seriais</span><span class="sxs-lookup"><span data-stu-id="a53f4-132">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="a53f4-133">Como: enviar cadeias de caracteres para portas seriais</span><span class="sxs-lookup"><span data-stu-id="a53f4-133">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="a53f4-134">Como: mostrar portas seriais disponíveis</span><span class="sxs-lookup"><span data-stu-id="a53f4-134">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
