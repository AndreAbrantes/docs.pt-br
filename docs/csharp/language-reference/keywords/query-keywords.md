---
title: "Palavras-chave de consulta (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6dadce6d48e711032cca03a7f7c2ba02360e685f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="e5b2b-102">Palavras-chave de consulta (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e5b2b-102">Query Keywords (C# Reference)</span></span>
<span data-ttu-id="e5b2b-103">Esta seção contém as palavras-chave contextuais usadas em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="e5b2b-103">This section contains the contextual keywords used in query expressions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5b2b-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e5b2b-104">In This Section</span></span>  
  
|<span data-ttu-id="e5b2b-105">Cláusula</span><span class="sxs-lookup"><span data-stu-id="e5b2b-105">Clause</span></span>|<span data-ttu-id="e5b2b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5b2b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5b2b-107">from</span><span class="sxs-lookup"><span data-stu-id="e5b2b-107">from</span></span>](../../../csharp/language-reference/keywords/from-clause.md)|<span data-ttu-id="e5b2b-108">Especifica uma fonte de dados e uma variável de intervalo (semelhante a uma variável de iteração).</span><span class="sxs-lookup"><span data-stu-id="e5b2b-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|  
|[<span data-ttu-id="e5b2b-109">where</span><span class="sxs-lookup"><span data-stu-id="e5b2b-109">where</span></span>](../../../csharp/language-reference/keywords/where-clause.md)|<span data-ttu-id="e5b2b-110">Filtra elementos de origem baseados em uma ou mais expressões boolianas separadas por operadores AND e OR lógicos ( `&&` ou <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="e5b2b-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|  
|[<span data-ttu-id="e5b2b-111">select</span><span class="sxs-lookup"><span data-stu-id="e5b2b-111">select</span></span>](../../../csharp/language-reference/keywords/select-clause.md)|<span data-ttu-id="e5b2b-112">Especifica o tipo e a forma que os elementos na sequência retornada terão quando a consulta for executada.</span><span class="sxs-lookup"><span data-stu-id="e5b2b-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|  
|[<span data-ttu-id="e5b2b-113">group</span><span class="sxs-lookup"><span data-stu-id="e5b2b-113">group</span></span>](../../../csharp/language-reference/keywords/group-clause.md)|<span data-ttu-id="e5b2b-114">Agrupa os resultados da consulta de acordo com um valor de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="e5b2b-114">Groups query results according to a specified key value.</span></span>|  
|[<span data-ttu-id="e5b2b-115">into</span><span class="sxs-lookup"><span data-stu-id="e5b2b-115">into</span></span>](../../../csharp/language-reference/keywords/into.md)|<span data-ttu-id="e5b2b-116">Fornece um identificador que pode funcionar como uma referência aos resultados de uma cláusula join, group ou select.</span><span class="sxs-lookup"><span data-stu-id="e5b2b-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|  
|[<span data-ttu-id="e5b2b-117">orderby</span><span class="sxs-lookup"><span data-stu-id="e5b2b-117">orderby</span></span>](../../../csharp/language-reference/keywords/orderby-clause.md)|<span data-ttu-id="e5b2b-118">Classifica os resultados da consulta em ordem crescente ou decrescente com base no comparador padrão para o tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="e5b2b-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|  
|[<span data-ttu-id="e5b2b-119">join</span><span class="sxs-lookup"><span data-stu-id="e5b2b-119">join</span></span>](../../../csharp/language-reference/keywords/join-clause.md)|<span data-ttu-id="e5b2b-120">Une duas fontes de dados com base em uma comparação de igualdade entre dois critérios de correspondência especificados.</span><span class="sxs-lookup"><span data-stu-id="e5b2b-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|  
|[<span data-ttu-id="e5b2b-121">let</span><span class="sxs-lookup"><span data-stu-id="e5b2b-121">let</span></span>](../../../csharp/language-reference/keywords/let-clause.md)|<span data-ttu-id="e5b2b-122">Introduz uma variável de intervalo para armazenar os resultados de subexpressão em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="e5b2b-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|  
|[<span data-ttu-id="e5b2b-123">in</span><span class="sxs-lookup"><span data-stu-id="e5b2b-123">in</span></span>](../../../csharp/language-reference/keywords/in.md)|<span data-ttu-id="e5b2b-124">Palavra-chave contextual em uma cláusula [join](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e5b2b-124">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e5b2b-125">on</span><span class="sxs-lookup"><span data-stu-id="e5b2b-125">on</span></span>](../../../csharp/language-reference/keywords/on.md)|<span data-ttu-id="e5b2b-126">Palavra-chave contextual em uma cláusula [join](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e5b2b-126">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e5b2b-127">equals</span><span class="sxs-lookup"><span data-stu-id="e5b2b-127">equals</span></span>](../../../csharp/language-reference/keywords/equals.md)|<span data-ttu-id="e5b2b-128">Palavra-chave contextual em uma cláusula [join](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e5b2b-128">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e5b2b-129">by</span><span class="sxs-lookup"><span data-stu-id="e5b2b-129">by</span></span>](../../../csharp/language-reference/keywords/by.md)|<span data-ttu-id="e5b2b-130">Palavra-chave contextual em uma cláusula [group](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e5b2b-130">Contextual keyword in a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e5b2b-131">ascending</span><span class="sxs-lookup"><span data-stu-id="e5b2b-131">ascending</span></span>](../../../csharp/language-reference/keywords/ascending.md)|<span data-ttu-id="e5b2b-132">Palavra-chave contextual em uma cláusula [ordery](../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e5b2b-132">Contextual keyword in an [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e5b2b-133">descending</span><span class="sxs-lookup"><span data-stu-id="e5b2b-133">descending</span></span>](../../../csharp/language-reference/keywords/descending.md)|<span data-ttu-id="e5b2b-134">Palavra-chave contextual em uma cláusula [ordery](../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e5b2b-134">Contextual keyword in an [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) clause.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5b2b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5b2b-135">See Also</span></span>  
 <span data-ttu-id="e5b2b-136">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e5b2b-136">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="e5b2b-137">[LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span><span class="sxs-lookup"><span data-stu-id="e5b2b-137">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span></span>  
 <span data-ttu-id="e5b2b-138">[Expressões de Consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="e5b2b-138">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="e5b2b-139">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="e5b2b-139">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

