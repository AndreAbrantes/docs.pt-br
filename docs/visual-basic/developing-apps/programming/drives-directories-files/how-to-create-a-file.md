---
title: Como criar um arquivo
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348795"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>Como criar um arquivo no Visual Basic

Este exemplo cria um arquivo de texto vazio no caminho especificado usando o método <xref:System.IO.File.Create%2A> na classe <xref:System.IO.File>.  
  
## <a name="example"></a>Exemplo  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  

 Use a variável `file` para gravar no arquivo.  
  
## <a name="robust-programming"></a>Programação robusta  

 Se o arquivo já existir, ele será substituído.  
  
 As seguintes condições podem causar uma exceção:  
  
- O nome do caminho está malformado. Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).  
  
- O caminho é somente leitura (<xref:System.IO.IOException>).  
  
- O nome do caminho é `Nothing` (<xref:System.ArgumentNullException>).  
  
- O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).  
  
- O caminho é inválido (<xref:System.IO.DirectoryNotFoundException>).  
  
- O caminho é apenas dois-pontos ":" (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  

 Uma <xref:System.Security.SecurityException> pode ser gerada em ambientes de confiança parcial.  
  
 A chamada para o método <xref:System.IO.File.Create%2A> requer <xref:System.Security.Permissions.FileIOPermission>.  
  
 Uma <xref:System.UnauthorizedAccessException> será gerada se o usuário não tiver permissão para criar o arquivo.  
  
## <a name="see-also"></a>Confira também

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [Usando bibliotecas de código parcialmente confiável](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [Noções básicas da segurança de acesso do código](../../../../framework/misc/code-access-security-basics.md)
