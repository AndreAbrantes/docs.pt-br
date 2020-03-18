---
title: Classificando dados (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 29a5e3e685bdc73536961b7783f4986796b46bdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167901"
---
# <a name="sorting-data-c"></a><span data-ttu-id="aa031-102">Classificando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="aa031-102">Sorting Data (C#)</span></span>
<span data-ttu-id="aa031-103">Uma operação de classificação ordena os elementos de uma sequência com base em um ou mais atributos.</span><span class="sxs-lookup"><span data-stu-id="aa031-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="aa031-104">O primeiro critério de classificação executa uma classificação primária dos elementos.</span><span class="sxs-lookup"><span data-stu-id="aa031-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="aa031-105">Especificando um segundo critério de classificação, você pode classificar os elementos dentro de cada grupo de classificação primário.</span><span class="sxs-lookup"><span data-stu-id="aa031-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="aa031-106">A ilustração a seguir mostra os resultados de uma operação de classificação alfabética em uma sequência de caracteres:</span><span class="sxs-lookup"><span data-stu-id="aa031-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Gráfico que mostra uma operação de classificação alfabética.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="aa031-108">Os métodos de operador de consulta padrão que classificam dados estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="aa031-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa031-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="aa031-109">Methods</span></span>  
  
|<span data-ttu-id="aa031-110">Nome do método</span><span class="sxs-lookup"><span data-stu-id="aa031-110">Method Name</span></span>|<span data-ttu-id="aa031-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa031-111">Description</span></span>|<span data-ttu-id="aa031-112">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="aa031-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="aa031-113">Mais informações</span><span class="sxs-lookup"><span data-stu-id="aa031-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="aa031-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="aa031-114">OrderBy</span></span>|<span data-ttu-id="aa031-115">Classifica valores em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="aa031-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="aa031-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="aa031-116">OrderByDescending</span></span>|<span data-ttu-id="aa031-117">Classifica valores em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="aa031-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="aa031-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="aa031-118">ThenBy</span></span>|<span data-ttu-id="aa031-119">Executa uma classificação secundária em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="aa031-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="aa031-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="aa031-120">ThenByDescending</span></span>|<span data-ttu-id="aa031-121">Executa uma classificação secundária em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="aa031-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="aa031-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="aa031-122">Reverse</span></span>|<span data-ttu-id="aa031-123">Inverte a ordem dos elementos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="aa031-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="aa031-124">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="aa031-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="aa031-125">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="aa031-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="aa031-126">Exemplos de classificação primária</span><span class="sxs-lookup"><span data-stu-id="aa031-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="aa031-127">Classificação crescente primária</span><span class="sxs-lookup"><span data-stu-id="aa031-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="aa031-128">O exemplo a seguir demonstra como usar a cláusula `orderby` em uma consulta de LINQ para classificar as cadeias de caracteres em uma matriz segundo o tamanho da cadeia de caracteres, em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="aa031-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="aa031-129">Classificação decrescente primária</span><span class="sxs-lookup"><span data-stu-id="aa031-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="aa031-130">O exemplo seguinte demonstra como usar a cláusula `orderby descending` em uma consulta de LINQ para classificar as cadeias de caracteres segundo sua primeira letra, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="aa031-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="aa031-131">Exemplos de classificação secundária</span><span class="sxs-lookup"><span data-stu-id="aa031-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="aa031-132">Classificação crescente secundária</span><span class="sxs-lookup"><span data-stu-id="aa031-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="aa031-133">O exemplo a seguir demonstra como usar a cláusula `orderby` em uma consulta de LINQ para executar uma classificação primária e uma classificação secundária das cadeias de caracteres em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="aa031-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="aa031-134">As cadeias de caracteres são classificadas primeiro segundo o tamanho e, depois, segundo a primeira letra da cadeia de caracteres, em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="aa031-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="aa031-135">Classificação decrescente secundária</span><span class="sxs-lookup"><span data-stu-id="aa031-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="aa031-136">O exemplo seguinte demonstra como usar a cláusula `orderby descending` em uma consulta de LINQ para executar uma classificação primária, em ordem crescente e uma classificação secundária, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="aa031-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="aa031-137">As cadeias de caracteres são classificadas primeiro segundo o tamanho e, depois, segundo a primeira letra da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="aa031-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa031-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa031-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="aa031-139">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="aa031-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="aa031-140">Cláusula orderby</span><span class="sxs-lookup"><span data-stu-id="aa031-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="aa031-141">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="aa031-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="aa031-142">Como classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="aa031-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
