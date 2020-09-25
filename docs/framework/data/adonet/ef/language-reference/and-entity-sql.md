---
title: '&amp;&amp; E (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 86ff43f8ed20c5696d15e21284394c3cb63200e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198035"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="3cabf-102">&amp;&amp; E (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3cabf-102">&amp;&amp; (AND) (Entity SQL)</span></span>

<span data-ttu-id="3cabf-103">Retorna `true` se as duas expressões são `true`; caso contrário, `false` ou `NULL`.</span><span class="sxs-lookup"><span data-stu-id="3cabf-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cabf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3cabf-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="3cabf-105">ou</span><span class="sxs-lookup"><span data-stu-id="3cabf-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3cabf-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3cabf-106">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="3cabf-107">Qualquer expressão válida que retorna um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="3cabf-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cabf-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3cabf-108">Remarks</span></span>  

 <span data-ttu-id="3cabf-109">O e comercial duplo (&&) têm a mesma funcionalidade que o operador AND.</span><span class="sxs-lookup"><span data-stu-id="3cabf-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="3cabf-110">A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.</span><span class="sxs-lookup"><span data-stu-id="3cabf-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="3cabf-111">TRUE</span><span class="sxs-lookup"><span data-stu-id="3cabf-111">TRUE</span></span>|<span data-ttu-id="3cabf-112">FALSE</span><span class="sxs-lookup"><span data-stu-id="3cabf-112">FALSE</span></span>|<span data-ttu-id="3cabf-113">NULO</span><span class="sxs-lookup"><span data-stu-id="3cabf-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="3cabf-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="3cabf-114">FALSE</span></span>|<span data-ttu-id="3cabf-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="3cabf-115">FALSE</span></span>|<span data-ttu-id="3cabf-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="3cabf-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="3cabf-117">NULO</span><span class="sxs-lookup"><span data-stu-id="3cabf-117">NULL</span></span>|<span data-ttu-id="3cabf-118">FALSE</span><span class="sxs-lookup"><span data-stu-id="3cabf-118">FALSE</span></span>|<span data-ttu-id="3cabf-119">NULO</span><span class="sxs-lookup"><span data-stu-id="3cabf-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3cabf-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3cabf-120">Example</span></span>  

 <span data-ttu-id="3cabf-121">A seguinte consulta SQL Entity demonstra como usar o operador AND.</span><span class="sxs-lookup"><span data-stu-id="3cabf-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="3cabf-122">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3cabf-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3cabf-123">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="3cabf-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3cabf-124">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3cabf-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3cabf-125">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="3cabf-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="3cabf-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="3cabf-126">See also</span></span>

- [<span data-ttu-id="3cabf-127">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3cabf-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
