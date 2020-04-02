---
title: como avaliar o desempenho de consulta PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 4cb0d408798d66c8491654c90f33255c700690a3
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587790"
---
# <a name="how-to-measure-plinq-query-performance"></a>como avaliar o desempenho de consulta PLINQ
Este exemplo mostra como usar a classe <xref:System.Diagnostics.Stopwatch> para medir o tempo de execução necessário de uma consulta PLINQ.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa um loop `foreach` vazio (`For Each` no Visual Basic) para medir o tempo necessário de execução da consulta. No código da vida real, o loop normalmente contém etapas de processamento adicionais que se juntam ao tempo de execução total de consultas. O cronômetro só é iniciado um pouco antes do loop, pois é quando começa a execução da consulta. Se você precisar de uma medição mais refinada, use a propriedade `ElapsedTicks` em vez de `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 O tempo total de execução é uma métrica útil quando você estiver experimentando com implantações de consulta, mas nem sempre ele aborda tudo. Para uma visão mais profunda e mais rica da interação dos threads de consulta entre si e com outros processos em execução, use a Visualização Simultânea. Para saber mais, confira [Visualização Simultânea](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Confira também

- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
