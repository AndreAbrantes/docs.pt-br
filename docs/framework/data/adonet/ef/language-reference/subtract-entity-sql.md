---
title: "- (Subtração) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 20b9fd7dda34d3f6f19551d8f7e313196e0acc12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="acb27-102">- (Subtração) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="acb27-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="acb27-103">Subtrai dois números.</span><span class="sxs-lookup"><span data-stu-id="acb27-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb27-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="acb27-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="acb27-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="acb27-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="acb27-106">Qualquer expressão válida de qualquer dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="acb27-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="acb27-107">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="acb27-107">Result Types</span></span>  
 <span data-ttu-id="acb27-108">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="acb27-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="acb27-109">Para obter mais informações sobre a promoção de tipo implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="acb27-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="acb27-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="acb27-110">Example</span></span>  
 <span data-ttu-id="acb27-111">A seguinte consulta SQL Entity usa o operador - aritmético para subtrair dois números.</span><span class="sxs-lookup"><span data-stu-id="acb27-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="acb27-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="acb27-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="acb27-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="acb27-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="acb27-114">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="acb27-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="acb27-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="acb27-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="acb27-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acb27-116">See Also</span></span>  
 [<span data-ttu-id="acb27-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="acb27-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
