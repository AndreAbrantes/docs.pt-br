---
title: 'Como: Especificar opções de mesclagem em PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 91c5ac91538942368b66399bf0bc0132a15bf667
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825592"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="2b7f2-102">Como: Especificar opções de mesclagem em PLINQ</span><span class="sxs-lookup"><span data-stu-id="2b7f2-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="2b7f2-103">Este exemplo mostra como especificar as opções de mesclagem que se aplicarão a todos os operadores subsequentes em uma consulta PLINQ.</span><span class="sxs-lookup"><span data-stu-id="2b7f2-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="2b7f2-104">Você não precisa definir as opções de mesclagem explicitamente, mas fazer isso pode melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="2b7f2-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="2b7f2-105">Para saber mais sobre opções de mesclagem, veja [Opções de mesclagem no PLINQ](merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="2b7f2-105">For more information about merge options, see [Merge Options in PLINQ](merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2b7f2-106">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="2b7f2-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="2b7f2-107">Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="2b7f2-107">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b7f2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b7f2-108">Example</span></span>  
 <span data-ttu-id="2b7f2-109">O exemplo a seguir demonstra o comportamento das opções de mesclagem em um cenário básico que tem uma fonte não ordenada e aplica uma função cara para todo elemento.</span><span class="sxs-lookup"><span data-stu-id="2b7f2-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="2b7f2-110">Em casos onde a opção <xref:System.Linq.ParallelMergeOptions.AutoBuffered> resulta em uma latência indesejável antes da produção do primeiro elemento, tente a opção <xref:System.Linq.ParallelMergeOptions.NotBuffered> para produz elementos de resultado mais rápido e mais fácil.</span><span class="sxs-lookup"><span data-stu-id="2b7f2-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7f2-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="2b7f2-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="2b7f2-112">LINQ paralelo (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2b7f2-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
