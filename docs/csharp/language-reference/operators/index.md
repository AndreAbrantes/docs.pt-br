---
title: Operadores C# – Referência de C#
ms.date: 08/20/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: f0ca111000033f9db84145a38e8d567f96b75d1d
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121071"
---
# <a name="c-operators-c-reference"></a>Operadores C# (Referência de C#)

O C# oferece vários operadores predefinidos, compatíveis com os tipos internos. Por exemplo, os [operadores aritméticos](arithmetic-operators.md) executam operações aritméticas com operandos numéricos, já os [operadores lógicos boolianos](boolean-logical-operators.md) executam operações lógicas com operandos [bool](../builtin-types/bool.md). Determinados operadores podem ser [sobrecarregados](operator-overloading.md). Com a sobrecarga de operador, você pode especificar o comportamento do operador para os operandos de um tipo definido pelo usuário.

Em uma [expressão](../../programming-guide/statements-expressions-operators/expressions.md), a precedência e a associação dos operadores determinam a ordem na qual as operações são executadas. Você pode usar parênteses para alterar a ordem de avaliação imposta pela prioridade e pela associação dos operadores.

## <a name="operator-precedence"></a>Precedência do operador

Em uma expressão com vários operadores, os operadores com maior precedência são avaliados antes dos operadores com menor precedência. No exemplo a seguir, a multiplicação é executada primeiro porque tem uma precedência mais alta do que a adição:

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

Use parênteses para alterar a ordem de avaliação imposta pela precedência do operador:

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

A tabela a seguir lista os operadores C#, começando com a precedência mais alta até a mais baixa. Os operadores em cada linha têm a mesma precedência.

| Operadores | Categoria ou nome |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-expression-), [x?.y](member-access-operators.md#null-conditional-operators--and-), [x?[y]](member-access-operators.md#null-conditional-operators--and-), [f(x)](member-access-operators.md#invocation-expression-), [a&#91;i&#93;](member-access-operators.md#indexer-operator-), [x++](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [new](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](default.md), [nameof](nameof.md), [delegate](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x->y](pointer-related-operators.md#pointer-member-access-operator--) | Primária |
| [+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++x](arithmetic-operators.md#increment-operator-), [-x](arithmetic-operators.md#decrement-operator---), [^x](member-access-operators.md#index-from-end-operator-), [(T)x](type-testing-and-cast.md#cast-expression), [esperar](await.md), [&x](pointer-related-operators.md#address-of-operator-), [*x](pointer-related-operators.md#pointer-indirection-operator-), [verdadeiro e falso](true-false-operators.md) | Unário |
| [X.. Y](member-access-operators.md#range-operator-) | Intervalo |
| [switch](../../whats-new/csharp-8.md#switch-expressions) | Expressão `switch` |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), [x % y](arithmetic-operators.md#remainder-operator-) | Multiplicativo|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Aditiva |
| [ \< x \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Turno |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x >= y](comparison-operators.md#greater-than-or-equal-operator-), [is](type-testing-and-cast.md#is-operator), [as](type-testing-and-cast.md#as-operator) | Teste de tipo e relacional |
| [x == y,](equality-operators.md#equality-operator-) [x != y](equality-operators.md#inequality-operator-) | Igualitário |
| `x & y` | [AND lógico booliano](boolean-logical-operators.md#logical-and-operator-) ou [AND lógico bit a bit](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [XOR lógico booliano](boolean-logical-operators.md#logical-exclusive-or-operator-) ou [XOR lógico bit a bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [OR lógico booliano](boolean-logical-operators.md#logical-or-operator-) ou [OR lógico bit a bit](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | AND condicional |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | OR condicional |
| [x ?? y](null-coalescing-operator.md) | Operador de coalescência nula |
| [c ? t : f](conditional-operator.md) | Operador condicional |
| [x = y](assignment-operator.md), [x += y](arithmetic-operators.md#compound-assignment), x [-= y](arithmetic-operators.md#compound-assignment), x [*= y](arithmetic-operators.md#compound-assignment), x [/= y](arithmetic-operators.md#compound-assignment), x % = [y](arithmetic-operators.md#compound-assignment), x &[= y](boolean-logical-operators.md#compound-assignment), x &#124;= [y](boolean-logical-operators.md#compound-assignment), x [^ y](boolean-logical-operators.md#compound-assignment), x <<= [y](bitwise-and-shift-operators.md#compound-assignment), x >>[= y](bitwise-and-shift-operators.md#compound-assignment), [x ?? = y,](null-coalescing-operator.md)[=>](lambda-operator.md) | Declaração de atribuição e lambda |

## <a name="operator-associativity"></a>Associação de operador

Quando os operadores têm a mesma precedência, a associação dos operadores determina a ordem na qual as operações são executadas:

- Os operadores *associativos esquerdos* são avaliados na ordem da esquerda para a direita. Com exceção dos [operadores de cessão](assignment-operator.md) e dos [operadores de coalizão nula,](null-coalescing-operator.md)todos os operadores binários são associativos à esquerda. Por exemplo, `a + b - c` é avaliado como `(a + b) - c`.
- Os operadores *associativos direitos* são avaliados na ordem da direita para a esquerda. Os operadores de cessão, os operadores de coalizão nula e o [operador `?:` condicional](conditional-operator.md) são associativos. Por exemplo, `x = y = z` é avaliado como `x = (y = z)`.

Use parênteses para alterar a ordem de avaliação imposta pela associação de operador:

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>Avaliação do operando

Sem considerar a relação com a precedência e a associação de operadores, os operandos em uma expressão são avaliados da esquerda para a direita. Os exemplos a seguir demonstram a ordem em que os operadores e os operandos são avaliados:

| Expression | Ordem de avaliação |
| ---------- | ------------------- |
|`a + b`|a, b, +|
|`a + b * c`|a, b, c, *, +|
|`a / b + c * d`|a, b, /, c, d, *, +|
|`a / (b + c) * d`|a, b, c, +, /, d, *|

Normalmente, todos os operandos do operador são avaliados. No entanto, alguns operadores avaliam os operands de forma condicional. Ou seja, o valor do operand mais à esquerda de tal operador define se (ou qual) outros operands devem ser avaliados. Estes operadores são os operadores lógicos condicionais [e`&&`( e](boolean-logical-operators.md#conditional-logical-and-operator-) OR ( [`||`)](boolean-logical-operators.md#conditional-logical-or-operator-) operadores, os [operadores nulos-coalescência e, `??` `??=` ](null-coalescing-operator.md)os [operadores nulidades `?.` e `?[]` ](member-access-operators.md#null-conditional-operators--and-), e o operador [ `?:`condicional ](conditional-operator.md). Para obter mais informações, consulte a descrição de cada operador.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira a seção [Operadores](~/_csharplang/spec/expressions.md#operators) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Expressões](../../programming-guide/statements-expressions-operators/expressions.md)
