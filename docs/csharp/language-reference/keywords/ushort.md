---
title: "ushort (Referência de C#) | Microsoft Docs"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ushort
- ushort_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 16
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
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 20d3c1e9b10df0d1fff96fa3e56e6a81c4663f51
ms.contentlocale: pt-br
ms.lasthandoff: 03/24/2017

---
# <a name="ushort-c-reference"></a>ushort (Referência de C#)

A palavra-chave `ushort` indica um tipo de dados integrais que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo do .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`ushort`|0 a 65.535|Inteiro de 16 bits sem sinal|<xref:System.UInt16?displayProperty=fullName>|  
  
## <a name="literals"></a>Literais  

Você pode declarar e inicializar uma variável `ushort` atribuindo um literal decimal, um literal hexadecimal ou (começando com C# 7) um literal binário a ela. Se o literal inteiro estiver fora do intervalo de `ushort` (ou seja, se ele for menor que <xref:System.UInt16.MinValue?displayProperty=fullName> ou maior que <xref:System.UInt16.MaxValue?displayProperty=fullName>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 65.034 representados como literais decimais, hexadecimais e binários são implicitamente convertidos de valores [int](../../../csharp/language-reference/keywords/int.md) para `ushort`.    
  
[!code-cs[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo.

Começando com o C# 7, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-cs[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a>Resolução de sobrecarga do compilador
  
 Uma conversão deve ser usada ao chamar métodos sobrecarregados. Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `ushort` e [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 O uso da conversão `ushort` garante que o tipo correto será chamado, por exemplo:  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `ushort` para [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Há uma conversão implícita predefinida de [byte](../../../csharp/language-reference/keywords/byte.md) ou [char](../../../csharp/language-reference/keywords/char.md) para `ushort`. Caso contrário, uma conversão deve ser usada para executar uma conversão explícita. Considere, por exemplo, as duas variáveis `ushort` `x` e `y` a seguir:  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como `int` por padrão.  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 Para corrigir esse problema, use uma conversão:  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 No entanto, é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 Observe também que não há conversão implícita de tipos de ponto flutuante em `ushort`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.UInt16>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
