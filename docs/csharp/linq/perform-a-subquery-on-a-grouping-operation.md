---
title: Executar uma subconsulta em uma operação de agrupamento (LINQ em C#)
description: Como executar uma subconsulta em uma operação de agrupamento usando LINQ em C#.
ms.date: 12/01/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: fd26f87ad7d5b4892f086bf8c7a34cf19a7f9e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173361"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="84b11-103">Executar uma subconsulta em uma operação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="84b11-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="84b11-104">Este artigo mostra duas maneiras diferentes de criar uma consulta que ordena os dados de origem em grupos e, em seguida, realiza uma subconsulta em cada grupo individualmente.</span><span class="sxs-lookup"><span data-stu-id="84b11-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="84b11-105">A técnica básica em cada exemplo é agrupar os elementos de origem usando uma *continuação* chamada `newGroup` e, em seguida, gerar uma nova subconsulta de `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="84b11-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="84b11-106">Essa subconsulta é executada em cada novo grupo criado pela consulta externa.</span><span class="sxs-lookup"><span data-stu-id="84b11-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="84b11-107">Observe que, nesse exemplo específico, a saída final não é um grupo, mas uma sequência simples de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="84b11-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="84b11-108">Para obter mais informações sobre como agrupar, consulte [Cláusula group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="84b11-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="84b11-109">Para obter mais informações sobre continuações, consulte [into](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="84b11-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="84b11-110">O exemplo a seguir usa uma estrutura de dados na memória como a fonte de dados, mas os mesmos princípios se aplicam a qualquer tipo de fonte de dados do LINQ.</span><span class="sxs-lookup"><span data-stu-id="84b11-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84b11-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84b11-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="84b11-112">Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="84b11-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]

<span data-ttu-id="84b11-113">A consulta no snippet acima também pode ser escrita usando a sintaxe de método.</span><span class="sxs-lookup"><span data-stu-id="84b11-113">The query in the snippet above can also be written using method syntax.</span></span> <span data-ttu-id="84b11-114">O snippet de código a seguir tem uma consulta semanticamente equivalente escrita usando a sintaxe de método.</span><span class="sxs-lookup"><span data-stu-id="84b11-114">The following code snippet has a semantically equivalent query written using method syntax.</span></span>

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a><span data-ttu-id="84b11-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="84b11-115">See also</span></span>

- [<span data-ttu-id="84b11-116">Consulta Integrada ao Idioma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="84b11-116">Language Integrated Query (LINQ)</span></span>](index.md)
