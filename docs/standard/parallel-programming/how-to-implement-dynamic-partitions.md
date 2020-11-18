---
title: 'Como: Implementar partições dinâmicas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 1120d846743ac3b89d2d110b4d1abdd0083f9eab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825735"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="28e82-102">Como: Implementar partições dinâmicas</span><span class="sxs-lookup"><span data-stu-id="28e82-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="28e82-103">O exemplo a seguir mostra como implementar um <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> personalizado que implementa o particionamento dinâmico e pode ser usado de determinadas sobrecargas <xref:System.Threading.Tasks.Parallel.ForEach%2A> e do PLINQ.</span><span class="sxs-lookup"><span data-stu-id="28e82-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28e82-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28e82-104">Example</span></span>

<span data-ttu-id="28e82-105">Cada vez que uma partição chama <xref:System.Collections.IEnumerator.MoveNext%2A> no enumerador, o enumerador fornece a partição com um elemento de lista.</span><span class="sxs-lookup"><span data-stu-id="28e82-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="28e82-106">No caso do PLINQ e do <xref:System.Threading.Tasks.Parallel.ForEach%2A>, a partição é uma instância de <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="28e82-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="28e82-107">Como as solicitações ocorrem simultaneamente em vários threads, o acesso ao índice atual é sincronizado.</span><span class="sxs-lookup"><span data-stu-id="28e82-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="28e82-108">Este é um exemplo de particionamento, com cada parte consistindo em um elemento.</span><span class="sxs-lookup"><span data-stu-id="28e82-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="28e82-109">Ao fornecer mais elementos de uma vez, você pode reduzir a contenção no bloqueio e, teoricamente, alcançar um desempenho mais rápido.</span><span class="sxs-lookup"><span data-stu-id="28e82-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="28e82-110">No entanto, em algum momento, partes maiores podem exigir lógica de balanceamento de carga adicional para manter todos os threads ocupados até que todo o trabalho seja concluído.</span><span class="sxs-lookup"><span data-stu-id="28e82-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e82-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="28e82-111">See also</span></span>

* [<span data-ttu-id="28e82-112">Particionadores personalizados para PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="28e82-112">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="28e82-113">Como: implementar um particionador para particionamento estático</span><span class="sxs-lookup"><span data-stu-id="28e82-113">How to: Implement a Partitioner for Static Partitioning</span></span>](how-to-implement-a-partitioner-for-static-partitioning.md)
