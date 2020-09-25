---
title: DOTIPO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: b5600b4cee23945fe60142b370feb35ac1a2efa1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175675"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="f2dab-102">DOTIPO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f2dab-102">OFTYPE (Entity SQL)</span></span>

<span data-ttu-id="f2dab-103">Retorna uma coleção de objetos de uma expressão de consulta que é de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="f2dab-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2dab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2dab-104">Syntax</span></span>  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="f2dab-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f2dab-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="f2dab-106">Qualquer expressão de consulta válida que retorna uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="f2dab-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="f2dab-107">O tipo para testar cada objeto retornado por `expression` contra.</span><span class="sxs-lookup"><span data-stu-id="f2dab-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="f2dab-108">O tipo deve ser qualificado por um namespace.</span><span class="sxs-lookup"><span data-stu-id="f2dab-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2dab-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="f2dab-109">Return Value</span></span>  

 <span data-ttu-id="f2dab-110">Uma coleção de objetos que são do tipo `test_type`, ou um tipo base ou um tipo derivado de `test_type`.</span><span class="sxs-lookup"><span data-stu-id="f2dab-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="f2dab-111">Se for especificado SOMENTE, somente as instâncias de `test_type` ou de uma coleção vazia serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="f2dab-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2dab-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2dab-112">Remarks</span></span>  

 <span data-ttu-id="f2dab-113">Uma expressão de `OFTYPE` especifica uma expressão que é emitida para executar um teste de tipo versus cada elemento de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f2dab-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="f2dab-114">A expressão de `OFTYPE` gerencia uma nova coleção do tipo especificado que contém somente os elementos que foram qualquer equivalente a esse tipo ou um subpropriedades tipo deles.</span><span class="sxs-lookup"><span data-stu-id="f2dab-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="f2dab-115">Uma expressão de `OFTYPE` é uma abreviação de expressão de consulta a seguir:</span><span class="sxs-lookup"><span data-stu-id="f2dab-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="f2dab-116">Já que um gerente é um subtipo de funcionários, a seguinte expressão gerenciar uma coleção somente de gerentes de uma coleção de funcionários:</span><span class="sxs-lookup"><span data-stu-id="f2dab-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="f2dab-117">Também é possível gerar a conversão uma coleção usando o filtro de tipo:</span><span class="sxs-lookup"><span data-stu-id="f2dab-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="f2dab-118">Desde que os executivos são gerentes, a coleção resultante ainda contém todos os executivos originais, embora a coleção é digitada agora como uma coleção de gerentes.</span><span class="sxs-lookup"><span data-stu-id="f2dab-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="f2dab-119">A tabela a seguir mostra o comportamento do operador de `OFTYPE` sobre alguns padrões.</span><span class="sxs-lookup"><span data-stu-id="f2dab-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="f2dab-120">Todas as exceções são geradas do lado do cliente antes que o provedor foi chamado:</span><span class="sxs-lookup"><span data-stu-id="f2dab-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="f2dab-121">Padrão</span><span class="sxs-lookup"><span data-stu-id="f2dab-121">Pattern</span></span>|<span data-ttu-id="f2dab-122">Comportamento</span><span class="sxs-lookup"><span data-stu-id="f2dab-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="f2dab-123">OFTYPE (coleção (EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="f2dab-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="f2dab-124">Coleção (EntityType)</span><span class="sxs-lookup"><span data-stu-id="f2dab-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="f2dab-125">OFTYPE (coleção (ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="f2dab-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="f2dab-126">Gera</span><span class="sxs-lookup"><span data-stu-id="f2dab-126">Throws</span></span>|  
|<span data-ttu-id="f2dab-127">OFTYPE (coleção (RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="f2dab-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="f2dab-128">Gera</span><span class="sxs-lookup"><span data-stu-id="f2dab-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f2dab-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2dab-129">Example</span></span>  

 <span data-ttu-id="f2dab-130">A consulta a seguir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador OfType para retornar uma coleção de objetos OnsiteCourse de uma coleção de objetos Course.</span><span class="sxs-lookup"><span data-stu-id="f2dab-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="f2dab-131">A consulta é baseada no [modelo escolar](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f2dab-131">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="f2dab-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="f2dab-132">See also</span></span>

- [<span data-ttu-id="f2dab-133">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f2dab-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
