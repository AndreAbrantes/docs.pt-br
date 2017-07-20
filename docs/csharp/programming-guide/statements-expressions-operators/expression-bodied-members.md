---
title: "Membros aptos para expressão (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: b77f656d36dc4f0a715755e13bfcd6c3515c697b
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="expression-bodied-members-c-programming-guide"></a>Membros aptos para expressão (Guia de Programação em C#)
As definições de corpo da expressão permitem que você forneça uma implementação de um membro em uma forma bastante concisa e legível. Você pode usar uma definição de corpo da expressão sempre que a lógica para qualquer membro com suporte, como um método ou propriedade, consiste em uma única expressão. Uma definição de corpo da expressão tem a seguinte sintaxe geral:

```csharp
member => expression;
```

em que *expression* é uma expressão válida. 

O suporte para definições de corpo da expressão foi introduzido para acessadores get da propriedade e de métodos no C# 6 e foi expandido no C# 7. As definições de corpo da expressão podem ser usadas com os membros de tipo listados na tabela a seguir: 

|Membro  |Com suporte desde... |
|---------|---------|
|[Método](#methods)  |C# 6 |
|[Construtor](#constructors)   |C# 7 |
|[Finalizador](#finalizers)     |C# 7 |
|[Get da propriedade](#property-get-statements)  |C# 6 |
|[Set da propriedade](#property-set-statements)  |C# 7 |
|[Indexador](#indexers)       |C# 7 |

## <a name="methods"></a>Métodos

Um método apto para expressão consiste em uma única expressão que retorna um valor cujo tipo corresponde ao tipo de retorno do método, ou, para métodos que retornam `void`, que executam uma operação. Por exemplo, os tipos que substituem o método <xref:System.Object.ToString%2A> normalmente incluem uma única expressão que retorna a representação da cadeia de caracteres do objeto atual. 

O exemplo a seguir define uma classe `Person` que substitui o método <xref:System.Object.ToString%2A> por uma definição de corpo da expressão. Ele também define um método `Show` que exibe um nome para o console. Observe que a palavra-chave `return` não é usada na definição de corpo da expressão `ToString`.

[!code-cs[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Para obter mais informações, consulte [Métodos (Guia de Programação em C#)](../classes-and-structs/methods.md).
 
## <a name="constructors"></a>Construtores

Uma definição de corpo da expressão para um construtor normalmente consiste em uma expressão de atribuição simples ou uma chamada de método que manipula os argumentos do construtor ou inicializa o estado da instância. 

O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*. A definição de corpo da expressão atribui o argumento à propriedade `Name`.

[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Para obter mais informações, consulte [Construtores (Guia de Programação em C#)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizadores

Uma definição de corpo da expressão para um finalizador normalmente contém instruções de limpeza, como instruções que liberam recursos não gerenciados.

O exemplo a seguir define um finalizador que usa uma definição de corpo da expressão para indicar que o finalizador foi chamado.

[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Para obter mais informações, consulte [Finalizadores (Guia de Programação em C#)](../classes-and-structs/destructors.md).

## <a name="property-get-statements"></a>Instruções get da propriedade

Se você optar por implementar um acessador get da propriedade por conta própria, poderá usar uma definição de corpo da expressão para expressões únicas que retornam simplesmente o valor da propriedade. Observe que a instrução `return` não é usada.

O exemplo a seguir define uma propriedade `Location.Name` cujo acessador get da propriedade retorna o valor do campo `locationName` particular que sustenta a propriedade. 

[!code-cs[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

As propriedades somente leitura que usam uma definição de corpo da expressão podem ser implementadas sem uma instrução `set` explícita. A sintaxe é:

```csharp
PropertyName => returnValue;
```

O exemplo a seguir define uma classe `Location` cuja propriedade `Name` somente leitura é implementada como uma definição de corpo da expressão que retorna o valor do campo `locationName` particular.

[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Para obter mais informações, consulte [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).

## <a name="property-set-statements"></a>Instruções set da propriedade

Se você optar por implementar um acessador set da propriedade por conta própria, poderá usar uma definição de corpo da expressão para uma expressão de linha única que atribui um valor ao campo que sustenta a propriedade.

O exemplo a seguir define uma propriedade `Location.Name` cujo acessador set da propriedade designa seu argumento de entrada ao campo `locationName` particular que sustenta a propriedade.

[!code-cs[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Para obter mais informações, consulte [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).

## <a name="indexers"></a>Indexadores

Como as propriedades, os acessadores get e set do indexador consistirão em definições de corpo da expressão se o acessador get consistir em uma única instrução que retorna um valor ou o acessador set executar uma designação simples.

O exemplo a seguir define uma classe chamada `Sports` que inclui uma matriz <xref:System.String> interna que contém os nomes de vários esportes. Os acessadores get e set do indexador são implementados como definições de corpo da expressão.

[!code-cs[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

Para obter mais informações, consulte [Indexadores (Guia de Programação em C#)](../indexers/index.md).


