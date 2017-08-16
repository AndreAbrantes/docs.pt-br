---
title: '&gt;&gt;Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>
dev_langs:
- VB
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators
- operator >>
- right shift operators
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
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
ms.openlocfilehash: df65a4ea15ec79e77bc8c1bd5c32ef03280c87c1
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;Operador (Visual Basic)
Executa um deslocamento aritmético à direita em um padrão de bit.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Valor numérico inteiro. O resultado do deslocamento do padrão de bits. O tipo de dados é o mesmo que `pattern`.  
  
 `pattern`  
 Necessário. Expressão numérica integral. O padrão de bits a ser deslocado. The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).  
  
 `amount`  
 Necessário. Expressão numérica. O número de bits para deslocar o padrão de bits. O tipo de dados deve ser `Integer` ou ampliar a `Integer`.  
  
## <a name="remarks"></a>Comentários  
 Deslocamentos aritméticos não são circulares, que significa que os bits deslocados de uma extremidade do resultado não são reconectados na outra extremidade. Em um deslocamento aritmético à direita, os bits deslocados além da posição mais à direita de bits são descartados, e o bit mais à esquerda (entrada) é propagado para as posições de bits vagas à esquerda. Isso significa que se `pattern` tem um valor negativo, as posições vagas são definidas como um; caso contrário, eles são definidos como zero.  
  
 Observe que os tipos de dados `Byte`, `UShort`, `UInteger`, e `ULong` são assinados e, portanto, não há nenhum bit de sinal para se propagar. Se `pattern` for de qualquer tipo não assinado, as posições vazias são sempre definidas como zero.  
  
 Para evitar um deslocamento de bits maior do que o resultado pode comportar, Visual Basic mascara o valor de `amount` com uma máscara de tamanho correspondente ao tipo de dados de `pattern`. O binário AND desses valores é usado para o valor de deslocamento. As máscaras de tamanho são da seguinte maneira:  
  
|Tipo de dados`pattern`|Máscara de tamanho (decimal)|Máscara de tamanho (hexadecimal)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&LT; / H00000007|  
|`Short`, `UShort`|15|&LT; / H0000000F|  
|`Integer`, `UInteger`|31|&LT; / H0000001F|  
|`Long`, `ULong`|63|&LT; / H0000003F|  
  
 Se `amount` for zero, o valor de `result` é idêntico ao valor de `pattern`. Se `amount` for negativo, ele é interpretado como um valor não assinado e mascarado com a máscara de tamanho apropriado.  
  
 Deslocamentos aritméticos nunca geram exceções de estouro.  
  
## <a name="overloading"></a>Sobrecarga  
 O `>>` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `>>` operador para executar deslocamentos aritméticos para a direita em valores integral. O resultado sempre tem os mesmos dados de tipo da expressão está sendo deslocada.  
  
 [!code-vb[VbVbalrOperators&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 Os resultados do exemplo anterior são os seguintes:  
  
-   `result1`é 2560 (0000 1010 0000 0000).  
  
-   `result2`é de 160 (0000 0000 1010 0000).  
  
-   `result3`é 2 (0000 0000 0000 0010).  
  
-   `result4`é 640 (0000 0010 1000 0000).  
  
-   `result5`é 0 (deslocadas 15 locais para a direita).  
  
 O valor de deslocamento para `result4` é calculado como 18 AND 15, que é igual a 2.  
  
 O exemplo a seguir mostra deslocamentos aritméticos em um valor negativo.  
  
 [!code-vb[VbVbalrOperators&#55;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 Os resultados do exemplo anterior são os seguintes:  
  
-   `negresult1`é -512 (1111 1110 0000 0000).  
  
-   `negresult2`é -1 (o bit de sinal é propagado).  
  
## <a name="see-also"></a>Consulte também  
 [Operadores bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [>> = Operador](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

