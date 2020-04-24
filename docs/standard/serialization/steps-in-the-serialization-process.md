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
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="46f7c-102">Etapas do processo de serialização</span><span class="sxs-lookup"><span data-stu-id="46f7c-102">Steps in the serialization process</span></span>
<span data-ttu-id="46f7c-103">Quando o método <xref:System.Runtime.Serialization.Formatter.Serialize%2A> é chamado em um [formatador](xref:System.Runtime.Serialization.Formatter), a serialização do objeto procede de acordo com a seguinte sequência de regras:</span><span class="sxs-lookup"><span data-stu-id="46f7c-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="46f7c-104">Uma verificação é feita para determinar se o formatador tem um seletor substituto.</span><span class="sxs-lookup"><span data-stu-id="46f7c-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="46f7c-105">Se tiver, verifique se o seletor substituto administra objetos do tipo determinado.</span><span class="sxs-lookup"><span data-stu-id="46f7c-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="46f7c-106">Se o seletor manipular o tipo de objeto, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> será chamado no seletor alternativo.</span><span class="sxs-lookup"><span data-stu-id="46f7c-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="46f7c-107">Se não houver nenhum seletor alternativo ou se ele não manipular o tipo de objeto, uma verificação será feita para determinar se o objeto está marcado com o atributo [Serializable](xref:System.SerializableAttribute).</span><span class="sxs-lookup"><span data-stu-id="46f7c-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="46f7c-108">Se o objeto não estiver marcado, uma <xref:System.Runtime.Serialization.SerializationException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="46f7c-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="46f7c-109">Se o objeto estiver marcado corretamente, verifique se ele implementa a interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="46f7c-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="46f7c-110">Se o objeto implementá-la, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> será chamado no objeto.</span><span class="sxs-lookup"><span data-stu-id="46f7c-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="46f7c-111">Se o objeto não implementar <xref:System.Runtime.Serialization.ISerializable>, a política de serialização padrão será usada, serializando todos os campos não marcados como [NonSerialized](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="46f7c-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="46f7c-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="46f7c-112">See also</span></span>

- [<span data-ttu-id="46f7c-113">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="46f7c-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="46f7c-114">Serialização de XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="46f7c-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
