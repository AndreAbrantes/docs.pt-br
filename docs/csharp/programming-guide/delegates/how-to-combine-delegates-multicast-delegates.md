---
title: Como combinar delegados (Delegados Multicast) - Guia de Programação C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705373"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Como combinar delegados (delegados multicast) (Guia de Programação em C#)
Este exemplo demonstra como criar delegados multicast. Uma propriedade útil de objetos [delegados](../../language-reference/builtin-types/reference-types.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`. O delegado multicast contém uma lista dos delegados atribuídos. Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem. Apenas os delegados do mesmo tipo podem ser combinados.  
  
 O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.MulticastDelegate>
- [C# Guia de Programação](../index.md)
- [Eventos](../events/index.md)
