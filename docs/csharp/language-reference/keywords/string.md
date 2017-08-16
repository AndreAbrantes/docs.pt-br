---
title: "string (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 737a0902a0cb010a74b59560abe43f5cfb6550db
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="string-c-reference"></a>string (Referência de C#)
O tipo `string` representa uma sequência de zero ou mais caracteres Unicode. `string` é um alias para <xref:System.String> no .NET Framework.  
  
 Embora `string` seja um tipo de referência, os operadores de igualdade (`==` e `!=`) são definidos para comparar os valores dos objetos `string`, não referências. Isso torna o teste de igualdade de cadeia de caracteres mais intuitivo. Por exemplo:  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 Isso exibe "True" e, em seguida, "False" porque os conteúdos das cadeias de caracteres são equivalentes, mas `a` e `b` não fazem referência à mesma instância da cadeia de caracteres.  
  
 O operador + concatena as cadeias de caracteres:  
  
```csharp  
string a = "good " + "morning";  
```  
  
 Isso cria um objeto de cadeia de caracteres que contém “good morning”.  
  
 Cadeias de caracteres são *imutável* – o conteúdo de um objeto de cadeia de caracteres não pode ser alterado depois que o objeto é criado, embora a sintaxe faça com que pareça que você pode fazer isso. Por exemplo, quando você escreve esse código, o compilador na verdade cria um novo objeto de cadeia de caracteres para manter a nova sequência de caracteres e esse novo objeto é atribuído a b. A cadeia de caracteres "h" é então qualificada para coleta de lixo.  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 O operador [] pode ser usado para o acesso somente leitura a caracteres individuais de uma `string`:  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 Literais de cadeia de caracteres são do tipo `string` e podem ser escritos de duas formas, entre aspas e @-quoted. Os literais de cadeia de caracteres entre aspas são colocados entre aspas duplas ("):  
  
```csharp  
"good morning"  // a string literal  
```  
  
 Os literais de cadeia de caracteres podem conter qualquer literal de caractere. Sequências de escape são incluídas. O exemplo a seguir usa a sequência de escape `\\` de barra invertida, `\u0066` para a letra f e `\n` para a nova linha.  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  O código de escape `\`u`dddd` (em que `dddd` é um número de quatro dígitos) representa o caractere Unicode U+`dddd`. Os códigos de escape Unicode de oito dígitos também são reconhecidos: `\Udddddddd`.  
  
 Os literais de cadeias de caracteres textuais começam com @ e também são colocados entre aspas duplas. Por exemplo:  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 A vantagem das cadeias de caracteres textuais é que as sequências de escape *não* são processadas, o que torna mais fácil escrever, por exemplo, um nome de arquivo totalmente qualificado:  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 Para incluir aspas duplas em uma cadeia de caracteres @-quoted, dobre-a:  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 Outro uso do símbolo @ é usar identificadores ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) referenciados que são palavras-chave C#.  
  
 Para obter mais informações sobre cadeias de caracteres, consulte [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md).  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Práticas recomendadas para o uso de cadeias de caracteres](../../../standard/base-types/best-practices-strings.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Tipos de Referência](../../../csharp/language-reference/keywords/reference-types.md)   
 [Tipos de Valor](../../../csharp/language-reference/keywords/value-types.md)   
 [Operações básicas de cadeias de caracteres](../../../standard/base-types/basic-string-operations.md)   
 [Criando novas cadeias de caracteres](../../../standard/base-types/creating-new.md)   
 [Tabela de formatação de resultados numéricos](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)

