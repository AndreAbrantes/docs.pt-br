---
title: "extern (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- extern_CSharpKeyword
- extern
dev_langs:
- CSharp
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
caps.latest.revision: 26
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 61cde8c8f6b3d255be5f6040141542e3e8d1e8c7
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="extern-c-reference"></a>extern (Referência de C#)
O modificador `extern` é usado para declarar um método implementado externamente. Um uso comum do modificador `extern` é com o atributo `DllImport` quando você está usando serviços Interop para chamar código não gerenciado. Nesse caso, o método também deve ser declarado como `static` conforme mostrado no seguinte exemplo:  
  
```  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 A palavra-chave `extern` também pode definir um alias de assembly externo que possibilita referenciar diferentes versões do mesmo componente de dentro de um único assembly. Para obter mais informações, consulte [alias extern](../../../csharp/language-reference/keywords/extern-alias.md).  
  
 É um erro usar os modificadores [abstract](../../../csharp/language-reference/keywords/abstract.md) e `extern` juntos para modificar o mesmo membro. Usar o modificador `extern` significa que esse método é implementado fora do código C#, enquanto que usar o modificador `abstract` significa que a implementação do método não é fornecida na classe.  
  
 A palavra-chave extern possui utilizações mais limitadas em C# do que em C++. Para comparar a palavra-chave de C# com a palavra-chave de C++, consulte Usando extern para especificar vínculos na referência da linguagem C++.  
  
## <a name="example"></a>Exemplo  
 **Exemplo 1.** Neste exemplo, o programa recebe uma cadeia de caracteres do usuário e a exibe dentro de uma caixa de mensagem. O programa usa o método `MessageBox` importado da biblioteca User32.dll.  
  
 [!code-cs[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]  
  
## <a name="example"></a>Exemplo  
 **Exemplo 2.** Este exemplo ilustra um programa C# que chama uma biblioteca em C (uma DLL nativa).  
  
 1. Crie o seguinte arquivo em C e atribua o nome `cmdll.c`:  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a>Exemplo  
 2. Abra uma janela do Prompt de Comando de Ferramentas Nativas do Visual Studio x64 (ou x32) do diretório de instalação do Visual Studio e compile o arquivo `cmdll.c` digitando **cl /LD cmdll.c** no prompt de comando.  
  
 3. No mesmo diretório, crie o seguinte arquivo em C# e atribua o nome `cm.cs`:  
  
```  
// cm.cs  
using System;  
using System.Runtime.InteropServices;  
public class MainClass   
{  
   [DllImport("Cmdll.dll")]  
   public static extern int SampleMethod(int x);  
  
   static void Main()   
   {  
      Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));  
   }  
}  
```  
  
## <a name="example"></a>Exemplo  
 3. Abra uma janela do Prompt de Comando de Ferramentas Nativas do Visual Studio x64 (ou x32) do diretório de instalação do Visual Studio e compile o arquivo `cm.cs` ao digitar:  
  
> **csc cm.cs** (para o prompt de comando x64)   
>  —ou—  
> **csc /platform:x86 cm.cs** (para o prompt de comando x32)  
  
 Isso criará o arquivo executável `cm.exe`.  
  
 4. Execute `cm.exe`. O método `SampleMethod` passa o valor 5 ao arquivo de DLL que retorna o valor multiplicado por 10.  O programa produz a seguinte saída:  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)
