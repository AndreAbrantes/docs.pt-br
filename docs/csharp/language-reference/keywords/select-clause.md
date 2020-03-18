---
title: Cláusula select – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 68ea7ad6fc7cf5580dbdd0ae7f012f36566db0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173504"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="ec31f-102">Cláusula select (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ec31f-102">select clause (C# Reference)</span></span>

<span data-ttu-id="ec31f-103">Em uma expressão de consulta, a cláusula `select` especifica o tipo de valores que serão produzidos quando a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="ec31f-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="ec31f-104">O resultado é baseado na avaliação de todas as cláusulas anteriores e em quaisquer expressões na cláusula `select` em si.</span><span class="sxs-lookup"><span data-stu-id="ec31f-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="ec31f-105">Uma expressão de consulta deve terminar com uma cláusula `select` ou uma cláusula [group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ec31f-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="ec31f-106">O exemplo a seguir mostra uma cláusula `select` simples em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="ec31f-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="ec31f-107">O tipo da sequência produzida pela cláusula `select` determina o tipo da variável de consulta `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="ec31f-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="ec31f-108">No caso mais simples, a cláusula `select` apenas especifica a variável de intervalo.</span><span class="sxs-lookup"><span data-stu-id="ec31f-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="ec31f-109">Isso faz com que a sequência retornada contenha elementos do mesmo tipo que a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="ec31f-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="ec31f-110">Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ec31f-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="ec31f-111">No entanto, a cláusula `select` também fornece um mecanismo poderoso para transformar (ou *projetar*) dados de origem em novos tipos.</span><span class="sxs-lookup"><span data-stu-id="ec31f-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="ec31f-112">Para obter mais informações, consulte [Transformações de dados com LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="ec31f-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="ec31f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec31f-113">Example</span></span>

<span data-ttu-id="ec31f-114">O exemplo a seguir mostra todas as diferentes formas que uma cláusula `select` pode tomar.</span><span class="sxs-lookup"><span data-stu-id="ec31f-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="ec31f-115">Em cada consulta, observe a `select` relação entre a cláusula e`studentQuery1` `studentQuery2`o tipo da *variável consulta* ( , e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="ec31f-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="ec31f-116">Conforme mostrado em `studentQuery8` no exemplo anterior, às vezes, convém que os elementos da sequência retornada contenham apenas um subconjunto das propriedades dos elementos de origem.</span><span class="sxs-lookup"><span data-stu-id="ec31f-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="ec31f-117">Mantendo a sequência retornada a menor possível, é possível reduzir os requisitos de memória e aumentar a velocidade da execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="ec31f-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="ec31f-118">É possível fazer isso criando um tipo anônimo na cláusula `select` e usando um inicializador de objeto para inicializá-lo com as propriedades adequadas do elemento de origem.</span><span class="sxs-lookup"><span data-stu-id="ec31f-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="ec31f-119">Para obter um exemplo de como fazer isso, consulte [Inicializadores de objeto e coleção](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="ec31f-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="ec31f-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec31f-120">Remarks</span></span>

<span data-ttu-id="ec31f-121">No tempo de compilação, a cláusula `select` é convertida em uma chamada de método para o operador de consulta padrão <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec31f-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec31f-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec31f-122">See also</span></span>

- [<span data-ttu-id="ec31f-123">C# Referência</span><span class="sxs-lookup"><span data-stu-id="ec31f-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ec31f-124">Palavras-chave de consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ec31f-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="ec31f-125">de cláusula</span><span class="sxs-lookup"><span data-stu-id="ec31f-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="ec31f-126">partial (método) (Referência do C#)</span><span class="sxs-lookup"><span data-stu-id="ec31f-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="ec31f-127">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="ec31f-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="ec31f-128">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="ec31f-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="ec31f-129">Consulta Integrada ao Idioma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ec31f-129">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
