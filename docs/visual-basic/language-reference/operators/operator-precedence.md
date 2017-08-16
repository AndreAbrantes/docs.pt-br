---
title: "Precedência do operador no Visual Basic | Documentos do Microsoft"
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
- arithmetic operators, precedence
- operator precedence
- logical operators, precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators
- operators [Visual Basic], precedence
- precedence, of operators
- comparison operators, precedence
- math operators
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6532fc0c26db3b736c863be075571570a3d25eef
ms.lasthandoff: 03/13/2017

---
# <a name="operator-precedence-in-visual-basic"></a>Precedência do operador no Visual Basic
Quando várias operações ocorrem em uma expressão, cada parte é avaliado e resolvido em uma ordem predeterminada chamada *precedência do operador*.  
  
## <a name="precedence-rules"></a>Regras de precedência  
 Quando as expressões contêm operadores de mais de uma categoria, eles são avaliados de acordo com as regras a seguir:  
  
-   Os operadores aritméticos e concatenação têm a ordem de precedência descrita na seção a seguir, e todas têm precedência maior do que a comparação, lógicos e operadores bit a bit.  
  
-   Todos os operadores de comparação têm a mesma precedência e todas têm precedência maior do que os operadores lógicos e bit a bit, mas menor precedência que os operadores aritméticos e concatenação.  
  
-   Os operadores lógicos e bit a bit que a ordem de precedência descrita na seção a seguir, e todas têm precedência menor que a aritmética, concatenação e operadores de comparação.  
  
-   Operadores com a mesma precedência são avaliados da esquerda para a direita na ordem em que aparecem na expressão.  
  
## <a name="precedence-order"></a>Ordem de precedência  
 Operadores são avaliados na seguinte ordem de precedência:  
  
### <a name="await-operator"></a>Operador Await  
 À espera  
  
### <a name="arithmetic-and-concatenation-operators"></a>Aritmética e operadores de concatenação  
 Exponenciação (`^`)  
  
 Unários identidade e negação (`+`, `–`)  
  
 Multiplicação e divisão de ponto flutuante (`*`, `/`)  
  
 Divisão de inteiros (`\`)  
  
 Módulo aritmético (`Mod`)  
  
 Adição e subtração (`+`, `–`)  
  
 Concatenação de cadeia de caracteres (`&`)  
  
 Aritmética bit shift (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Operadores de comparação  
 All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Operadores lógicos e bit a bit  
 Negação (`Not`)  
  
 Conjunto (`And`, `AndAlso`)  
  
 Disjunção (`Or`, `OrElse`)  
  
 Disjunção (`Xor`)  
  
### <a name="comments"></a>Comentários  
 O `=` operador é apenas o igualdade operador de comparação, não o operador de atribuição.  
  
 O operador de concatenação de cadeia de caracteres (`&`) não é um operador aritmético, mas na prioridade é agrupado com os operadores aritméticos.  
  
 O `Is` e `IsNot` operadores são operadores de comparação de referência de objeto. Eles não são os valores dos dois objetos. eles verifique apenas para determinar se duas variáveis de objeto se referem à mesma instância de objeto.  
  
## <a name="associativity"></a>Associatividade  
 Quando operadores de precedência igual aparecem juntos em uma expressão, por exemplo, multiplicação e divisão, o compilador avalia cada operação conforme ele encontra da esquerda para a direita. O exemplo a seguir ilustra essa situação.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 A primeira expressão é avaliada a divisão 96 / 8 (o que resulta em 12) e, em seguida, a divisão de 12 / 4, o que resulta em três. Porque o compilador avalia as operações `n1` da esquerda para a direita, a avaliação é o mesmo quando a ordem é explicitamente indicada para `n2`. Ambos `n1` e `n2` tem um resultado de três. Por outro lado, `n3` possui um resultado de 48, porque os parênteses forçam o compilador para avaliar 8 / 4 primeiro.  
  
 Devido a esse comportamento, operadores são considerados *permanecem associativos* em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="overriding-precedence-and-associativity"></a>Substituição de precedência e associatividade  
 Você pode usar parênteses para forçar algumas partes de uma expressão a ser avaliada antes de outros. Isso pode substituir a ordem de precedência e a associatividade à esquerda. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]sempre executa operações que estão entre parênteses antes de fora. No entanto, dentro dos parênteses, ele mantém comum precedência e associatividade, a menos que você use parênteses dentro dos parênteses. O exemplo a seguir ilustra essa situação.  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>Consulte também  
 [= Operador](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Operador is](../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Operador LIKE](../../../visual-basic/language-reference/operators/like-operator.md)   
 [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Operador await](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
