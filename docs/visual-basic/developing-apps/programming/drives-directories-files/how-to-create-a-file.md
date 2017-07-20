---
title: Como Criar um Arquivo no Visual Basic | Microsoft Docs
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
- text files, creating
- files, creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
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
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: f9e2b11b6eed10bac04d22b202e7e16cfa70225d
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-create-a-file-in-visual-basic"></a>Como criar um arquivo no Visual Basic
Este exemplo cria um arquivo de texto vazio no caminho especificado usando o método <xref:System.IO.File.Create%2A> na classe <xref:System.IO.File>.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Use a variável `file` para gravar no arquivo.  
  
## <a name="robust-programming"></a>Programação robusta  
 Se o arquivo já existir, ele será substituído.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome do caminho está malformado. Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).  
  
-   O caminho é somente leitura (<xref:System.IO.IOException>).  
  
-   O nome do caminho é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).  
  
-   O caminho é inválido (<xref:System.IO.DirectoryNotFoundException>).  
  
-   O caminho é apenas dois-pontos ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Uma <xref:System.Security.SecurityException> pode ser gerada em ambientes de confiança parcial.  
  
 A chamada para o método <xref:System.IO.File.Create%2A> requer <xref:System.Security.Permissions.FileIOPermission>.  
  
 Uma <xref:System.UnauthorizedAccessException> será gerada se o usuário não tiver permissão para criar o arquivo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO>   
 <xref:System.IO.File.Create%2A>   
 [Usando Bibliotecas de Código Parcialmente Confiável](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)   
 [Noções Básicas da Segurança de Acesso do Código](https://msdn.microsoft.com/library/33tceax8)
