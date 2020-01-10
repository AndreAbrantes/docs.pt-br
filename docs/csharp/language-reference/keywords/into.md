---
title: into – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: f0f5ff1e56a65e83385f814df2fadd957f53561e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713620"
---
# <a name="into-c-reference"></a>into (Referência de C#)

A palavra-chave contextual `into` pode ser usada para criar um identificador temporário para armazenar os resultados de uma cláusula [group](group-clause.md), [join](join-clause.md) ou [select](select-clause.md) em um novo identificador. Esse identificador por si só pode ser um gerador de comandos de consulta adicionais. Quando usado em uma cláusula `group` ou `select`, o uso do novo identificador é, às vezes, conhecido como uma *continuação*.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra o uso da palavra-chave `into` para habilitar um identificador temporário `fruitGroup` que tem um tipo inferido de `IGrouping`. Usando o identificador, é possível invocar o método <xref:System.Linq.Enumerable.Count%2A> em cada grupo e selecionar apenas os grupos que contêm duas ou mais palavras.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

O uso de `into` em uma cláusula `group` só é necessário quando você deseja realizar operações de consulta adicionais em cada grupo. Para obter mais informações, consulte [Cláusula group](group-clause.md).

Para obter um exemplo do uso de `into` em uma cláusula `join`, consulte [cláusula join](join-clause.md).

## <a name="see-also"></a>Veja também

- [Palavras-chave de Consulta (LINQ)](query-keywords.md)
- [LINQ em C#](../../linq/index.md)
- [Cláusula group](group-clause.md)
