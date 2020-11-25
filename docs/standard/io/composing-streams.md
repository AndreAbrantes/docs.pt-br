---
title: Redigir fluxos
ms.date: 01/21/2019
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
ms.openlocfilehash: d848a989378ed40df794554f3a0a9a7f135fbd4e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732184"
---
# <a name="compose-streams"></a>Redigir fluxos

Um *repositório de backup* é um meio de armazenamento, como um disco ou memória. Cada repositório de backup diferente implementa seu próprio fluxo como uma implementação da classe <xref:System.IO.Stream>.

Cada tipo de fluxo lê e grava bytes de e para seu repositório de backup específico. Os fluxos que se conectam a repositórios de backup são chamados de *fluxos base*. Os fluxos base têm construtores com os parâmetros necessários para conectar o fluxo ao repositório de backup. Por exemplo, <xref:System.IO.FileStream> tem construtores que especificam um parâmetro de caminho, o qual especifica como o arquivo será compartilhado por processos.  

O design das classes <xref:System.IO> fornece uma composição de fluxo simplificada. Você pode anexar os fluxos base a um ou mais fluxos de passagem que fornecem a funcionalidade desejada. Você pode anexar um leitor ou um gravador ao final da cadeia, de forma que os tipos preferidos possam ser lidos ou gravados com facilidade.  

Os exemplos de código a seguir criam um **FileStream** em torno do *MyFile.txt* existente para armazenar em buffer *MyFile.txt*. Observe que os **filestreams** são armazenados em buffer por padrão.

>[!IMPORTANT]
>Os exemplos pressupõem que um arquivo chamado *MyFile.txt* já exista na mesma pasta do aplicativo.  

## <a name="example-use-streamreader"></a>Exemplo: usar StreamReader

O exemplo a seguir cria um <xref:System.IO.StreamReader> para ler caracteres do **FileStream**, que é passado para o **StreamReader** como seu argumento construtor. Em seguida, <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> lê até <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> não encontrar mais caracteres.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Exemplo: usar BinaryReader

O exemplo a seguir cria um <xref:System.IO.BinaryReader> para ler bytes do **FileStream**, que é passado para o **BinaryReader** como seu argumento construtor. Em seguida, <xref:System.IO.BinaryReader.ReadByte%2A> lê até <xref:System.IO.BinaryReader.PeekChar%2A> não encontrar mais bytes.  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
