---
title: Como copiar arquivos com um padrão específico para um diretório
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: ee3951e967436a1b8aec09b8e42dc6d1b547bc02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348846"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="b01e4-102">Como copiar arquivos com um padrão específico para um diretório no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b01e4-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="b01e4-103">O método <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retorna uma coleção somente leitura de cadeias de caracteres que representam os nomes de caminho para os arquivos.</span><span class="sxs-lookup"><span data-stu-id="b01e4-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="b01e4-104">É possível usar o parâmetro `wildCards` para especificar um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="b01e4-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="b01e4-105">Se nenhum arquivo correspondente for encontrado, uma coleção vazia será retornada.</span><span class="sxs-lookup"><span data-stu-id="b01e4-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="b01e4-106">Você pode usar o método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> para copiar os arquivos em um diretório.</span><span class="sxs-lookup"><span data-stu-id="b01e4-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="b01e4-107">Copiar arquivos com um padrão específico para um diretório</span><span class="sxs-lookup"><span data-stu-id="b01e4-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="b01e4-108">Use o método `GetFiles` para retornar a lista de arquivos.</span><span class="sxs-lookup"><span data-stu-id="b01e4-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="b01e4-109">Este exemplo retorna todos os arquivos .rtf do diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="b01e4-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="b01e4-110">Use o método `CopyFile` para copiar os arquivos.</span><span class="sxs-lookup"><span data-stu-id="b01e4-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="b01e4-111">Este exemplo copia os arquivos para o diretório de nome `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="b01e4-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="b01e4-112">Feche a instrução `For` com uma instrução `Next`.</span><span class="sxs-lookup"><span data-stu-id="b01e4-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="b01e4-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b01e4-113">Example</span></span>  

 <span data-ttu-id="b01e4-114">O exemplo a seguir, que apresenta os snippets acima em sua forma completa, copia todos os arquivos .rtf do diretório especificado para o diretório de nome `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="b01e4-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="b01e4-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b01e4-115">.NET Framework Security</span></span>  

 <span data-ttu-id="b01e4-116">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="b01e4-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b01e4-117">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b01e4-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="b01e4-118">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b01e4-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b01e4-119">O diretório não existe (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b01e4-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="b01e4-120">O diretório aponta para um arquivo existente (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b01e4-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b01e4-121">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b01e4-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="b01e4-122">Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="b01e4-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="b01e4-123">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b01e4-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="b01e4-124">O usuário não possui as permissões necessárias (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="b01e4-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b01e4-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="b01e4-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="b01e4-126">Como localizar subdiretórios com um padrão específico</span><span class="sxs-lookup"><span data-stu-id="b01e4-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="b01e4-127">Solução de problemas: lendo e gravando em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="b01e4-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="b01e4-128">Como obter a coleção de arquivos em um diretório</span><span class="sxs-lookup"><span data-stu-id="b01e4-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
