---
title: "Como excluir arquivos e diretórios no armazenamento isolado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="2e2cd-102">Como excluir arquivos e diretórios no armazenamento isolado</span><span class="sxs-lookup"><span data-stu-id="2e2cd-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="2e2cd-103">Você pode excluir pastas e arquivos em um arquivo de armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="2e2cd-104">Em um armazenamento, nomes de arquivo e diretório são dependentes do sistema operacional e são especificados como relacionado à raiz do sistema de arquivos virtual.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="2e2cd-105">Eles não diferenciam maiusculas de minúsculas em sistemas operacionais Windows.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="2e2cd-106">O <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> classe fornece dois métodos para excluir arquivos e diretórios: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> e <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="2e2cd-107">Um <xref:System.IO.IsolatedStorage.IsolatedStorageException> exceção é gerada se você tentar excluir um arquivo ou diretório não existe.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="2e2cd-108">Se você incluir um caractere curinga no nome do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> lança um <xref:System.IO.IsolatedStorage.IsolatedStorageException> exceção, e <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> lança um <xref:System.ArgumentException> exceção.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="2e2cd-109">O <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> método falhará se o diretório contém quaisquer arquivos ou subpastas.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="2e2cd-110">Você pode usar o <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> e <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> métodos para recuperar os arquivos e diretórios existentes.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="2e2cd-111">Para obter mais informações sobre o sistema de arquivos virtual de um repositório de pesquisa, consulte [como: localizar arquivos e diretórios existentes no armazenamento isolado](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="2e2cd-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e2cd-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e2cd-112">Example</span></span>  
 <span data-ttu-id="2e2cd-113">O exemplo de código a seguir cria e, em seguida, exclui vários diretórios e arquivos.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2e2cd-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e2cd-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [<span data-ttu-id="2e2cd-115">Armazenamentos isolado</span><span class="sxs-lookup"><span data-stu-id="2e2cd-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
