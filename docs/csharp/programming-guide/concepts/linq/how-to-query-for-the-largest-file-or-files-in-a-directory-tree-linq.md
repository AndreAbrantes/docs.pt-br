---
title: Como consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (C#)
description: Este exemplo de C# mostra cinco consultas LINQ relacionadas ao tamanho do arquivo em bytes. Você pode modificá-los para consultar uma outra Propriedade do objeto FileInfo.
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 049db9bf104af1593ba9807c307008e8e760da32
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176247"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="50ed9-104">Como consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="50ed9-104">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>

<span data-ttu-id="50ed9-105">Este exemplo mostra cinco consultas relacionadas ao tamanho do arquivo em bytes:</span><span class="sxs-lookup"><span data-stu-id="50ed9-105">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="50ed9-106">Como recuperar o tamanho em bytes do maior arquivo.</span><span class="sxs-lookup"><span data-stu-id="50ed9-106">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="50ed9-107">Como recuperar o tamanho em bytes do menor arquivo.</span><span class="sxs-lookup"><span data-stu-id="50ed9-107">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="50ed9-108">Como recuperar o maior ou menor arquivo do objeto <xref:System.IO.FileInfo> de uma ou mais pastas em uma pasta raiz especificada.</span><span class="sxs-lookup"><span data-stu-id="50ed9-108">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="50ed9-109">Como recuperar uma sequência, como os 10 maiores arquivos.</span><span class="sxs-lookup"><span data-stu-id="50ed9-109">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="50ed9-110">Como ordenar os arquivos em grupos com base no tamanho do arquivo em bytes, ignorando arquivos menores do que um tamanho especificado.</span><span class="sxs-lookup"><span data-stu-id="50ed9-110">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50ed9-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50ed9-111">Example</span></span>  

 <span data-ttu-id="50ed9-112">O exemplo a seguir contém cinco consultas separadas que mostram como consultar e agrupar arquivos, dependendo do tamanho do arquivo em bytes.</span><span class="sxs-lookup"><span data-stu-id="50ed9-112">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="50ed9-113">Você pode modificar facilmente esses exemplos para basear a consulta em outra propriedade do objeto <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="50ed9-113">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
  
}  
```  
  
 <span data-ttu-id="50ed9-114">Para retornar um ou mais objetos <xref:System.IO.FileInfo> completos, a consulta deve primeiro examinar cada um dos objetos na fonte de dados e, em seguida, classificá-los segundo o valor de sua propriedade Length.</span><span class="sxs-lookup"><span data-stu-id="50ed9-114">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="50ed9-115">Em seguida, ela pode retornar um único elemento ou a sequência com os maiores tamanhos.</span><span class="sxs-lookup"><span data-stu-id="50ed9-115">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="50ed9-116">Use <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro elemento em uma lista.</span><span class="sxs-lookup"><span data-stu-id="50ed9-116">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="50ed9-117">Use <xref:System.Linq.Enumerable.Take%2A> para retornar o primeiro número n de elementos.</span><span class="sxs-lookup"><span data-stu-id="50ed9-117">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="50ed9-118">Especifique uma ordem de classificação decrescente para colocar os menores elementos no início da lista.</span><span class="sxs-lookup"><span data-stu-id="50ed9-118">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="50ed9-119">A consulta chama um método separado para obter o tamanho do arquivo em bytes para consumir a exceção possível que ocorrerá caso um arquivo tenha sido excluído em outro thread no período desde que o objeto <xref:System.IO.FileInfo> foi criado na chamada para `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="50ed9-119">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="50ed9-120">Embora o objeto <xref:System.IO.FileInfo> já tenha sido criado, a exceção poderá ocorrer porque um objeto <xref:System.IO.FileInfo> tentará atualizar sua propriedade <xref:System.IO.FileInfo.Length%2A> usando o tamanho mais atual em bytes na primeira vez que a propriedade foi acessada.</span><span class="sxs-lookup"><span data-stu-id="50ed9-120">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="50ed9-121">Ao colocar essa operação em um bloco try-catch fora da consulta, nós seguimos a regra de evitar operações em consultas que podem causar efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="50ed9-121">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="50ed9-122">Em geral, deve-se ter muito cuidado ao consumir exceções para garantir que um aplicativo não seja deixado em um estado desconhecido.</span><span class="sxs-lookup"><span data-stu-id="50ed9-122">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="50ed9-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="50ed9-123">Compiling the Code</span></span>  

<span data-ttu-id="50ed9-124">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="50ed9-124">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="50ed9-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="50ed9-125">See also</span></span>

- [<span data-ttu-id="50ed9-126">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="50ed9-126">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="50ed9-127">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="50ed9-127">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
