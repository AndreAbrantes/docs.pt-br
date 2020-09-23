---
title: 'Como: agrupar arquivos por extensão (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 3b1b02283dc65148b8a44952ce39659cc92b483a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077300"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="7bcf3-102">Como: agrupar arquivos por extensão (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bcf3-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="7bcf3-103">Este exemplo mostra como o LINQ pode ser usado para realizar operações avançadas de classificação e agrupamento em listas de arquivos ou pastas.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="7bcf3-104">Ele também mostra como paginar a saída na janela do console usando os métodos <xref:System.Linq.Enumerable.Skip%2A> e <xref:System.Linq.Enumerable.Take%2A>.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bcf3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7bcf3-105">Example</span></span>  

 <span data-ttu-id="7bcf3-106">A consulta a seguir mostra como agrupar o conteúdo de uma árvore de diretórios especificada, pela extensão de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7bcf3-107">A saída desse programa pode ser longa, dependendo dos detalhes do sistema de arquivos local e o que está definido em `startFolder`.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="7bcf3-108">Para habilitar a exibição de todos os resultados, este exemplo mostra como paginá-los.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="7bcf3-109">As mesmas técnicas podem ser aplicadas a aplicativos do Windows e aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="7bcf3-110">Observe que, como o código dispõe os itens em um grupo, é necessário um loop `For Each` aninhado.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="7bcf3-111">Há também alguma lógica adicional para calcular a posição atual na lista e para permitir que o usuário interrompa a paginação e saia do programa.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="7bcf3-112">Nesse caso específico, a consulta de paginação é executada nos resultados da consulta original armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="7bcf3-113">Em outros contextos, como LINQ to SQL, esse cache não é necessário.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="7bcf3-114">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="7bcf3-114">Compile the code</span></span>  

<span data-ttu-id="7bcf3-115">Crie um projeto de aplicativo de console Visual Basic, com uma `Imports` instrução para o namespace System. Linq.</span><span class="sxs-lookup"><span data-stu-id="7bcf3-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7bcf3-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="7bcf3-116">See also</span></span>

- [<span data-ttu-id="7bcf3-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bcf3-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="7bcf3-118">LINQ e diretórios de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bcf3-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
