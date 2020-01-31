---
title: <permission> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 14abb5bd181f401a4e6834d110e20fa920566580
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789730"
---
# <a name="permission-c-programming-guide"></a>> de permissão \<C# (guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parâmetros

- cref = " `member`"

  Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída. *member* deve ser exibido entre aspas duplas (" ").

  Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [\<consulte>](./see.md).

- `description`

  Uma descrição do acesso ao membro.

## <a name="remarks"></a>Comentários

A marca \<permissão > permite documentar o acesso de um membro. A classe <xref:System.Security.PermissionSet> permite que você especifique o acesso a um membro.

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
