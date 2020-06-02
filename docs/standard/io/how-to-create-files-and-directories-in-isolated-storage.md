---
title: 'Como: Criar arquivos e diretórios no armazenamento isolado'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: b74bf62dabe24765e07ffa6820cc1675122a9122
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288544"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Como: Criar arquivos e diretórios no armazenamento isolado
Depois de obter um repositório isolado, você pode criar diretórios e arquivos para armazenar dados. Em um repositório, nomes de arquivo e diretório são especificados com relação à raiz do sistema de arquivos virtual.  
  
 Para criar um diretório, use o método de instância <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType>. Se você especificar um subdiretório de um diretório que não existe, os dois diretórios serão criados. Se você especificar um diretório que já existe, o método retornará sem criar um diretório, e nenhuma exceção será lançada. No entanto, se você especificar um nome de diretório que contém caracteres inválidos, uma exceção <xref:System.IO.IsolatedStorage.IsolatedStorageException> será lançada.  
  
 Para criar um arquivo, use o método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType>.  
  
 No sistema operacional Windows, nomes de arquivo de armazenamento isolado e de diretório diferenciam maiúsculas de minúsculas. Ou seja, se você criar um arquivo chamado `ThisFile.txt`, depois criar outro arquivo chamado `THISFILE.TXT`, somente um arquivo será criado. O nome do arquivo mantém sua capitalização original para fins de exibição.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra como criar arquivos e diretórios em um repositório isolado.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Armazenamento isolado](isolated-storage.md)
