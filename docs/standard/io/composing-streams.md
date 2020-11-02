---
title: Redigir fluxos
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
ms.openlocfilehash: 93295c1d70f510ef563abc3a191d6690b1174fa8
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188569"
---
# <a name="compose-streams"></a><span data-ttu-id="91211-102">Redigir fluxos</span><span class="sxs-lookup"><span data-stu-id="91211-102">Compose streams</span></span>
<span data-ttu-id="91211-103">Um *repositório de backup* é um meio de armazenamento, como um disco ou memória.</span><span class="sxs-lookup"><span data-stu-id="91211-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="91211-104">Cada repositório de backup diferente implementa seu próprio fluxo como uma implementação da classe <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="91211-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="91211-105">Cada tipo de fluxo lê e grava bytes de e para seu repositório de backup específico.</span><span class="sxs-lookup"><span data-stu-id="91211-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="91211-106">Os fluxos que se conectam a repositórios de backup são chamados de *fluxos base* .</span><span class="sxs-lookup"><span data-stu-id="91211-106">Streams that connect to backing stores are called *base streams* .</span></span> <span data-ttu-id="91211-107">Os fluxos base têm construtores com os parâmetros necessários para conectar o fluxo ao repositório de backup.</span><span class="sxs-lookup"><span data-stu-id="91211-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="91211-108">Por exemplo, <xref:System.IO.FileStream> tem construtores que especificam um parâmetro de caminho, o qual especifica como o arquivo será compartilhado por processos.</span><span class="sxs-lookup"><span data-stu-id="91211-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="91211-109">O design das classes <xref:System.IO> fornece uma composição de fluxo simplificada.</span><span class="sxs-lookup"><span data-stu-id="91211-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="91211-110">Você pode anexar os fluxos base a um ou mais fluxos de passagem que fornecem a funcionalidade desejada.</span><span class="sxs-lookup"><span data-stu-id="91211-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="91211-111">Você pode anexar um leitor ou um gravador ao final da cadeia, de forma que os tipos preferidos possam ser lidos ou gravados com facilidade.</span><span class="sxs-lookup"><span data-stu-id="91211-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="91211-112">Os exemplos de código a seguir criam um **FileStream** em torno do *MyFile.txt* existente para armazenar em buffer *MyFile.txt* .</span><span class="sxs-lookup"><span data-stu-id="91211-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt* .</span></span> <span data-ttu-id="91211-113">Observe que os **filestreams** são armazenados em buffer por padrão.</span><span class="sxs-lookup"><span data-stu-id="91211-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="91211-114">Os exemplos pressupõem que um arquivo chamado *MyFile.txt* já exista na mesma pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91211-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="91211-115">Exemplo: usar StreamReader</span><span class="sxs-lookup"><span data-stu-id="91211-115">Example: Use StreamReader</span></span>
<span data-ttu-id="91211-116">O exemplo a seguir cria um <xref:System.IO.StreamReader> para ler caracteres do **FileStream** , que é passado para o **StreamReader** como seu argumento construtor.</span><span class="sxs-lookup"><span data-stu-id="91211-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream** , which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="91211-117">Em seguida, <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> lê até <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> não encontrar mais caracteres.</span><span class="sxs-lookup"><span data-stu-id="91211-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="91211-118">Exemplo: usar BinaryReader</span><span class="sxs-lookup"><span data-stu-id="91211-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="91211-119">O exemplo a seguir cria um <xref:System.IO.BinaryReader> para ler bytes do **FileStream** , que é passado para o **BinaryReader** como seu argumento construtor.</span><span class="sxs-lookup"><span data-stu-id="91211-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream** , which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="91211-120">Em seguida, <xref:System.IO.BinaryReader.ReadByte%2A> lê até <xref:System.IO.BinaryReader.PeekChar%2A> não encontrar mais bytes.</span><span class="sxs-lookup"><span data-stu-id="91211-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="91211-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="91211-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
