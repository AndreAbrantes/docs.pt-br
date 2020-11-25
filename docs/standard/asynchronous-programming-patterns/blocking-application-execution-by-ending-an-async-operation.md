---
title: Bloqueando a execução de um aplicativo finalizando uma operação assíncrona
ms.date: 03/30/2017
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: d99c09c4ac087152407fa8dc12894c216f9f43dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716168"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a><span data-ttu-id="7b9af-102">Bloqueando a execução de um aplicativo finalizando uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="7b9af-102">Blocking Application Execution by Ending an Async Operation</span></span>

<span data-ttu-id="7b9af-103">Aplicativos que não continuem a executar outras tarefas enquanto aguardam os resultados de uma operação assíncrona devem bloquear até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="7b9af-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="7b9af-104">Use uma das opções a seguir para bloquear o thread principal do aplicativo ao aguardar a conclusão de uma operação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="7b9af-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="7b9af-105">Chame o método _OperationName_ de **end** de operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="7b9af-105">Call the asynchronous operations **End**_OperationName_ method.</span></span> <span data-ttu-id="7b9af-106">Esta abordagem será demonstrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="7b9af-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="7b9af-107">Use a <xref:System.IAsyncResult.AsyncWaitHandle%2A> Propriedade do <xref:System.IAsyncResult> retornada pelo método **begin**_OperationName_ da operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="7b9af-107">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="7b9af-108">Para obter um exemplo que demonstra essa abordagem, consulte [Bloqueando a execução de um aplicativo com um AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span><span class="sxs-lookup"><span data-stu-id="7b9af-108">For an example that demonstrates this approach, see [Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
 <span data-ttu-id="7b9af-109">Os aplicativos que usarem o método **End**_OperationName_ para bloqueio até a conclusão de uma operação assíncrona normalmente chamarão o método **Begin**_OperationName_, executarão qualquer trabalho que possa ser feito sem os resultados da operação e, em seguida, chamarão **End**_OperationName_.</span><span class="sxs-lookup"><span data-stu-id="7b9af-109">Applications that use the **End**_OperationName_ method to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then call **End**_OperationName_.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b9af-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b9af-110">Example</span></span>  

 <span data-ttu-id="7b9af-111">O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do Sistema de Nomes de Domínio de computadores especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7b9af-111">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="7b9af-112">Observe que `null` (`Nothing` no Visual Basic) é passado para os parâmetros <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` e `stateObject` porque esses argumentos não são necessários ao usar essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="7b9af-112">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these arguments are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7b9af-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b9af-113">See also</span></span>

- [<span data-ttu-id="7b9af-114">Padrão assíncrono baseado em evento (EAP)</span><span class="sxs-lookup"><span data-stu-id="7b9af-114">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="7b9af-115">Visão geral do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="7b9af-115">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
