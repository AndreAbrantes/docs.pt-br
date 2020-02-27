---
title: Valores padrão de C# tipos – C# referência
description: Aprenda os valores padrão de C# tipos como bool, Char, int, float, Double e mais.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625859"
---
# <a name="default-values-of-c-types-c-reference"></a>Valores padrão de C# tipos (C# referência)

A seguinte tabela mostra os valores padrão de tipos C#:

|Tipo|Valor padrão|
|---------|------------------|
|Qualquer tipo de referência|`null`|
|Qualquer [tipo numérico integral interno](integral-numeric-types.md)|0 (zero)|
|Qualquer [tipo numérico de ponto flutuante interno](floating-point-numeric-types.md)|0 (zero)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U+0000)|
|[enum](enum.md)|O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.|
|[struct](struct.md)|O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.|
|Qualquer [tipo de valor que permite valor nulo](nullable-value-types.md)|Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida. Esse valor padrão também é conhecido como o valor *nulo* de um tipo de valor anulável.|

Use o [operador padrão](../operators/default.md) para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:

```csharp
int a = default(int);
```

Começando no C# 7.1, você pode usar o [`default` literal](../operators/default.md#default-literal) para inicializar uma variável com o valor padrão de seu tipo:

```csharp
int a = default;
```

Para um tipo de valor, o construtor implícito sem parâmetros também produz o valor padrão do tipo, como mostra o seguinte exemplo:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

Em tempo de execução, se a instância de <xref:System.Type?displayProperty=nameWithType> representar um tipo de valor, você poderá usar o método <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> para invocar o construtor sem parâmetros para obter o valor padrão do tipo.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Valores padrão](~/_csharplang/spec/variables.md#default-values)
- [Construtores padrão](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Construtores](../../programming-guide/classes-and-structs/constructors.md)
