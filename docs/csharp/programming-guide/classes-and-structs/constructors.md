---
title: "Construtores (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2017-05-05
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: 23
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
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 064d8f8b3068596cd1d4fc2dd073f165f0ebadcb
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="constructors-c-programming-guide"></a>Construtores (Guia de Programação em C#)
Sempre que uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) é criada, o construtor é chamado. Uma classe ou struct pode ter vários construtores que usam argumentos diferentes. Os construtores permitem que o programador defina valores padrão, limite a instanciação e grave códigos flexíveis e fáceis de ler. Para obter mais informações e exemplos, consulte [Usando Construtores](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) e [Construtores de Instância](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="default-constructors"></a>Construtores padrão
  
Se um construtor não for fornecido para a classe, o C# criará por padrão um construtor que instancia o objeto e define variáveis de membro para os valores padrão, conforme listado na [Tabela de Valores Padrão](../../../csharp/language-reference/keywords/default-values-table.md). Se você não fornecer um construtor para o struct, o C# responderá em um *construtor padrão implícito* para inicializar automaticamente a cada campo de um tipo de valor para o valor padrão conforme listado na [Tabela de Valores Padrão](../../../csharp/language-reference/keywords/default-values-table.md). Para obter mais informações e exemplos, consulte [Construtores de Instância](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="constructor-syntax"></a>Sintaxe do construtor

Um construtor é um método cujo nome é igual ao nome de seu tipo. Sua assinatura do método inclui apenas o nome do método e lista de parâmetros, ele não inclui um tipo de retorno. O exemplo a seguir mostra o construtor para uma classe denominada `Person`.

[!code-cs[construtores](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Se um construtor puder ser implementado como uma única instrução, você poderá usar uma [definição de corpo da expressão](../statements-expressions-operators/expression-bodied-members.md). O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*. A definição de corpo da expressão atribui o argumento à propriedade `Name`.

[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Construtores estáticos

Os exemplos anteriores têm todos os construtores de instância mostrado, que criam um novo objeto. Uma classe ou struct também pode ter um construtor estático, que inicializa membros estáticos do tipo.  Construtores estáticos não têm parâmetros. Se você não fornecer um construtor estático para inicializar campos estáticos, o compilador do C# fornecerá um construtor estático padrão que inicializa os campos com seus valores padrão, conforme listado na [Tabela de Valores Padrão](../../../csharp/language-reference/keywords/default-values-table.md). 

O exemplo a seguir usa um construtor estático para inicializar um campo estático.

[!code-cs[construtores](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Você também pode definir um construtor estático com uma definição de corpo da expressão, como mostra o exemplo a seguir. 

[!code-cs[construtores](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Para obter mais informações e exemplos, consulte [Construtores Estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Usando construtores](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [Construtores de instância](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [Construtores particulares](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [Construtores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [Como escrever um construtor de cópia](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [static](../../../csharp/language-reference/keywords/static.md)   
 [Por que os inicializadores são executados na ordem oposta, como construtores? Parte 1](http://go.microsoft.com/fwlink/?LinkId=112374)
