---
title: Etapas do processo de serialização
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: f30dd550437e6bc1030c79865bf2edd2c0efbfa9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741044"
---
# <a name="steps-in-the-serialization-process"></a>Etapas do processo de serialização
Quando o método <xref:System.Runtime.Serialization.Formatter.Serialize%2A> é chamado em um [formatador](xref:System.Runtime.Serialization.Formatter), a serialização do objeto procede de acordo com a seguinte sequência de regras:

- Uma verificação é feita para determinar se o formatador tem um seletor substituto. Se tiver, verifique se o seletor substituto administra objetos do tipo determinado. Se o seletor manipular o tipo de objeto, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> será chamado no seletor alternativo.

- Se não houver nenhum seletor alternativo ou se ele não manipular o tipo de objeto, uma verificação será feita para determinar se o objeto está marcado com o atributo [Serializable](xref:System.SerializableAttribute). Se o objeto não estiver marcado, uma <xref:System.Runtime.Serialization.SerializationException> será gerada.

- Se o objeto estiver marcado corretamente, verifique se ele implementa a interface <xref:System.Runtime.Serialization.ISerializable>. Se o objeto implementá-la, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> será chamado no objeto.
  
- Se o objeto não implementar <xref:System.Runtime.Serialization.ISerializable>, a política de serialização padrão será usada, serializando todos os campos não marcados como [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Veja também

- [Serialização binária](binary-serialization.md)
- [Serialização de XML e SOAP](xml-and-soap-serialization.md)
