---
title: 'Solução de problemas: ouvintes de log'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74346862"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="37d70-102">Solucionando problemas: ouvintes de log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37d70-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="37d70-103">É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37d70-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="37d70-104">Para determinar quais ouvintes de log recebem essas mensagens, consulte [Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="37d70-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="37d70-105">O objeto `Log` pode usar filtragem de log para limitar a quantidade de informações que ele registra no log.</span><span class="sxs-lookup"><span data-stu-id="37d70-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="37d70-106">Se os filtros tiverem sido configurados incorretamente, os logs poderão conter informações incorretas.</span><span class="sxs-lookup"><span data-stu-id="37d70-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="37d70-107">Para obter informações sobre filtragem, consulte [Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="37d70-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="37d70-108">No entanto, se um log tiver sido configurado incorretamente, talvez seja necessário obter mais informações sobre sua configuração atual.</span><span class="sxs-lookup"><span data-stu-id="37d70-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="37d70-109">É possível obter essas informações por meio da propriedade `TraceSource` avançada do log.</span><span class="sxs-lookup"><span data-stu-id="37d70-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="37d70-110">Para determinar os ouvintes de log do objeto Log no código</span><span class="sxs-lookup"><span data-stu-id="37d70-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="37d70-111">Importe o namespace <xref:System.Diagnostics> no início do arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="37d70-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="37d70-112">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="37d70-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="37d70-113">Crie uma função que retorna uma cadeia de caracteres que consiste de informações para cada um dos ouvintes de log.</span><span class="sxs-lookup"><span data-stu-id="37d70-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="37d70-114">Passe a coleção dos ouvintes de rastreamento do log para a função `GetListeners` e exiba o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="37d70-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="37d70-115">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="37d70-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d70-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="37d70-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="37d70-117">Trabalhar com logs do aplicativo</span><span class="sxs-lookup"><span data-stu-id="37d70-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="37d70-118">Passo a passo: determinar o local no qual My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="37d70-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
