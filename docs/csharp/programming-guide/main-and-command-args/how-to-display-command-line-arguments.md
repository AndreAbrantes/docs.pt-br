---
title: Como exibir argumentos de linha de comando - C# Guia de Programação
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712020"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Como exibir argumentos de linha de comando (Guia de Programação C#)
Os argumentos fornecidos a um executável na linha de comando são acessíveis por meio de um parâmetro opcional para `Main`. Os argumentos são fornecidos na forma de uma matriz de cadeias de caracteres. Cada elemento da matriz contém um argumento. O espaço em branco entre os argumentos é removido. Por exemplo, considere essas invocações de linha de comando de um executável fictício:  
  
|Entrada na linha de comando|Matriz de cadeias de caracteres passada a Main|  
|----------------------------|-------------------------------------|  
|**executável.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executável.exe um dois**|"um"<br /><br /> "dois"|  
|**executável.exe "um dois" três**|"one two"<br /><br /> "three"|  
  
> [!NOTE]
> Quando estiver executando um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Exemplo  
 Este exemplo exibe os argumentos de linha de comando passados a um aplicativo de linha de comando. A saída mostrada é para a primeira entrada da tabela acima.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Build pela linha de comando com csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main() e argumentos de linha de comando](./index.md)
- [Valores retornados de Main()](./main-return-values.md)
