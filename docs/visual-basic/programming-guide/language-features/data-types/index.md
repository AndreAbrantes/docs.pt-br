---
title: Tipos de dados no Visual Basic
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
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8b90a5e58d135a3769761ca431fd0c05f79e045f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="data-types-in-visual-basic"></a>Tipos de dados no Visual Basic
O *tipo de dados* de um elemento de programação se refere a que tipo de dados ele pode armazenar e como ele armazena esses dados. Os tipos de dados se aplicam a todos os valores que podem ser armazenados na memória do computador ou participam da avaliação de uma expressão. Cada variável, literal, constante, enumeração, propriedade, parâmetro de procedimento, argumento de procedimento e valor retornado do procedimento tem um tipo de dados.  
  
## <a name="declared-data-types"></a>Tipos de dados declarados  
 Você define um elemento de programação com uma instrução de declaração, e você especifica o tipo de dados com a cláusula `As`. A tabela a seguir mostra as instruções que você usa para declarar vários elementos.  
  
|Elemento de programação|Declaração de tipo de dados|  
|-------------------------|---------------------------|  
|Variável|Em uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literal|Com um caractere de tipo literal. Consulte "Caracteres de tipo Literal" em [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Constante|Em uma [instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Enumeração|Em uma [instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Propriedade|Em uma [instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parâmetro de procedimento|Em uma [instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md), [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) ou [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argumento de procedimento|No código de chamada. Cada argumento é um elemento de programação que já foi declarado ou uma expressão que contém elementos declarados<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Valor retornado do procedimento|Em uma [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) ou [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Para obter uma lista dos tipos de dados do Visual Basic, consulte [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="see-also"></a>Consulte também  
 [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Tuplas](tuples.md)     
 [Solução de problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Uso Eficiente de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

