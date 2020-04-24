---
title: 'Como: registrar exceções em log'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352082"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="a5114-102">Como registrar em log as exceções no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5114-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="a5114-103">É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log informações sobre exceções que ocorrem em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5114-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="a5114-104">Esses exemplos mostram como usar o método `My.Application.Log.WriteException` para registrar em log exceções capturadas explicitamente e exceções sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="a5114-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="a5114-105">Para registrar informações de rastreamento de registros em log, use o método `My.Application.Log.WriteEntry`.</span><span class="sxs-lookup"><span data-stu-id="a5114-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="a5114-106">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5114-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="a5114-107">Registrar em log uma exceção manipulada</span><span class="sxs-lookup"><span data-stu-id="a5114-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="a5114-108">Crie o método que gerará as informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="a5114-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="a5114-109">Use um bloco `Try...Catch` para capturar a exceção.</span><span class="sxs-lookup"><span data-stu-id="a5114-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="a5114-110">Coloque o código que poderá gerar uma exceção no bloco `Try`.</span><span class="sxs-lookup"><span data-stu-id="a5114-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="a5114-111">Remova a marca de comentário das linhas `Dim` e `MsgBox` para lançar uma exceção <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="a5114-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="a5114-112">No bloco `Catch`, use o método `My.Application.Log.WriteException` para gravar as informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="a5114-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="a5114-113">O exemplo a seguir mostra o código completo para registrar em log uma exceção manipulada.</span><span class="sxs-lookup"><span data-stu-id="a5114-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="a5114-114">Registrar em log uma exceção sem tratamento</span><span class="sxs-lookup"><span data-stu-id="a5114-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="a5114-115">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="a5114-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a5114-116">No menu **projeto** , escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a5114-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="a5114-117">Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="a5114-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="a5114-118">Clique no botão **Exibir Eventos de Aplicativo** para abrir o Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="a5114-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="a5114-119">Isso abrirá o arquivo ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="a5114-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="a5114-120">Abra o arquivo ApplicationEvents.vb no Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="a5114-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="a5114-121">No menu **Geral**, escolha **Eventos MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="a5114-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="a5114-122">No menu **Declarações**, escolha **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="a5114-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="a5114-123">A aplicativo gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> antes da execução do aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="a5114-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="a5114-124">Adicione o método `My.Application.Log.WriteException` ao manipulador de eventos `UnhandledException`.</span><span class="sxs-lookup"><span data-stu-id="a5114-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="a5114-125">O exemplo a seguir mostra o código completo para registrar em log uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="a5114-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a5114-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="a5114-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="a5114-127">Trabalhar com logs do aplicativo</span><span class="sxs-lookup"><span data-stu-id="a5114-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="a5114-128">Como: gravar mensagens de log</span><span class="sxs-lookup"><span data-stu-id="a5114-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="a5114-129">Passo a passo: determinar o local no qual My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="a5114-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="a5114-130">Passo a passo: alterar o local no qual My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="a5114-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
