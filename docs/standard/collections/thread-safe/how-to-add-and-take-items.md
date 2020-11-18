---
title: 'Como: Adicionar e remover itens individualmente de uma BlockingCollection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: 5501e108d1866fc1ae6fc66f9fe665b63373414b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818629"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="4c116-102">Como: Adicionar e remover itens individualmente de uma BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="4c116-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="4c116-103">Este exemplo mostra como adicionar e remover itens de um <xref:System.Collections.Concurrent.BlockingCollection%601> tanto com bloqueio quanto sem bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4c116-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="4c116-104">Para obter mais informações sobre <xref:System.Collections.Concurrent.BlockingCollection%601>, veja [Visão geral de BlockingCollection](blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4c116-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="4c116-105">Para obter um exemplo de como enumerar um <xref:System.Collections.Concurrent.BlockingCollection%601> até que ele esteja vazio e nenhum elemento adicional seja adicionado, consulte [como: usar ForEach para remover itens de um BlockingCollection](how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="4c116-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="4c116-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c116-106">Example</span></span>  
 <span data-ttu-id="4c116-107">Este primeiro exemplo mostra como adicionar e remover itens para que as operações sejam bloqueadas se a coleção fica temporariamente vazia (ao remover) ou com a capacidade máxima (ao adicionar) ou se um período de tempo limite especificado é decorrido.</span><span class="sxs-lookup"><span data-stu-id="4c116-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="4c116-108">Observe que o bloqueio de capacidade máxima é habilitado apenas quando a BlockingCollection é criada com uma capacidade máxima especificada no construtor.</span><span class="sxs-lookup"><span data-stu-id="4c116-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="4c116-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c116-109">Example</span></span>  
 <span data-ttu-id="4c116-110">Este segundo exemplo mostra como adicionar e tirar itens para que as operações não sejam bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="4c116-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="4c116-111">Se nenhum item estiver presente, a capacidade máxima em uma coleção associada tiver sido atingida ou o tempo limite tiver expirado, a operação <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ou <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> retornará false.</span><span class="sxs-lookup"><span data-stu-id="4c116-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="4c116-112">Isso permite que o thread faça algum trabalho útil por um tempo e então, mais tarde, tente novamente recuperar um item novo ou tente adicionar o mesmo item que não pôde ser adicionado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4c116-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="4c116-113">O programa também demonstra como implementar o cancelamento ao acessar um <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="4c116-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="4c116-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="4c116-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="4c116-115">Visão geral de BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="4c116-115">BlockingCollection Overview</span></span>](blockingcollection-overview.md)
