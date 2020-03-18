---
title: Executar junções agrupadas (LINQ em C#)
description: Saiba como executar junções agrupadas usando o LINQ em C#.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61689132"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="b5008-103">Executar junções agrupadas</span><span class="sxs-lookup"><span data-stu-id="b5008-103">Perform grouped joins</span></span>

<span data-ttu-id="b5008-104">A junção de grupo é útil para a produção de estruturas de dados hierárquicos.</span><span class="sxs-lookup"><span data-stu-id="b5008-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="b5008-105">Ela combina cada elemento da primeira coleção com um conjunto de elementos correlacionados da segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="b5008-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="b5008-106">Por exemplo, uma classe ou uma tabela de banco de dados relacional chamada `Student` pode conter dois campos: `Id` e `Name`.</span><span class="sxs-lookup"><span data-stu-id="b5008-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="b5008-107">Uma segunda classe ou tabela de banco de dados relacional chamada `Course` pode conter dois campos: `StudentId` e `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="b5008-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="b5008-108">Uma junção de grupo dessas duas fontes de dados, com base na correspondência de `Student.Id` e `Course.StudentId`, agruparia cada `Student` com uma coleção de objetos `Course` (que pode estar vazia).</span><span class="sxs-lookup"><span data-stu-id="b5008-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="b5008-109">Cada elemento da primeira coleção aparece no conjunto de resultados de uma junção de grupo, independentemente de se os elementos correlacionados encontram-se na segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="b5008-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="b5008-110">Caso nenhum elemento correlacionado seja encontrado, a sequência de elementos correlacionados desse elemento ficará vazia.</span><span class="sxs-lookup"><span data-stu-id="b5008-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="b5008-111">O seletor de resultado, portanto, tem acesso a todos os elementos da primeira coleção.</span><span class="sxs-lookup"><span data-stu-id="b5008-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="b5008-112">Isso difere do seletor de resultado de uma junção que não é de grupo, que não pode acessar os elementos da primeira coleção que não têm correspondência na segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="b5008-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="b5008-113">O primeiro exemplo neste artigo mostra como executar uma junção de grupo.</span><span class="sxs-lookup"><span data-stu-id="b5008-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="b5008-114">O segundo exemplo mostra como usar uma junção de grupo para criar elementos XML.</span><span class="sxs-lookup"><span data-stu-id="b5008-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="b5008-115">Exemplo – junção de grupo</span><span class="sxs-lookup"><span data-stu-id="b5008-115">Example - Group join</span></span>

<span data-ttu-id="b5008-116">O exemplo a seguir realiza uma junção de grupo de objetos do tipo `Person` e `Pet` com base em `Person` correspondente à propriedade `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="b5008-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="b5008-117">Ao contrário de uma junção que não é de grupo, que produziria um par de elementos para cada correspondência, a junção de grupo produz apenas um objeto resultante para cada elemento da primeira coleção, que neste exemplo é um objeto `Person`.</span><span class="sxs-lookup"><span data-stu-id="b5008-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="b5008-118">Os elementos correspondentes da segunda coleção, que neste exemplo são objetos `Pet`, são agrupados em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="b5008-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="b5008-119">Por fim, a função de seletor de resultado cria um tipo anônimo para cada correspondência que consiste em `Person.FirstName` e em uma coleção de objetos `Pet`.</span><span class="sxs-lookup"><span data-stu-id="b5008-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="b5008-120">Exemplo – junção de grupo para criar XML</span><span class="sxs-lookup"><span data-stu-id="b5008-120">Example - Group join to create XML</span></span>

<span data-ttu-id="b5008-121">As junções de grupo são ideais para a criação de XML usando o LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="b5008-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="b5008-122">O exemplo a seguir é semelhante ao exemplo anterior, exceto que em vez de criar tipos anônimos, a função de seletor de resultado cria elementos XML que representam os objetos associados.</span><span class="sxs-lookup"><span data-stu-id="b5008-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="b5008-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5008-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="b5008-124">Executar junções internas</span><span class="sxs-lookup"><span data-stu-id="b5008-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="b5008-125">Executar junções externas esquerdas</span><span class="sxs-lookup"><span data-stu-id="b5008-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="b5008-126">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="b5008-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
