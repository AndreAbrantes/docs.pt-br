---
description: '@ – Referência de C#'
title: '@ – Referência de C#'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: 7d78b28479ed6128321207073dc94976710f10b6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138898"
---
# <a name="-c-reference"></a>@ (Referência de C#)

O caractere especial `@` serve como um identificador textual. Ele pode ser usado das seguintes maneiras:

1. Para habilitar palavras-chave de C# a serem usadas como identificadores. O caractere `@` atua como prefixo de um elemento de código que o compilador deve interpretar como um identificador e não como uma palavra-chave de C#. O exemplo a seguir usa o caractere `@` para definir um identificador chamado `for` que usa em um loop `for`.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Para indicar que um literal de cadeia de caracteres é interpretado de forma textual. O caractere `@` neste exemplo define um *literal de cadeia de caracteres textual*. Sequências de escape simples (como `"\\"` para uma barra invertida), sequências de escape hexadecimais (como um `"\x0041"` para um A maiúsculo) e sequências de escape Unicode (como `"\u0041"` para um A maiúsculo) são interpretadas de forma textual. Apenas uma sequência de escape de aspas ( `""` ) não é interpretada literalmente; ela produz uma aspa dupla. Além disso, no caso de uma [cadeia de caracteres interpolada](interpolated.md) textual, as sequências de escape de chave (`{{` e `}}`) não são interpretadas de forma textual; elas geram caracteres de chave única. O exemplo a seguir define dois caminhos de arquivo idênticos, um usando um literal de cadeia de caracteres regular e o outro usando um literal de cadeia de caracteres textual. Este é um dos usos mais comuns de literais de cadeias de caracteres textuais.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   O exemplo a seguir ilustra o efeito de definir um literal de cadeia de caracteres regular e um literal de cadeia de caracteres textual que contêm sequências de caracteres idênticas.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Para habilitar o compilador a distinguir entre os atributos em caso de um conflito de nomenclatura. Um atributo é um tipo que deriva de <xref:System.Attribute>. Seu nome de tipo normalmente inclui o sufixo **Attribute**, embora o compilador não imponha essa convenção. O atributo pode, então, ser referenciado no código por seu nome de tipo completo (por exemplo, `[InfoAttribute]` ou pelo nome abreviado (por exemplo, `[Info]`). No entanto, um conflito de nomenclatura ocorre se dois nomes de tipo abreviados forem idênticos e um nome de tipo incluir o sufixo **Attribute** e o outro não incluir. Por exemplo, o código a seguir não é compilado porque o compilador não consegue determinar se o atributo `Info` ou `InfoAttribute` é aplicado à classe `Example`. Veja [CS1614](../compiler-messages/cs1614.md) para obter mais informações.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Guia de programação C#](../../programming-guide/index.md)
- [Caracteres especiais do C#](./index.md)
