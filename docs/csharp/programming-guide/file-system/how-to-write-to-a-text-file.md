---
title: "Como gravar em um arquivo de texto (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
dev_langs:
- CSharp
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c56095582561e4df19b164bc9a46b69a14da7c9d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Como escrever em um arquivo de texto (Guia de Programação em C#)
Estes exemplos mostram várias maneiras de gravar textos em um arquivo.  Os dois primeiros exemplos usam métodos de conveniência estáticos na classe <xref:System.IO.File?displayProperty=fullName> para gravar cada elemento de qualquer IEnumerable\<string> e uma cadeia de caracteres em um arquivo de texto.  O exemplo 3 mostra como adicionar texto a um arquivo quando você precisa processar cada linha individualmente enquanto escreve no arquivo.  Os exemplos de 1 a 3 substituem todo o conteúdo existente no arquivo, mas o exemplo 4 mostra como adicionar texto em um arquivo existente.  
  
 Todos esses exemplos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para escrever diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento e assim por diante.  Você também pode usar o recurso [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) do C#.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 Todos esses exemplos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para escrever diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento e assim por diante.  Você também pode usar o recurso [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) do C#.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O arquivo existe e é somente leitura.  
  
-   O nome do caminho pode ser muito longo.  
  
-   O disco pode estar cheio.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md)   
 [Exemplo: salvar uma coleção no armazenamento de aplicativos](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
