---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: b4d8503543c93d0112fc39e4b2dba5434bc56472
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237398"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="1843a-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1843a-102">MtomMessageEncodingBindingElement</span></span>

<span data-ttu-id="1843a-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1843a-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1843a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1843a-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1843a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1843a-105">Methods</span></span>  

 <span data-ttu-id="1843a-106">A classe MtomMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="1843a-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1843a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1843a-107">Properties</span></span>  

 <span data-ttu-id="1843a-108">A classe MtomMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1843a-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="1843a-109">Codificação</span><span class="sxs-lookup"><span data-stu-id="1843a-109">Encoding</span></span>  

 <span data-ttu-id="1843a-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1843a-110">Data type: string</span></span>  
  
 <span data-ttu-id="1843a-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1843a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1843a-112">A codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="1843a-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="1843a-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="1843a-113">MaxReadPoolSize</span></span>  

 <span data-ttu-id="1843a-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="1843a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1843a-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1843a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1843a-116">Um inteiro que define quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="1843a-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="1843a-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="1843a-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="1843a-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="1843a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="1843a-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1843a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1843a-120">Um inteiro que define quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="1843a-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="1843a-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1843a-121">ReaderQuotas</span></span>  

 <span data-ttu-id="1843a-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1843a-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="1843a-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1843a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1843a-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="1843a-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1843a-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1843a-125">Requirements</span></span>  
  
|<span data-ttu-id="1843a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1843a-126">MOF</span></span>|<span data-ttu-id="1843a-127">Declarado em ServiceModel. mof.</span><span class="sxs-lookup"><span data-stu-id="1843a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1843a-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="1843a-128">Namespace</span></span>|<span data-ttu-id="1843a-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1843a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1843a-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="1843a-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
