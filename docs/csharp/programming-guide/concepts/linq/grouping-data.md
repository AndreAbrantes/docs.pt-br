---
title: Agrupando dados (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2cf1b228a5ff4120bdf3b97a7ec9308f11d7b8ee
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="grouping-data-c"></a><span data-ttu-id="6bbb8-102">Agrupando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="6bbb8-102">Grouping Data (C#)</span></span>
<span data-ttu-id="6bbb8-103">O agrupamento refere-se à operação de colocação de dados em grupos, de modo que os elementos em cada grupo compartilhem um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="6bbb8-104">A ilustração a seguir mostra os resultados do agrupamento de uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="6bbb8-105">A chave para cada grupo é o caractere.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="6bbb8-106">![Operações de agrupamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="6bbb8-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="6bbb8-107">Os métodos do operador de consulta padrão que agrupam elementos de dados estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bbb8-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="6bbb8-108">Methods</span></span>  
  
|<span data-ttu-id="6bbb8-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="6bbb8-109">Method Name</span></span>|<span data-ttu-id="6bbb8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6bbb8-110">Description</span></span>|<span data-ttu-id="6bbb8-111">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="6bbb8-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="6bbb8-112">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6bbb8-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6bbb8-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="6bbb8-113">GroupBy</span></span>|<span data-ttu-id="6bbb8-114">Agrupa elementos que compartilham um atributo comum.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="6bbb8-115">Cada grupo é representado por um objeto <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="6bbb8-116">-ou-</span><span class="sxs-lookup"><span data-stu-id="6bbb8-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName>|  
|<span data-ttu-id="6bbb8-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="6bbb8-117">ToLookup</span></span>|<span data-ttu-id="6bbb8-118">Insere os elementos em um <xref:System.Linq.Lookup%602> (um dicionário one-to-many) com base em uma função de seletor de chave.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="6bbb8-119">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="6bbb8-120">Exemplo de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="6bbb8-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="6bbb8-121">O seguinte exemplo de código usa a cláusula `group by` para agrupar inteiros em uma lista de acordo com se eles são pares ou ímpares.</span><span class="sxs-lookup"><span data-stu-id="6bbb8-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bbb8-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bbb8-122">See Also</span></span>  
 <span data-ttu-id="6bbb8-123"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="6bbb8-123"><xref:System.Linq></span></span>   
 <span data-ttu-id="6bbb8-124">[Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="6bbb8-124">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="6bbb8-125">[Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="6bbb8-125">[group clause](../../../../csharp/language-reference/keywords/group-clause.md) </span></span>  
 <span data-ttu-id="6bbb8-126">[Como Criar um Grupo Aninhado](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md) </span><span class="sxs-lookup"><span data-stu-id="6bbb8-126">[How to: Create a Nested Group](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md) </span></span>  
 <span data-ttu-id="6bbb8-127">[Como agrupar arquivos por extensão (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span><span class="sxs-lookup"><span data-stu-id="6bbb8-127">[How to: Group Files by Extension (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span></span>  
 <span data-ttu-id="6bbb8-128">[Como Agrupar Resultados de Consulta](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md) </span><span class="sxs-lookup"><span data-stu-id="6bbb8-128">[How to: Group Query Results](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md) </span></span>  
 <span data-ttu-id="6bbb8-129">[Como executar uma subconsulta em uma operação de agrupamento](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md) </span><span class="sxs-lookup"><span data-stu-id="6bbb8-129">[How to: Perform a Subquery on a Grouping Operation](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md) </span></span>  
 [<span data-ttu-id="6bbb8-130">Como dividir um arquivo em vários arquivos usando grupos (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6bbb8-130">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)

