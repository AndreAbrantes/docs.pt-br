---
description: Cláusula where – Referência de C#
title: Cláusula where – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 58a8dc226bb2720b6a8251f028712a80f74e893c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89141680"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="64c7c-103">Cláusula where (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="64c7c-103">where clause (C# Reference)</span></span>

<span data-ttu-id="64c7c-104">A cláusula `where` é usada em uma expressão de consulta para especificar quais elementos da fonte de dados serão retornados na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="64c7c-104">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="64c7c-105">Aplica-se uma condição booliana (*predicate*) para cada elemento de origem (referenciado pela variável de intervalo) e retorna aqueles para os quais a condição especificada for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="64c7c-105">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="64c7c-106">Uma única expressão de consulta pode conter várias cláusulas `where` e uma única cláusula pode conter várias subexpressões de predicado.</span><span class="sxs-lookup"><span data-stu-id="64c7c-106">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="64c7c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64c7c-107">Example</span></span>

<span data-ttu-id="64c7c-108">No exemplo a seguir, a cláusula `where` filtra todos os números, exceto aqueles que são menores que cinco.</span><span class="sxs-lookup"><span data-stu-id="64c7c-108">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="64c7c-109">Se você remover a cláusula `where`, todos os números da fonte de dados serão retornados.</span><span class="sxs-lookup"><span data-stu-id="64c7c-109">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="64c7c-110">A expressão `num < 5` é o predicado aplicado a cada elemento.</span><span class="sxs-lookup"><span data-stu-id="64c7c-110">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="64c7c-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64c7c-111">Example</span></span>

<span data-ttu-id="64c7c-112">Em uma única `where` cláusula, você pode especificar quantos predicados forem necessários usando os [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) operadores e [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="64c7c-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="64c7c-113">No exemplo a seguir, a consulta especifica dois predicados para selecionar apenas os números pares que são menores que cinco.</span><span class="sxs-lookup"><span data-stu-id="64c7c-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="64c7c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64c7c-114">Example</span></span>

<span data-ttu-id="64c7c-115">Uma cláusula `where` pode conter um ou mais métodos que retornam valores boolianos.</span><span class="sxs-lookup"><span data-stu-id="64c7c-115">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="64c7c-116">No exemplo a seguir, a cláusula `where` usa um método para determinar se o valor atual da variável de intervalo é par ou ímpar.</span><span class="sxs-lookup"><span data-stu-id="64c7c-116">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="64c7c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="64c7c-117">Remarks</span></span>

<span data-ttu-id="64c7c-118">A cláusula `where` é um mecanismo de filtragem.</span><span class="sxs-lookup"><span data-stu-id="64c7c-118">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="64c7c-119">Ela pode ser posicionada em quase qualquer lugar em uma expressão de consulta, exceto que ela não pode ser a primeira ou a última cláusula.</span><span class="sxs-lookup"><span data-stu-id="64c7c-119">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="64c7c-120">A cláusula `where` pode aparecer antes ou depois de uma cláusula [group](group-clause.md) dependendo se você tiver que filtrar os elementos de origem antes ou depois de eles serem agrupados.</span><span class="sxs-lookup"><span data-stu-id="64c7c-120">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="64c7c-121">Se um predicado especificado não for válido para os elementos na fonte de dados, o resultado será um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="64c7c-121">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="64c7c-122">Esse é um dos benefícios da verificação de tipo forte fornecida pelo LINQ.</span><span class="sxs-lookup"><span data-stu-id="64c7c-122">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="64c7c-123">Em tempo de compilação, a palavra-chave `where` é convertida em uma chamada para o método de operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="64c7c-123">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="64c7c-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="64c7c-124">See also</span></span>

- [<span data-ttu-id="64c7c-125">Palavras-chave de consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="64c7c-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="64c7c-126">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="64c7c-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="64c7c-127">cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="64c7c-127">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="64c7c-128">Filtrar dados</span><span class="sxs-lookup"><span data-stu-id="64c7c-128">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="64c7c-129">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="64c7c-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="64c7c-130">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="64c7c-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
