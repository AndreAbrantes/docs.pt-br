---
title: como avaliar o desempenho de consulta PLINQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03432e70454cb6203e55e340111a6cb7efe62dc4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="a5c58-102">como avaliar o desempenho de consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="a5c58-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="a5c58-103">Este exemplo mostra como usar o <xref:System.Diagnostics.Stopwatch> classe para medir o tempo necessário para uma consulta PLINQ executar.</span><span class="sxs-lookup"><span data-stu-id="a5c58-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c58-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5c58-104">Example</span></span>  
 <span data-ttu-id="a5c58-105">Este exemplo usa um vazio `foreach` loop (`For Each` no Visual Basic) para medir o tempo necessário para executar a consulta.</span><span class="sxs-lookup"><span data-stu-id="a5c58-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="a5c58-106">No código do mundo real, o loop normalmente contém etapas de processamento adicionais que adicionar o tempo de execução total de consultas.</span><span class="sxs-lookup"><span data-stu-id="a5c58-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="a5c58-107">Observe que o cronômetro não é iniciado até que antes do loop, pois esse é começa a execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="a5c58-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="a5c58-108">Se você precisar de mais de medição refinada, você pode usar o `ElapsedTicks` propriedade em vez de `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="a5c58-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="a5c58-109">Tempo total de execução é uma métrica útil quando você estiver experimentando com implementações de consulta, mas ele não aborda toda a história sempre.</span><span class="sxs-lookup"><span data-stu-id="a5c58-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="a5c58-110">Para obter uma visão mais profunda e mais rica da interação entre os threads de consulta entre si e com outros processos em execução, use o Visualizador de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="a5c58-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="a5c58-111">Para obter mais informações, consulte [Visualizador de simultaneidade](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="a5c58-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c58-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5c58-112">See Also</span></span>  
 [<span data-ttu-id="a5c58-113">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="a5c58-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
