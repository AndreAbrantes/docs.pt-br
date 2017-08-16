---
title: "Como: consultar sentenças que contêm um conjunto especificado de palavras (LINQ) (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 31561d586c9c05f502002efdfc455acb55159fed
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Como: consultar sentenças que contêm um conjunto especificado de palavras (LINQ) (Visual Basic)
Este exemplo mostra como localizar as frases em um arquivo de texto que contêm correspondências para cada um de um conjunto especificado de palavras. Embora a matriz de termos de pesquisa é embutida em código neste exemplo, ele poderia também ser preenchido dinamicamente em tempo de execução. Neste exemplo, a consulta retorna as sentenças que contêm as palavras "Historicamente", "dados" e "integrado".  
  
## <a name="example"></a>Exemplo  
  
```vb  
Class FindSentences  
  
    Shared Sub Main()  
        Dim text As String = "Historically, the world of data and the world of objects " &   
        "have not been well integrated. Programmers work in C# or Visual Basic " &   
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &   
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &   
        "are tables, columns, rows, nodes, and separate languages for dealing with " &   
        "them. Data types often require translation between the two worlds; there are " &   
        "different standard functions. Because the object world has no notion of query, a " &   
        "query can only be represented as a string without compile-time type checking or " &   
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &   
        "objects in memory is often tedious and error-prone."  
  
        ' Split the text block into an array of sentences.  
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})  
  
        ' Define the search terms. This list could also be dynamically populated at runtime  
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}  
  
        ' Find sentences that contain all the terms in the wordsToMatch array  
        ' Note that the number of terms to match is not specified at compile time  
        Dim sentenceQuery = From sentence In sentences   
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                   StringSplitOptions.RemoveEmptyEntries)   
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()   
                            Select sentence  
  
        ' Execute the query  
        For Each str As String In sentenceQuery  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Class  
' Output:  
' Historically, the world of data and the world of objects have not been well integrated  
```  
  
 A consulta funciona primeiro dividindo o texto em sentenças, e, em seguida, dividindo as sentenças em uma matriz de cadeias de caracteres que contêm cada palavra. Para cada um desses conjuntos de <xref:System.Linq.Enumerable.Distinct%2A>método Remove todas as palavras duplicadas e, em seguida, executa a consulta um <xref:System.Linq.Enumerable.Intersect%2A>operação na matriz de word e o `wordsToMatch` array.</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Distinct%2A> Se a contagem de interseção é o mesmo que a contagem da `wordsToMatch` matriz, todas as palavras foram encontradas nas palavras e a frase original é retornada.  
  
 Na chamada para <xref:System.String.Split%2A>, as marcas de pontuação para removê-los da cadeia de caracteres usadas como separadores.</xref:System.String.Split%2A> Se você não fizer isso, por exemplo, você poderia ter uma cadeia de caracteres "Historicamente", que não corresponde a "Historicamente" no `wordsToMatch` matriz. Você talvez precise usar separadores adicionais, dependendo dos tipos de pontuação encontrado no texto de origem.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e uma `Imports` declaração para o namespace System. Linq.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
