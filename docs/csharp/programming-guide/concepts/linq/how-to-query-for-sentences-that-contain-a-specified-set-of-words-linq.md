---
title: Como consultar frases que contêm um conjunto especificado de palavras (LINQ) (C#)
description: Saiba como usar o LINQ em C# para localizar frases em um arquivo de texto que contenham correspondências para cada um dos conjuntos de palavras, que podem ser populadas no tempo de execução.
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: daf86d6641b82fb77ca237e8a190b4f60b9dea4d
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465644"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="9d211-103">Como consultar frases que contêm um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9d211-103">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>
<span data-ttu-id="9d211-104">Este exemplo mostra como localizar frases em um arquivo de texto que contenham correspondências para cada conjunto de palavras especificado.</span><span class="sxs-lookup"><span data-stu-id="9d211-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="9d211-105">Embora a matriz de termos de pesquisa esteja embutida em código neste exemplo, ela também poderia ser populada dinamicamente em runtime.</span><span class="sxs-lookup"><span data-stu-id="9d211-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="9d211-106">Neste exemplo, a consulta retorna as frases que contêm as palavras "Historically", "data" e "integrated".</span><span class="sxs-lookup"><span data-stu-id="9d211-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d211-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d211-107">Example</span></span>  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 <span data-ttu-id="9d211-108">A consulta funciona primeiro dividindo o texto em frases e, em seguida, dividindo as sentenças em uma matriz de cadeias de caracteres que contêm cada palavra.</span><span class="sxs-lookup"><span data-stu-id="9d211-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="9d211-109">Para cada uma dessas matrizes, o método <xref:System.Linq.Enumerable.Distinct%2A> remove todas as palavras duplicadas e, em seguida, a consulta executa uma operação <xref:System.Linq.Enumerable.Intersect%2A> na matriz de palavras e na matriz `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="9d211-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="9d211-110">Se a contagem da interseção for igual à contagem da matriz `wordsToMatch`, todas as palavras foram encontradas nas palavras e a frase original será retornada.</span><span class="sxs-lookup"><span data-stu-id="9d211-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="9d211-111">Na chamada para <xref:System.String.Split%2A>, as marcas de pontuação são usadas como separadores para removê-las da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9d211-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="9d211-112">Se não fizer isso, por exemplo, você poderia ter uma cadeia de caracteres "Historically" que não corresponderia a "Historically" na matriz `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="9d211-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="9d211-113">Talvez você precise usar separadores adicionais, dependendo dos tipos de pontuação encontrados no texto de origem.</span><span class="sxs-lookup"><span data-stu-id="9d211-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d211-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9d211-114">Compiling the Code</span></span>  
<span data-ttu-id="9d211-115">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="9d211-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d211-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="9d211-116">See also</span></span>

- [<span data-ttu-id="9d211-117">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="9d211-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
