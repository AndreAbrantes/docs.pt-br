---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150487"
---
# <a name="between-entity-sql"></a><span data-ttu-id="29761-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="29761-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="29761-103">Determina se uma expressão resulta em um valor em um intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="29761-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="29761-104">A [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão BETWEEN tem a mesma funcionalidade da expressão Transact-SQL BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="29761-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29761-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29761-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="29761-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="29761-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="29761-107">Qualquer expressão válida para testar no intervalo definido por `begin_expression` e por `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="29761-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="29761-108">`expression` deve ser do mesmo tipo de `begin_expression` e `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="29761-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="29761-109">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="29761-109">Any valid expression.</span></span> <span data-ttu-id="29761-110">`begin_expression` deve ser do mesmo tipo de `expression` e `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="29761-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="29761-111">`begin_expression` deve ser menor que `end_expression`, o valor de retorno será negado mais.</span><span class="sxs-lookup"><span data-stu-id="29761-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="29761-112">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="29761-112">Any valid expression.</span></span> <span data-ttu-id="29761-113">`end_expression` deve ser do mesmo tipo de `expression` e `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="29761-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="29761-114">NOT</span><span class="sxs-lookup"><span data-stu-id="29761-114">NOT</span></span>  
 <span data-ttu-id="29761-115">Especifica que o resultado de ENTER é negado.</span><span class="sxs-lookup"><span data-stu-id="29761-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="29761-116">AND</span><span class="sxs-lookup"><span data-stu-id="29761-116">AND</span></span>  
 <span data-ttu-id="29761-117">Atua como um espaço reservado que indica que `expression` deve estar dentro do intervalo indicado por `begin_expression` e por `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="29761-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29761-118">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="29761-118">Return Value</span></span>  
 <span data-ttu-id="29761-119">`true` se `expression` está entre o intervalo indicado por `begin_expression` e `end_expression`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="29761-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="29761-120">`null` será retornado se `expression` é `null` ou se `begin_expression` ou `end_expression` são `null`.</span><span class="sxs-lookup"><span data-stu-id="29761-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29761-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="29761-121">Remarks</span></span>  
 <span data-ttu-id="29761-122">Para especificar um intervalo exclusivo, use os operadores maiores (>) e menores do que (<) em vez de BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="29761-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29761-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29761-123">Example</span></span>  
 <span data-ttu-id="29761-124">Os seguintes usos da consulta SQL Entity ENTER o operador determinar se uma expressão resulta em um valor em um intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="29761-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="29761-125">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="29761-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="29761-126">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="29761-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="29761-127">Siga o procedimento em [Como: Executar uma consulta que retorna resultados do tipo estrutural](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="29761-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="29761-128">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="29761-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="29761-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="29761-129">See also</span></span>

- [<span data-ttu-id="29761-130">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="29761-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
