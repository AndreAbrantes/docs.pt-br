---
title: "Tipos de dados numéricos (Visual Basic) | Documentos do Microsoft"
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
- integral types, Visual Basic
- Short data type, numeric data types
- Double data type, numeric data types
- Long data type, Visual Basic numeric data types
- numbers, whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers, integer
- fractional data types
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type, numeric data types
- exponent, of fractional numbers
- integers
- numeric data types, Visual Basic
- Single data type, numeric types
- Decimal data type, numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3c3098370b8d9dcb6aafcb06dcfb8f4e144b899a
ms.lasthandoff: 03/13/2017

---
# <a name="numeric-data-types-visual-basic"></a>Tipos de dados numéricos (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece vários *tipos de dados numéricos* para tratar números em diversas representações. *Integral* tipos representam apenas números inteiros (positivo, negativo e zero), e *nonintegral* tipos representam números com partes inteira e fracionárias.  
  
 Para uma tabela que mostre uma comparação lado a lado do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="integral-numeric-types"></a>Tipos numéricos integrais  
 *Tipos de dados integrais* são aqueles que representam apenas números sem partes fracionárias.  
  
 O *assinado* são tipos de dados integrais [tipo de dados SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8 bits) [tipo de dados Short](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16 bits) [tipo de dados inteiro](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32 bits) e [tipo de dados Long](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64 bits). Se uma variável sempre armazena números inteiros em vez de números fracionários, declare-a como um desses tipos.  
  
 O *sem sinal* tipos integrais são [tipo de dados Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8 bits) [tipo de dados UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16 bits) [tipo de dados UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32 bits) e [tipo de dados ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64 bits). Se uma variável contiver dados binários, ou natureza desconhecida, declare-a como um desses tipos.  
  
### <a name="performance"></a>Desempenho  
 Operações aritméticas são mais rápidas com tipos integrais do que com outros tipos de dados. Eles são mais rápidos com o `Integer` e `UInteger` tipos [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### <a name="large-integers"></a>Inteiros grandes  
 Se você precisar armazenar um número inteiro maior do que o `Integer` tipo de dados pode armazenar, você pode usar o `Long` tipo de dados. `Long`variáveis podem conter números de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807. Operações com `Long` são um pouco mais lentas do que com `Integer`.  
  
 Se você precisar de valores ainda maiores, você pode usar o [tipo de dados Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Você pode armazenar números de-79.228.162.514.264.337.593.543.950.335 até 79.228.162.514.264.337.593.543.950.335 em um `Decimal` variável se você não usar casas decimais. No entanto, operações com `Decimal` números são consideravelmente mais lentos do que com qualquer outro tipo de dados numéricos.  
  
### <a name="small-integers"></a>Inteiros pequenos  
 Se você não precisar de toda a gama do `Integer` tipo de dados, você pode usar o `Short` tipo de dados que pode conter números inteiros de -32.768 a 32.767. Para o menor intervalo inteiro, o `SByte` tipo de dados armazena inteiros de -128 a 127. Se você tiver um grande número de variáveis que armazenam números inteiros pequenos, o common language runtime, às vezes, pode armazenar seu `Short` e `SByte` variáveis de forma mais eficiente e economizar memória. No entanto, operações com `Short` e `SByte` são um pouco mais lentas do que com `Integer`.  
  
### <a name="unsigned-integers"></a>Inteiros sem sinal  
 Se você souber que sua variável nunca precisará armazenar um número negativo, você pode usar o *tipos sem sinal*`Byte`, `UShort`, `UInteger`, e `ULong`. Cada um desses tipos de dados pode conter um número inteiro positivo duas vezes tão grande quanto o tipo com sinal correspondente (`SByte`, `Short`, `Integer`, e `Long`). Em termos de desempenho, cada tipo sem sinal é tão eficiente quanto seu tipo com sinal correspondente. Em particular, `UInteger` compartilha com `Integer` a distinção de ser o mais eficiente de todos os tipos de dados numérico elementar.  
  
## <a name="nonintegral-numeric-types"></a>Tipos numéricos não integral  
 *Tipos de dados não integral* são aqueles que representam números com partes inteira e fracionárias.  
  
 Os tipos de dados numérico não integral são `Decimal` (128 bits fixo ponto), [único tipo de dados](../../../../visual-basic/language-reference/data-types/single-data-type.md) (ponto flutuante de&32; bits), e [tipo de dados Double](../../../../visual-basic/language-reference/data-types/double-data-type.md) (ponto flutuante de&64; bits). Eles são tipos tudo assinados. Se uma variável pode conter uma fração, declare-a como um desses tipos.  
  
 `Decimal`não é um tipo de dados de ponto flutuante. `Decimal`números têm um valor inteiro binário e um fator de escala inteiro que especifica qual parte do valor é uma fração decimal.  
  
 Você pode usar `Decimal` variáveis para valores monetários. A vantagem é a precisão dos valores. O `Double` tipo de dados é mais rápido e requer menos memória, mas ela está sujeita a erros de arredondamento. O `Decimal` tipo de dados retém precisão completa para 28 casas decimais.  
  
 Ponto flutuante (`Single` e `Double`) números têm intervalos maiores do que `Decimal` números, mas podem estar sujeitos a erros de arredondamento. Tipos de ponto flutuantes suportam menos dígitos significativos que `Decimal` mas podem representar valores de magnitude maior.  
  
 Valores numéricos não integral podem ser expresso como mmmEeee, em que é mmm o *mantissa* (os dígitos significativos) e eee é o *expoente* (uma potência de 10). Os valores positivos mais altos dos tipos não integral são 7.9228162514264337593543950335 e + 28 para `Decimal`, 3, 4028235E + 38 para `Single`, e 1.79769313486231570 e + 308 para `Double`.  
  
### <a name="performance"></a>Desempenho  
 `Double`é o mais eficiente de tipos de dados fracionários, porque os processadores em plataformas atuais executam operações de ponto flutuante de precisão dupla. No entanto, operações com `Double` não são tão rápidas como com os tipos integrais como `Integer`.  
  
### <a name="small-magnitudes"></a>Magnitudes pequenas  
 Para números com o menor magnitude possível (próximo a 0), `Double` variáveis podem conter números tão pequenos quanto - 4.94065645841246544 e-324 para valores negativos e 4.94065645841246544 e -324 para valores positivos.  
  
### <a name="small-fractional-numbers"></a>Números fracionários pequenos  
 Se você não precisar de toda a gama do `Double` tipo de dados, você pode usar o `Single` tipo de dados, que pode conter números de ponto flutuante de - 3, 4028235E + 38 a 3, 4028235E + 38. Os menores magnitudes para `Single` variáveis são - 1, 401298E-45 para valores negativos e 1, 401298E-45 para valores positivos. Se você tiver um grande número de variáveis que armazenam números de ponto flutuantes pequenos, o common language runtime, às vezes, pode armazenar seu `Single` variáveis de forma mais eficiente e economizar memória.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados de caractere](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Diversos tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Como chamar uma função do Windows que use tipos não assinados](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
