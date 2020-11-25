---
title: 'Como: Retornar um valor de uma tarefa'
description: Consulte como usar o tipo System. Threading. Tasks. Task <TResult> para retornar um valor da propriedade Result no .net.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 60ab4a92fed4838934a2d544bea844a5810d4f5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701179"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="670da-103">Como: Retornar um valor de uma tarefa</span><span class="sxs-lookup"><span data-stu-id="670da-103">How to: Return a Value from a Task</span></span>

<span data-ttu-id="670da-104">Este exemplo mostra como usar o tipo <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para retornar um valor da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="670da-104">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="670da-105">Isso requer que o diretório C:\Usuários\Público\Imagens\Imagens de Exemplo\ exista e contenha arquivos.</span><span class="sxs-lookup"><span data-stu-id="670da-105">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="670da-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="670da-106">Example</span></span>  

 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="670da-107">A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> bloqueia o thread de chamada até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="670da-107">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="670da-108">Para ver como passar o resultado de um <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> para uma tarefa de continuação, confira [Encadeamento de tarefas usando tarefas de continuação](chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="670da-108">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="670da-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="670da-109">See also</span></span>

- [<span data-ttu-id="670da-110">Programação assíncrona baseada em tarefas</span><span class="sxs-lookup"><span data-stu-id="670da-110">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="670da-111">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="670da-111">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
