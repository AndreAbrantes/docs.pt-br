---
title: / Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
dev_langs:
- VB
helpviewer_keywords:
- division operator, floating point
- floating-point numbers, division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators, division
- division, by zero
- operators [Visual Basic], division
- division operator, syntax
- / operator [Visual Basic]
- math operators
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 71b4f64f6deeb334412c87131ccd9480620f284f
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>Operador / (Visual Basic)
Divide dois números e retorna um resultado de ponto flutuante.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>Partes  
 `expression1`  
 Necessário. Qualquer expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="supported-types"></a>Tipos com suporte  
 Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.  
  
## <a name="result"></a>Resultado  
 O resultado é o quociente total de `expression1` dividido por `expression2`, incluindo qualquer restante.  
  
 O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro, que ignora o resto.  
  
## <a name="remarks"></a>Comentários  
 O tipo de dados do resultado depende do tipo dos operandos. A tabela a seguir mostra como o tipo de dados do resultado é determinado.  
  
|Tipos de dados de operando|Tipo de dados de resultado|  
|------------------------|----------------------|  
|As duas expressões são tipos de dados integrais ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Uma expressão é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) tipo de dados e o outro não é um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Uma expressão é um [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) tipo de dados e o outro não é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) ou um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Uma das expressões é um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) tipo de dados|`Double`|  
  
 Antes de divisão, qualquer integrante expressões numéricas são ampliados para `Double`. Se você atribuir o resultado a um tipo de dados inteiros, Visual Basic tenta converter o resultado da `Double` para esse tipo. Isso pode gerar uma exceção se o resultado não couber nesse tipo. Em particular, consulte "Tentativa de divisão por Zero" nesta página de Ajuda.  
  
 Se `expression1` ou `expression2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.  
  
## <a name="attempted-division-by-zero"></a>Tentativa de divisão por Zero  
 Se `expression2` for avaliada como zero, o `/` operador se comporta de forma diferente para operando diferentes tipos de dados. A tabela a seguir mostra os comportamentos possíveis.  
  
|Tipos de dados de operando|Comportamento se `expression2` é zero|  
|------------------------|---------------------------------------|  
|Ponto flutuante (`Single` ou `Double`)|Retorna infinito (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>), ou <xref:System.Double.NaN>(não um número) se `expression1` também é zero</xref:System.Double.NaN> </xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity>|  
|`Decimal`|Lança<xref:System.DivideByZeroException></xref:System.DivideByZeroException>|  
|Integral (assinados ou não assinados)|Tentativa de conversão de volta para tipo integral gera <xref:System.OverflowException>porque tipos integrais não podem aceitar <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, ou <xref:System.Double.NaN></xref:System.Double.NaN> </xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity> </xref:System.OverflowException>|  
  
> [!NOTE]
>  O `/` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `/` operador para realizar a divisão de ponto flutuante. O resultado é o quociente de dois operandos.  
  
 [!code-vb[VbVbalrOperators n º&16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 As expressões no exemplo anterior retornam valores de 2.5 and 3.333333. Observe que o resultado é sempre um ponto flutuante (`Double`), embora ambos os operandos são constantes de inteiro.  
  
## <a name="see-also"></a>Consulte também  
 [Operador / = (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [Tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)   
 [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

