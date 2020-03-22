---
title: Como gravar em arquivos binários
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334425"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="4db42-102">Como gravar em arquivos binários no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4db42-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="4db42-103">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> grava dados em um arquivo binário.</span><span class="sxs-lookup"><span data-stu-id="4db42-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="4db42-104">Se o parâmetro `append` for `True`, ele acrescentará os dados ao arquivo; caso contrário, os dados no arquivo serão substituídos.</span><span class="sxs-lookup"><span data-stu-id="4db42-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="4db42-105">Se o caminho especificado, excluindo o nome de arquivo, não for válido, uma exceção <xref:System.IO.DirectoryNotFoundException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="4db42-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="4db42-106">Se o caminho for válido, mas o arquivo não existir, o arquivo será criado.</span><span class="sxs-lookup"><span data-stu-id="4db42-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="4db42-107">Para gravar em um arquivo binário</span><span class="sxs-lookup"><span data-stu-id="4db42-107">To write to a binary file</span></span>

<span data-ttu-id="4db42-108">Use o método `WriteAllBytes`, fornecendo o nome e o caminho do arquivo e os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="4db42-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="4db42-109">Este exemplo acrescenta a matriz de dados `CustomerData` ao arquivo chamado `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="4db42-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="4db42-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="4db42-110">Robust Programming</span></span>

<span data-ttu-id="4db42-111">As seguintes condições podem criar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="4db42-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="4db42-112">O caminho não é válido por um destes motivos: é uma cadeia de caracteres de comprimento zero; contém somente espaço em branco ou contém caracteres inválidos.</span><span class="sxs-lookup"><span data-stu-id="4db42-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="4db42-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="4db42-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="4db42-114">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="4db42-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="4db42-115">`File` aponta para um caminho que não existe (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="4db42-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="4db42-116">O arquivo está sendo usado por outro processo, ou ocorre um erro de E/S (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="4db42-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="4db42-117">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="4db42-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="4db42-118">Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="4db42-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="4db42-119">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4db42-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="4db42-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="4db42-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="4db42-121">Como gravar texto em arquivos</span><span class="sxs-lookup"><span data-stu-id="4db42-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
