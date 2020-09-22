---
title: O arquivo é muito grande para ser lido em um array de bytes
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 89459aaf766a70f69008f847dda7ac6e2a1e41d1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874181"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="9d5ad-102">O arquivo é muito grande para ser lido em um array de bytes</span><span class="sxs-lookup"><span data-stu-id="9d5ad-102">File is too large to read into a byte array</span></span>

<span data-ttu-id="9d5ad-103">O tamanho do arquivo que você está tentando ler em uma matriz de bytes excede 4 GB.</span><span class="sxs-lookup"><span data-stu-id="9d5ad-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="9d5ad-104">O `My.Computer.FileSystem.ReadAllBytes` método não pode ler um arquivo que exceda esse tamanho.</span><span class="sxs-lookup"><span data-stu-id="9d5ad-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d5ad-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9d5ad-105">To correct this error</span></span>  
  
- <span data-ttu-id="9d5ad-106">Use um <xref:System.IO.StreamReader> para ler o arquivo.</span><span class="sxs-lookup"><span data-stu-id="9d5ad-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="9d5ad-107">Para obter mais informações, consulte [noções básicas de .NET Framework e/s de arquivo e o sistema de arquivos (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="9d5ad-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d5ad-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="9d5ad-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="9d5ad-109">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d5ad-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="9d5ad-110">Como: ler texto usando arquivos com um StreamReader</span><span class="sxs-lookup"><span data-stu-id="9d5ad-110">How to: Read Text from Files with a StreamReader</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
