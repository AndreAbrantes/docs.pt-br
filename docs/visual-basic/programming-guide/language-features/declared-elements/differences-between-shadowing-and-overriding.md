---
title: "Diferenças entre sombreamento e sobreposição (Visual Basic) | Documentos do Microsoft"
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
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: 24
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
ms.openlocfilehash: ff6e2a5ce61571d21e49230f58804bd37fdbdb26
ms.lasthandoff: 03/13/2017

---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Diferenças entre sombreamento e sobreposição (Visual Basic)
Quando você define uma classe que herda de uma classe base, às vezes você deseja redefinir uma ou mais dos elementos de classe base na classe derivada. Sombreamento e sobreposição estão disponíveis para essa finalidade.  
  
## <a name="comparison"></a>Comparação  
 Sombreamento e sobreposição forem usadas quando uma classe derivada herda de uma classe base, e os dois redefinem um elemento declarado com outro. Mas há diferenças significativas entre os dois.  
  
 A tabela a seguir compara sombreamento com substituição.  
  
||||  
|---|---|---|  
|Ponto de comparação|Sombreamento|Substituindo|  
|Finalidade|Protege contra uma modificação subsequente de classe base que introduz um membro que você já tenha definido em sua classe derivada|Permite polimorfismo através da definição de uma implementação de um procedimento ou propriedade com a mesma sequência de chamada<sup>1</sup>|  
|Elemento redefinido|Qualquer tipo de elemento declarado|Somente um procedimento (`Function`, `Sub`, ou `Operator`) ou propriedade|  
|Elemento redefinido|Qualquer tipo de elemento declarado|Somente um procedimento ou propriedade com a sequência de chamada idêntica<sup>1</sup>|  
|Nível de acesso do elemento redefinido|Qualquer nível de acesso|Não é possível alterar o nível de acesso de elemento substituído|  
|Legibilidade de gravabilidade do elemento redefinido|Qualquer combinação|Não é possível mudar a legibilidade ou gravabilidade de propriedades sobrescritas|  
|Controle da redefinição|Elemento de classe base não pode forçar ou proibir sombreamento|Elemento da classe base pode especificar `MustOverride`, `NotOverridable`, ou`Overridable`|  
|Uso da palavra-chave|`Shadows`recomendado na classe derivada; `Shadows` pressuposto se nenhum `Shadows` nem `Overrides` especificado<sup>2</sup>|`Overridable`ou `MustOverride` necessário na classe base; `Overrides` necessário na classe derivada|  
|Herança do elemento redefinido em classes derivadas da classe derivada|Elemento de sombreamento herdado por futuras classes derivadas; elemento sombreado ainda ocultado<sup>3</sup>|Substituir o elemento herdado por futuras classes derivadas; elemento sobrescrito ainda sobrescrito|  
  
 <sup>1</sup> o *sequência de chamada* consiste em tipo de elemento (`Function`, `Sub`, `Operator`, ou `Property`), nome, listas de parâmetros e tipo de retorno. Você não pode substituir um procedimento com uma propriedade, ou vice-versa. Você não pode substituir um tipo de procedimento (`Function`, `Sub`, ou `Operator`) com outro tipo.  
  
 <sup>2</sup> se você não especificar `Shadows` ou `Overrides`, o compilador emite uma mensagem de aviso para ajudá-lo a não se esqueça de que tipo de redefinição que você deseja usar. Se você ignorar o aviso, o mecanismo de sombreamento é usado.  
  
 <sup>3</sup> se o elemento sombreador é inacessível numa futura classe derivada, sombreamento não é herdado. Por exemplo, se você declarar o elemento sombreador como `Private`, uma classe que deriva da classe derivada herda ou elemento original em vez do elemento de sombreamento.  
  
## <a name="guidelines"></a>Diretrizes  
 Você normalmente usa substituindo nos seguintes casos:  
  
-   Você está definindo classes derivadas polimórficas.  
  
-   Você deseja a segurança de fazer o compilador forçar o mesmo tipo de elemento e sequência de chamada.  
  
 Você normalmente usa sombreamento nos seguintes casos:  
  
-   Você prevê que sua classe base pode ser modificada e define um elemento usando o mesmo nome que o seu.  
  
-   Você quer a liberdade de alterar o tipo de elemento ou sequência de chamada.  
  
## <a name="see-also"></a>Consulte também  
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [Como: ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [Como: acessar uma variável ocultada por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)
