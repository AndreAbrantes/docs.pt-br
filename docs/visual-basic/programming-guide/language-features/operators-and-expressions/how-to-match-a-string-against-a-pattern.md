---
title: "Como: corresponder uma cadeia de caracteres com um padrão (Visual Basic) | Documentos do Microsoft"
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
- comparison operators, comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching, string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
caps.latest.revision: 8
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
ms.openlocfilehash: 317cb2f2a92b4c79dd321819a0f986ab852afff6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Como corresponder uma cadeia de caracteres a um padrão (Visual Basic)
Se você quiser saber se uma expressão do [tipo de dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfaz um padrão, você pode usar o [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like`leva dois operandos. O operando esquerdo é uma expressão de cadeia de caracteres, e o operando à direita é uma cadeia de caracteres contendo o padrão a ser usado para correspondência. `Like`Retorna um `Boolean` valor que indica se a expressão de cadeia de caracteres satisfaz o padrão.  
  
 Você pode corresponder a cada caractere na expressão de cadeia de caracteres com um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres. As posições das especificações na cadeia de caracteres padrão correspondem às posições dos caracteres a ser correspondida na expressão de cadeia de caracteres.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Para corresponder um caractere na expressão de cadeia de caracteres com um caractere específico  
  
-   Coloque o caractere específico diretamente na cadeia de caracteres padrão. Certos caracteres especiais devem ser colocados entre colchetes (`[ ]`). Para obter mais informações, consulte [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     A exemplo a seguir testa se `myString` consiste exatamente do único caractere `H`.  
  
     [!code-vb[VbVbalrOperators&#70;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Para corresponder um caractere na expressão de cadeia de caracteres com um caractere curinga  
  
-   Coloque um ponto de interrogação (`?`) na cadeia de caracteres padrão. Qualquer caractere válido nessa posição é uma correspondência com êxito.  
  
     A exemplo a seguir testa se `myString` consiste no caractere único `W` seguido por exatamente dois caracteres de quaisquer valores.  
  
     [!code-vb[VbVbalrOperators&#71;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Para corresponder um caractere na expressão de cadeia de caracteres em uma lista de caracteres  
  
-   Coloque colchetes (`[ ]`) na cadeia de caracteres padrão e dentro dos colchetes coloque a lista de caracteres. Não separe os caracteres com vírgulas ou qualquer outro separador. Qualquer caractere único na lista é uma correspondência com êxito.  
  
     A exemplo a seguir testa se `myString` consiste de qualquer caractere válido seguido por exatamente um dos caracteres `A`, `C`, ou `E`.  
  
     [!code-vb[VbVbalrOperators&#72;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     Observe que essa correspondência diferencia maiusculas de minúsculas.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Para corresponder um caractere na expressão de cadeia de caracteres com um intervalo de caracteres  
  
-   Coloque colchetes (`[ ]`) na cadeia de caracteres padrão e dentro dos colchetes colocados os caracteres mais baixos e mais altos do intervalo, separados por um hífen (`–`). Qualquer caractere único dentro do intervalo é uma correspondência com êxito.  
  
     A exemplo a seguir testa se `myString` consiste em caracteres `num` seguidos por exatamente um dos caracteres `i`, `j`, `k`, `l`, `m`, ou `n`.  
  
     [!code-vb[VbVbalrOperators&#73;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     Observe que essa correspondência diferencia maiusculas de minúsculas.  
  
## <a name="matching-empty-strings"></a>Correspondência de cadeias de caracteres vazias  
 `Like`trata a sequência `[]` como uma cadeia de caracteres de comprimento zero (`""`). Você pode usar `[]` para testar se a expressão de cadeia de caracteres inteira está vazia, mas você não pode usá-lo para testar se uma determinada posição na expressão de cadeia de caracteres está vazia. Se uma posição vazia é uma das opções que você precisa testar, você pode usar `Like` mais de uma vez.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Para corresponder um caractere na expressão de cadeia de caracteres em uma lista de caracteres ou nenhum caractere  
  
1.  Chamar o `Like` operador duas vezes na mesma expressão de cadeia de caracteres e conecte as duas chamadas com o [operador ou](../../../../visual-basic/language-reference/operators/or-operator.md) ou [operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  Na cadeia de caracteres padrão para o primeiro `Like` cláusula, inclua a lista de caracteres entre colchetes (`[ ]`).  
  
3.  Na cadeia de caracteres padrão para o segundo `Like` cláusula, não coloque nenhum caractere na posição em questão.  
  
     O exemplo a seguir testa o número de telefone de sete dígitos `phoneNum` exatamente três dígitos numéricos, seguidos por um espaço, um hífen (`–`), um período (`.`), ou nenhum caractere, seguidos por exatamente quatro dígitos numéricos.  
  
     [!code-vb[VbVbalrOperators&#74;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operadores de comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operadores e expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Operador LIKE](../../../../visual-basic/language-reference/operators/like-operator.md)   
 [Tipo de Dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)
