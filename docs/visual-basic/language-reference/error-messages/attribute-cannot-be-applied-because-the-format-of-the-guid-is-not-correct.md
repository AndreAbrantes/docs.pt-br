---
title: "'<attribute>' não pode ser aplicado porque o formato da GUID '<number>' não está correto"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 8e9ac019470685d9fc45342273096d678a29428d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162642"
---
# <a name="bc32500-attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>BC32500: ' \<attribute> ' não pode ser aplicado porque o formato do GUID ' \<number> ' não está correto

Um `COMClassAttribute` bloco de atributo especifica um GUID (identificador global exclusivo) que não está de acordo com o formato adequado para um GUID. `COMClassAttribute` usa GUIDs para identificar exclusivamente a classe, a interface e o evento de criação.

 Um GUID consiste em 16 bytes, dos quais os oito primeiros são numéricos e os oito últimos são binários. Ele é gerado pelos utilitários da Microsoft, como uuidgen.exe e é garantido que seja exclusivo em espaço e tempo.

 **ID do erro:** BC32500

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Determine o GUID ou GUIDs corretos necessários para identificar o objeto COM.

2. Certifique-se de que as cadeias de caracteres GUID apresentadas ao `COMClassAttribute` bloco de atributos sejam copiadas corretamente.

## <a name="see-also"></a>Veja também

- <xref:System.Guid>
- [Visão geral de atributos](../../programming-guide/concepts/attributes/index.md)
