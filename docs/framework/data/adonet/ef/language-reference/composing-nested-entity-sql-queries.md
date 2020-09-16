---
title: Composta consultas aninhadas Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: b28c46ba9a89ffffe8cd95ad55eb502eb8ea48a6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541090"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="e4577-102">Composta consultas aninhadas Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e4577-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e4577-103">é uma linguagem funcional rico.</span><span class="sxs-lookup"><span data-stu-id="e4577-103">is a rich functional language.</span></span> <span data-ttu-id="e4577-104">O bloco de construção de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="e4577-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="e4577-105">Ao contrário do SQL convencional, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o não está limitado a um conjunto de resultados de tabela: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dá suporte à composição de expressões complexas que podem ter literais, parâmetros ou expressões aninhadas.</span><span class="sxs-lookup"><span data-stu-id="e4577-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="e4577-106">Um valor na expressão pode ser parametrizada ou composta de alguma outra expressão.</span><span class="sxs-lookup"><span data-stu-id="e4577-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="e4577-107">Expressões aninhadas</span><span class="sxs-lookup"><span data-stu-id="e4577-107">Nested Expressions</span></span>  
 <span data-ttu-id="e4577-108">Uma expressão aninhada pode ser colocadas em qualquer lugar um valor de tipo que retorna é aceito.</span><span class="sxs-lookup"><span data-stu-id="e4577-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="e4577-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e4577-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="e4577-110">Uma consulta aninhada pode ser colocadas em uma cláusula de projeção.</span><span class="sxs-lookup"><span data-stu-id="e4577-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="e4577-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e4577-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="e4577-112">Em [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultas aninhadas devem sempre ser colocado entre parênteses:</span><span class="sxs-lookup"><span data-stu-id="e4577-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="e4577-113">O exemplo a seguir demonstra como aninhar expressões corretamente em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] : [como ordenar a União de duas consultas](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e4577-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="e4577-114">Consultas aninhadas na projeção</span><span class="sxs-lookup"><span data-stu-id="e4577-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="e4577-115">Consultas aninhadas na cláusula de projeto podem obter convertido em consultas de produto cartesiano no servidor.</span><span class="sxs-lookup"><span data-stu-id="e4577-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="e4577-116">Em alguns servidores de back-end, incluindo SQL Server, isso pode fazer com que a tabela TempDB fique muito grande, o que pode afetar negativamente o desempenho do servidor.</span><span class="sxs-lookup"><span data-stu-id="e4577-116">In some backend servers, including SQL Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="e4577-117">O seguinte é um exemplo de tal consulta:</span><span class="sxs-lookup"><span data-stu-id="e4577-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="e4577-118">Ordenando consultas aninhadas</span><span class="sxs-lookup"><span data-stu-id="e4577-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="e4577-119">Em Entity Framework, uma expressão aninhada pode ser colocadas em qualquer lugar na consulta.</span><span class="sxs-lookup"><span data-stu-id="e4577-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="e4577-120">Porque Entity SQL permite grande flexibilidade em consultas de escrita, é possível escrever uma consulta que contém a ordem das consultas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="e4577-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="e4577-121">No entanto, a ordem de uma consulta aninhada não é preservada.</span><span class="sxs-lookup"><span data-stu-id="e4577-121">However, the order of a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4577-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="e4577-122">See also</span></span>

- [<span data-ttu-id="e4577-123">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e4577-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
