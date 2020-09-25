---
title: Paginação (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 42f685e0b84109f3099b501b2a75e681af1ea1bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177469"
---
# <a name="paging-entity-sql"></a><span data-ttu-id="74e6e-102">Paginação (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="74e6e-102">Paging (Entity SQL)</span></span>

<span data-ttu-id="74e6e-103">A paginação física pode ser executada usando as subcláusulas [Skip](skip-entity-sql.md) e [Limit](limit-entity-sql.md) na cláusula [order by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="74e6e-103">Physical paging can be performed by using the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="74e6e-104">Para executar a físico paginação deterministically, você deve usar a SKIP e o LIMIT.</span><span class="sxs-lookup"><span data-stu-id="74e6e-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="74e6e-105">Se você quiser restringir o número de linhas no resultado de uma forma não determinística, deverá usar [Top](top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="74e6e-105">If you only want to restrict the number of rows in the result in a non-deterministic way, you should use [TOP](top-entity-sql.md).</span></span> <span data-ttu-id="74e6e-106">A TOP e SKIP/LIMIT são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="74e6e-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="74e6e-107">Visão geral TOP</span><span class="sxs-lookup"><span data-stu-id="74e6e-107">TOP Overview</span></span>  

 <span data-ttu-id="74e6e-108">A cláusula SELECT pode ter uma cláusula as subjanelas TOP opcional após o modificador opcional de ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="74e6e-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="74e6e-109">A cláusula subpropriedades TOP especifica que apenas definir primeiro as linhas será retornado do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="74e6e-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="74e6e-110">Para obter mais informações, consulte [superior](top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="74e6e-110">For more information, see [TOP](top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="74e6e-111">Visão geral de SKIP e de LIMIT</span><span class="sxs-lookup"><span data-stu-id="74e6e-111">SKIP And LIMIT Overview</span></span>  

 <span data-ttu-id="74e6e-112">A SKIP e o LIMIT são parte da cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="74e6e-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="74e6e-113">Se uma subpropriedades cláusula de expressão de SKIP está presente em uma cláusula ORDER BY, os resultados serão classificados de acordo com a especificação do tipo e o conjunto de resultados incluirá as fileiras a partir da linha seguinte logo após a expressão de SKIP.</span><span class="sxs-lookup"><span data-stu-id="74e6e-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="74e6e-114">Por exemplo, a SKIP 5 ignorará as primeiras cinco linhas e retornará a sexta linha avançar.</span><span class="sxs-lookup"><span data-stu-id="74e6e-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="74e6e-115">Se uma subcláusula de expressão LIMIT estiver presente em uma cláusula ORDER BY, a consulta será classificada de acordo com a especificação de classificação e o número de linhas resultante será restrito pela expressão LIMIT.</span><span class="sxs-lookup"><span data-stu-id="74e6e-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="74e6e-116">Por exemplo, o LIMIT 5 restringirá o conjunto de resultados a instâncias ou cinco linhas.</span><span class="sxs-lookup"><span data-stu-id="74e6e-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="74e6e-117">A SKIP e o LIMIT não têm que ser usados juntos; você pode usar apenas a SKIP ou apenas o LIMIT com cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="74e6e-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="74e6e-118">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="74e6e-118">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="74e6e-119">SKIP</span><span class="sxs-lookup"><span data-stu-id="74e6e-119">SKIP</span></span>](skip-entity-sql.md)  
  
- [<span data-ttu-id="74e6e-120">LIMITE</span><span class="sxs-lookup"><span data-stu-id="74e6e-120">LIMIT</span></span>](limit-entity-sql.md)  
  
- [<span data-ttu-id="74e6e-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="74e6e-121">ORDER BY</span></span>](order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="74e6e-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="74e6e-122">See also</span></span>

- [<span data-ttu-id="74e6e-123">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74e6e-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="74e6e-124">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74e6e-124">Entity SQL Overview</span></span>](entity-sql-overview.md)
- <span data-ttu-id="74e6e-125">[Como: paginar os resultados da consulta](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="74e6e-125">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
