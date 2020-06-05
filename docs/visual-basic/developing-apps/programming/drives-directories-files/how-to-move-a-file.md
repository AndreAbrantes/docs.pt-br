---
title: 'Como: mover um arquivo'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 2dafeb3b5f8b8c3a8976b25c1a57f405aebb32b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401596"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="b5a26-102">Como mover um arquivo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5a26-102">How to: Move a File in Visual Basic</span></span>

<span data-ttu-id="b5a26-103">O método `My.Computer.FileSystem.MoveFile` pode ser utilizado para mover um arquivo para outra pasta.</span><span class="sxs-lookup"><span data-stu-id="b5a26-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="b5a26-104">Se a estrutura de destino não existir, ela será criada.</span><span class="sxs-lookup"><span data-stu-id="b5a26-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="b5a26-105">Mover um arquivo</span><span class="sxs-lookup"><span data-stu-id="b5a26-105">To move a file</span></span>  
  
- <span data-ttu-id="b5a26-106">Use o método `MoveFile` para mover o arquivo, especificando o nome de arquivo e o local tanto para o arquivo de origem quanto para o arquivo de destino.</span><span class="sxs-lookup"><span data-stu-id="b5a26-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="b5a26-107">Este exemplo move o arquivo de nome `test.txt` de `TestDir1` para `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="b5a26-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="b5a26-108">Observe que o nome do arquivo de destino é especificado mesmo que seja igual ao nome do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="b5a26-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="b5a26-109">Mover um arquivo e renomeá-lo</span><span class="sxs-lookup"><span data-stu-id="b5a26-109">To move a file and rename it</span></span>  
  
- <span data-ttu-id="b5a26-110">Use o método `MoveFile` para mover o arquivo, especificando o nome de arquivo e o local, o local de destino e o novo nome no local de destino.</span><span class="sxs-lookup"><span data-stu-id="b5a26-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="b5a26-111">Este exemplo move o arquivo de nome `test.txt` de `TestDir1` para `TestDir2` e o renomeia como `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="b5a26-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b5a26-112">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b5a26-112">Robust Programming</span></span>  

 <span data-ttu-id="b5a26-113">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="b5a26-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b5a26-114">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="b5a26-115">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b5a26-116">`destinationFileName` é `Nothing` ou é uma cadeia de caracteres vazia (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b5a26-117">O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="b5a26-118">O caminho combinado aponta para um diretório existente, o arquivo de destino existe e `overwrite` é definido como `False`, um arquivo no diretório de destino com o mesmo nome está sendo usado ou o usuário não tem permissões suficientes para acessar o arquivo (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b5a26-119">Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="b5a26-120">`showUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e o usuário cancelou a operação ou ocorre um erro de E/S não especificado (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="b5a26-121">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="b5a26-122">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="b5a26-123">O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="b5a26-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a26-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5a26-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="b5a26-125">Como: renomear um arquivo</span><span class="sxs-lookup"><span data-stu-id="b5a26-125">How to: Rename a File</span></span>](how-to-rename-a-file.md)
- [<span data-ttu-id="b5a26-126">Como: criar uma cópia de um arquivo em outro diretório</span><span class="sxs-lookup"><span data-stu-id="b5a26-126">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="b5a26-127">Como: analisar caminhos de arquivo</span><span class="sxs-lookup"><span data-stu-id="b5a26-127">How to: Parse File Paths</span></span>](how-to-parse-file-paths.md)
