---
title: Como cancelar uma tarefa e seus filhos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 4e0e783a4dfe3bf3a55795d7baef461369d7405a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134197"
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Como cancelar uma tarefa e seus filhos
Estes exemplos mostram como realizar as seguintes tarefas:  
  
1. Crie e inicie uma tarefa cancelável.  
  
2. Passe um token de cancelamento para o representante de usuário e, opcionalmente, para a instância da tarefa.  
  
3. Observe e responda à solicitação de cancelamento de seu representante de usuário.  
  
4. Opcionalmente, observe no thread de chamada que a tarefa foi cancelada.  
  
 O thread de chamada não força o término da tarefa. Ele apenas sinaliza que o cancelamento é solicitado. Se a tarefa já estiver em execução, cabe ao representante de usuário observar a solicitação e responder adequadamente. Se cancelamento for solicitado antes da execução da tarefa, o representante de usuário nunca será executado e o objeto de tarefa fará a transição para o estado Cancelado.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como terminar uma <xref:System.Threading.Tasks.Task> e suas tarefas filho em resposta a uma solicitação de cancelamento. Ele também mostra que quando um representante de usuário termina lançando um <xref:System.Threading.Tasks.TaskCanceledException>, o thread de chamada pode optar por usar o método <xref:System.Threading.Tasks.Task.Wait%2A> ou o método <xref:System.Threading.Tasks.Task.WaitAll%2A> para aguardar a conclusão das tarefas. Nesse caso, você deve usar um bloco `try/catch` para lidar com as exceções no thread de chamada.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 A classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> está totalmente integrada com o modelo de cancelamento que se baseia nos tipos <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> e <xref:System.Threading.CancellationToken?displayProperty=nameWithType>. Para saber mais, confira [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md) e [Cancelamento de tarefas](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Programação Assíncrona baseada em tarefas](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [Tarefas filho anexadas e desanexadas](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)
- [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
