---
title: Classes usadas em E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ca1ecff264734c16369c9a7d28fbb388bb2f1ccc
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Classes usadas em E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)
As tabelas a seguir listam as classes usadas comumente para E/S de arquivos do .NET Framework, categorizadas em classes de E/S de arquivos, classes usadas para criar fluxos e classes usadas para ler e gravar em fluxos.  
  
 Para inserir a documentação [!INCLUDE[dnprdnlong](../../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] e encontrar uma listagem mais abrangente, consulte [Visão geral da biblioteca de classes](https://msdn.microsoft.com/library/hfa3fa08).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Classes básicas de E/S para arquivos, unidades e pastas  
 A tabela a seguir lista e descreve as principais classes usadas para E/S de arquivos.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=fullName>|Fornece métodos estáticos para criar, mover e enumerar ao longo de diretórios e subdiretórios.|  
|<xref:System.IO.DirectoryInfo?displayProperty=fullName>|Fornece métodos de instância para criar, mover e enumerar ao longo de diretórios e subdiretórios.|  
|<xref:System.IO.DriveInfo?displayProperty=fullName>|Fornece métodos de instância para criar, mover e enumerar ao longo de unidades.|  
|<xref:System.IO.File?displayProperty=fullName>|Fornece métodos estáticos para criar, copiar, excluir, mover e abrir arquivos, além de ajudar na criação de um `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=fullName>|Define constantes para acesso de leitura, gravação ou leitura/gravação para um arquivo.|  
|<xref:System.IO.FileAttributes?displayProperty=fullName>|Fornece atributos para arquivos e diretórios como `Archive`, `Hidden` e `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=fullName>|Fornece métodos estáticos para criar, copiar, excluir, mover e abrir arquivos, além de ajudar na criação de um `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=fullName>|Controla como um arquivo é aberto. Este parâmetro é especificado em muitos dos construtores para `FileStream` e `IsolatedStorageFileStream`, também para os métodos `Open` de <xref:System.IO.File> e <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=fullName>|Define constantes para controlar o tipo de acesso que outros fluxos de arquivos podem ter ao mesmo arquivo.|  
|<xref:System.IO.Path?displayProperty=fullName>|Fornece métodos e propriedades para processar cadeias de caracteres de diretório.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>|Controla o acesso de arquivos e pastas definindo permissões <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> e <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>.|  
  
## <a name="classes-used-to-create-streams"></a>Classes usadas para criar fluxos  
 A tabela a seguir lista e descreve as principais classes usadas para criar fluxos.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=fullName>|Adiciona uma camada de armazenamento em buffer para ler e gravar operações em outro fluxo.|  
|<xref:System.IO.FileStream?displayProperty=fullName>|Dá suporte ao acesso aleatório a arquivos por meio de seu método <xref:System.IO.FileStream.Seek%2A>. <xref:System.IO.FileStream> abre arquivos de forma síncrona por padrão, mas também dá suporte à operação assíncrona.|  
|<xref:System.IO.MemoryStream?displayProperty=fullName>|Cria um fluxo cujo repositório de backup é a memória, em vez de um arquivo.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=fullName>|Fornece o fluxo de dados subjacente para acesso à rede.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=fullName>|Define uma transmissão que liga fluxos de dados a transformações criptográficas.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Classes usadas para ler e gravar em fluxos  
 A tabela a seguir mostra as classes específicas usadas para ler e gravar em arquivos com fluxos.  
  
|**Class**|**Descrição**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=fullName>|Lê cadeias de caracteres codificadas e tipos de dados primitivos de um <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=fullName>|Grava cadeias de caracteres codificadas e tipos de dados primitivos em um <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=fullName>|Lê caracteres de um <xref:System.IO.FileStream>, usando <xref:System.IO.StreamReader.CurrentEncoding%2A> para converter caracteres em bytes e vice-versa. <xref:System.IO.StreamReader> tem um construtor que tenta determinar o <xref:System.IO.StreamReader.CurrentEncoding%2A> correto de determinado fluxo, com base na presença de um preâmbulo específico de <xref:System.IO.StreamReader.CurrentEncoding%2A>, como uma marca de ordem de byte.|  
|<xref:System.IO.StreamWriter?displayProperty=fullName>|Grava caracteres em um `FileStream`, usando <xref:System.IO.StreamWriter.Encoding%2A> para converter caracteres em bytes.|  
|<xref:System.IO.StringReader?displayProperty=fullName>|Lê caracteres de um `String`. A saída pode ser um fluxo em qualquer codificação ou um `String`.|  
|<xref:System.IO.StringWriter?displayProperty=fullName>|Grava caracteres em um `String`. A saída pode ser um fluxo em qualquer codificação ou um `String`.|  
  
## <a name="see-also"></a>Consulte também  
 [Compondo fluxos](https://msdn.microsoft.com/library/e4y2dch9)   
 [E/S de arquivo e de fluxo](https://msdn.microsoft.com/library/k3352a4t)   
 [E/S de arquivo assíncrona](https://msdn.microsoft.com/library/kztecsys)   
 [Noções básicas de E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
