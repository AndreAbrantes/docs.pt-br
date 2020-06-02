---
title: 'Como: Desencapsular uma tarefa aninhada'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 9a69fa42da41ee4a071a6571042fd96fb5a009d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288024"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="4e3d2-102">Como: Desencapsular uma tarefa aninhada</span><span class="sxs-lookup"><span data-stu-id="4e3d2-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="4e3d2-103">Você pode retornar uma tarefa de um método e esperar ou continuar a tarefa, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4e3d2-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="4e3d2-104">No exemplo anterior, a propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> é do tipo `string` (`String` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4e3d2-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="4e3d2-105">No entanto, em alguns cenários, pode ser pertinente criar uma tarefa dentro de outra tarefa e, em seguida, retornar a tarefa aninhada.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="4e3d2-106">Nesse caso, o `TResult` da tarefa delimitadora é uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="4e3d2-107">No exemplo a seguir, a propriedade Result é um `Task<Task<string>>` em C# ou `Task(Of Task(Of String))` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="4e3d2-108">Embora seja possível gravar código para decodificar a tarefa externa e recuperar a tarefa original e sua propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>, esse código não é fácil escrever porque você deve lidar com exceções e solicitações de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="4e3d2-109">Nessa situação, é recomendável que você use um dos métodos de extensão <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>, conforme é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="4e3d2-110">Os métodos <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> podem ser usados para transformar qualquer `Task<Task>` ou `Task<Task<TResult>>` (`Task(Of Task)` ou `Task(Of Task(Of TResult))` no Visual Basic) em um `Task` ou `Task<TResult>` (`Task(Of TResult)` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4e3d2-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="4e3d2-111">A nova tarefa representa por completo a tarefa aninhada interna e inclui o estado de cancelamento e todas as exceções.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e3d2-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e3d2-112">Example</span></span>  
 <span data-ttu-id="4e3d2-113">O exemplo a seguir demonstra como usar os métodos de extensão <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="4e3d2-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="4e3d2-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="4e3d2-115">Programação assíncrona baseada em tarefas</span><span class="sxs-lookup"><span data-stu-id="4e3d2-115">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
