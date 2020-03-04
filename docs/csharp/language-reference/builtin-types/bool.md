---
title: referência de C# tipo bool
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 0e01c183ef07c23203619e0cbbf550c6268bdd46
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239827"
---
# <a name="bool-c-reference"></a>bool (C# referência)

A palavra-chave Type de `bool` é um alias para o tipo de estrutura .NET <xref:System.Boolean?displayProperty=nameWithType> que representa um valor booliano, que pode ser `true` ou `false`.

Para executar operações lógicas com valores do tipo `bool`, use operadores [lógicos boolianos](../operators/boolean-logical-operators.md) . O tipo de `bool` é o tipo de resultado de operadores de [comparação](../operators/comparison-operators.md) e de [igualdade](../operators/equality-operators.md) . Uma expressão de `bool` pode ser uma expressão condicional de controle nas instruções [If](../keywords/if-else.md) [, do,](../keywords/do.md) [while](../keywords/while.md)e [for](../keywords/for.md) e no [operador condicional `?:`](../operators/conditional-operator.md).

O valor padrão do tipo de `bool` é `false`.

## <a name="literals"></a>Literais

Você pode usar os literais `true` e `false` para inicializar uma variável `bool` ou para passar um valor de `bool`:

[!code-csharp-interactive[bool literals](~/samples/snippets/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Lógica booleana de três valores

Use o tipo de `bool?` anulável, se você precisar dar suporte à lógica de três valores, por exemplo, ao trabalhar com bancos de dados que dão suporte a um tipo booliano de três valores. Para os operandos `bool?`, os operadores `&` e `|` predefinidos oferecem suporte à lógica de três valores. Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).

Para obter mais informações sobre tipos de valor anulável, consulte [tipos de valor anulável](nullable-value-types.md).

## <a name="conversions"></a>Conversões

C#fornece apenas duas conversões que envolvem o tipo de `bool`. Essas são uma conversão implícita para o tipo de `bool?` anulável correspondente e uma conversão explícita do tipo `bool?`. No entanto, o .NET fornece métodos adicionais que você pode usar para converter de ou para o tipo de `bool`. Para obter mais informações, consulte a seção [convertendo de valores booleanos](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) na página de referência da API <xref:System.Boolean?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte [a seção tipo bool](~/_csharplang/spec/types.md#the-bool-type) da [ C# especificação da linguagem](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência de C#](../index.md)
- [Tipos de valor](value-types.md)
- [operadores true e false](../operators/true-false-operators.md)
