---
title: struct – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 74e9909fda83c781b5a15727f79ff755e7682b0f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963119"
---
# <a name="struct-c-reference"></a>struct (Referência de C#)

O tipo `struct` é um tipo de valor normalmente usado para encapsular pequenos grupos de variáveis relacionadas, tais como coordenadas de um retângulo ou as características de um item em um inventário. O seguinte exemplo mostra uma declaração simples de struct:

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Comentários

Os structs também podem conter [construtores](../../programming-guide/classes-and-structs/constructors.md), [constantes](../../programming-guide/classes-and-structs/constants.md), [campos](../../programming-guide/classes-and-structs/fields.md), [métodos](../../programming-guide/classes-and-structs/methods.md), [propriedades](../../programming-guide/classes-and-structs/properties.md), [indexadores](../../programming-guide/indexers/index.md), [operadores](../operators/index.md), [eventos](../../programming-guide/events/index.md) e [tipos aninhados](../../programming-guide/classes-and-structs/nested-types.md), embora, se vários desses membros forem necessários, você deva considerar tonar seu tipo uma classe.

Para obter exemplos, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).

Os structs podem implantar uma interface, mas não podem herdá-la de outra struct. Por esse motivo, os membros de struct não podem ser declarados como `protected`.

Para obter mais informações, consulte [Structs](../../programming-guide/classes-and-structs/structs.md).

## <a name="examples"></a>Exemplos

Para obter exemplos e mais informações, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter exemplos, consulte [Usando structs](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="see-also"></a>Veja também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tabela de tipos internos](built-in-types-table.md)
- [Tipos](/dotnet/csharp/language-reference/keywords)
- [Tipos de valor](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Classes e Structs](../../programming-guide/classes-and-structs/index.md)
