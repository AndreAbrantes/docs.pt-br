---
title: Palavra-chave contextual remove – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 8ea3ea1910e28c03b2a894c64415cb2ccff942d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713138"
---
# <a name="remove-c-reference"></a>remove (Referência de C#)

A palavra-chave contextual `remove` é usada para definir um acessador de eventos personalizado invocado quando o código cliente cancela a assinatura do seu [evento](event.md). Se você fornecer um acessador `remove` personalizado, também será necessário fornecer um acessador [add](add.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um evento com os acessadores [add](add.md) e `remove` personalizados. Para o exemplo completo, consulte [Como implementar eventos de interface](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.

## <a name="see-also"></a>Confira também

- [Eventos](../../programming-guide/events/index.md)
