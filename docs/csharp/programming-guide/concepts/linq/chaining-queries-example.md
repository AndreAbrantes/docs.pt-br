---
title: Exemplo de encadeamento de consultas (C#)
description: Este exemplo mostra o que acontece quando você encadea duas consultas que usam a execução adiada e a avaliação lenta em C#.
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 0cfcfe1c8f537778fd1ef909277d95d83991af51
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105534"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="4396c-103">Exemplo de encadeamento de consultas (C#)</span><span class="sxs-lookup"><span data-stu-id="4396c-103">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="4396c-104">Este exemplo compila no exemplo anterior e mostra o que acontece quando você encadeia duas consultas que usam execução adiada e avaliação lenta.</span><span class="sxs-lookup"><span data-stu-id="4396c-104">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4396c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4396c-105">Example</span></span>  
 <span data-ttu-id="4396c-106">Nesse exemplo, um outro método de extensão é apresentado, `AppendString`, que acrescenta uma cadeia de caracteres especificada em cada cadeia de caracteres na coleção de origem, e produz nas novas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4396c-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="4396c-107">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="4396c-107">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 <span data-ttu-id="4396c-108">Nesse exemplo, você pode ver que cada método de extensão opera um de cada vez para cada item na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="4396c-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="4396c-109">O que deve ser claro desse exemplo é o mesmo que nós encadeemos juntos consultas que rendem coleções, qualquer coleção intermediária é materializada.</span><span class="sxs-lookup"><span data-stu-id="4396c-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="4396c-110">Em vez disso, cada item é passado de um método lenta a seguir.</span><span class="sxs-lookup"><span data-stu-id="4396c-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="4396c-111">Isso resulta em uma pegada muito menor de memória do que uma abordagem que recebe primeiro uma matriz de cadeias de caracteres, então cria uma segunda matriz de cadeias de caracteres que foram convertidos para maiúsculas, e criar finalmente uma terceira matriz de cadeias de caracteres onde cada cadeia de caracteres tem os pontos de exclamação acrescentados a ele.</span><span class="sxs-lookup"><span data-stu-id="4396c-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="4396c-112">O próximo tópico neste tutorial mostra o materialization intermediário:</span><span class="sxs-lookup"><span data-stu-id="4396c-112">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="4396c-113">Materialização intermediária (C#)</span><span class="sxs-lookup"><span data-stu-id="4396c-113">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="4396c-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="4396c-114">See also</span></span>

- [<span data-ttu-id="4396c-115">Tutorial: encadear consultas juntas (C#)</span><span class="sxs-lookup"><span data-stu-id="4396c-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
