---
title: Retornar a união de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 13e5e821f68e839039569b4ac8a993a20c45ab27
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403941"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="3c498-102">Retornar a união de sequências de duas</span><span class="sxs-lookup"><span data-stu-id="3c498-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="3c498-103">Use o operador de <xref:System.Linq.Queryable.Union%2A> para retornar a união ajustada de duas sequências.</span><span class="sxs-lookup"><span data-stu-id="3c498-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c498-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c498-104">Example</span></span>  
 <span data-ttu-id="3c498-105">Este exemplo usa <xref:System.Linq.Queryable.Union%2A> para retornar uma sequência de todos os países em que há `Customers` ou `Employees`.</span><span class="sxs-lookup"><span data-stu-id="3c498-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="3c498-106">Na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], o <xref:System.Linq.Queryable.Union%2A> operador está definido para multisets como concatenação não ordenada de multisets (efetivamente o resultado das [ `UNION ALL` ](https://docs.microsoft.com/en-us/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) cláusula no SQL).</span><span class="sxs-lookup"><span data-stu-id="3c498-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](https://docs.microsoft.com/en-us/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause in SQL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c498-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c498-107">See Also</span></span>  
 [<span data-ttu-id="3c498-108">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="3c498-108">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="3c498-109">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="3c498-109">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
