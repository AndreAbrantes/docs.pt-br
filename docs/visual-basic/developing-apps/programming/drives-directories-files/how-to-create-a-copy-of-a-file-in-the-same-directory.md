---
title: "Como criar uma cópia de um arquivo no mesmo diretório no Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- File.Copy
dev_langs:
- VB
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files, copying
- CopyFile method, copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 21
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
ms.openlocfilehash: c7078edf6822cc06c7d3c7933c5df7fdd2a73e6f
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Como criar uma cópia de um arquivo no mesmo diretório no Visual Basic
Use o método `My.Computer.FileSystem.CopyFile` para copiar arquivos. Os parâmetros permitem substituir os arquivos existentes, renomear o arquivo, mostrar o progresso da operação e permitir que o usuário cancele a operação.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Para criar uma cópia de um arquivo na mesma pasta  
  
-   Use o método `CopyFile`, fornecendo o arquivo e o local de destino. O exemplo a seguir cria uma cópia do `test.txt` chamada `test2.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Para criar uma cópia de um arquivo na mesma pasta, sobrescrevendo arquivos existentes  
  
-   Use o método `CopyFile`, fornecendo o arquivo e o local de destino e configurando `overwrite` como `True`. O exemplo a seguir cria uma cópia do `test.txt` com o nome `test2.txt` e substitui os arquivos existentes com este nome.  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar o lançamento de uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
-   O sistema não conseguiu recuperar o caminho absoluto (<xref:System.ArgumentException>).  
  
-   O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).  
  
-   O caminho combinado aponta para um diretório existente (<xref:System.IO.IOException>).  
  
-   O arquivo de destino já existe e `overwrite` está definido como `False` (<xref:System.IO.IOException>).  
  
-   O usuário não tem permissões suficientes para acessar o arquivo (<xref:System.IO.IOException>).  
  
-   Um arquivo na pasta de destino com o mesmo nome está sendo usado (<xref:System.IO.IOException>).  
  
-   Um nome de pasta no caminho contém dois pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   `ShowUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e o usuário cancelou a operação (<xref:System.OperationCanceledException>).  
  
-   `ShowUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e ocorreu um erro de E/S não especificado (<xref:System.OperationCanceledException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).  
  
-   O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [Como Copiar Arquivos com um Padrão Específico para um Diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [Como Criar uma Cópia de um Arquivo em um Diretório Diferente](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [Como Copiar um Diretório para outro Diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [Como renomear um arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
