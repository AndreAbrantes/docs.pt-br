---
title: "Expansão (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.widening
dev_langs:
- VB
helpviewer_keywords:
- conversions, type
- type conversion
- conversions, data type
- Widening keyword
- data type conversion
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 49e49f91361f5a946f24796a2c05ef946350266e
ms.lasthandoff: 03/13/2017

---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
Indica que um operador de conversão (`CType`) converte uma classe ou estrutura para um tipo que pode conter todos os possíveis valores da classe ou estrutura original.  
  
## <a name="converting-with-the-widening-keyword"></a>Convertendo com a palavra-chave Widening  
 O procedimento de conversão deve especificar `Public Shared` além `Widening`.  
  
 Conversões de ampliação sempre são bem-sucedidas em tempo de execução e nunca provocam perda de dados. Os exemplos são `Single` para `Double`, `Char` para `String`e um tipo derivado para seu tipo base. Essa última conversão está ampliando porque o tipo derivado contém todos os membros do tipo base e, portanto, é uma instância do tipo base.  
  
 O código consumidor não precisa usar `CType` para ampliação conversões, mesmo se `Option Strict` é `On`.  
  
 O `Widening` palavra-chave pode ser usada neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Por exemplo, definições de widening e narrowing operadores de conversão, consulte [como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
