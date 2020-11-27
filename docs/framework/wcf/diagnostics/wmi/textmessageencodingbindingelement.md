---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 551761af255681dd2c2dbb9e40b7103c95cd2e0a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267215"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="8dea7-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8dea7-102">TextMessageEncodingBindingElement</span></span>

<span data-ttu-id="8dea7-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8dea7-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dea7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dea7-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8dea7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8dea7-105">Methods</span></span>  

 <span data-ttu-id="8dea7-106">A classe TextMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="8dea7-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8dea7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8dea7-107">Properties</span></span>  

 <span data-ttu-id="8dea7-108">A classe TextMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8dea7-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="8dea7-109">Codificação</span><span class="sxs-lookup"><span data-stu-id="8dea7-109">Encoding</span></span>  

 <span data-ttu-id="8dea7-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8dea7-110">Data type: string</span></span>  
  
 <span data-ttu-id="8dea7-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8dea7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8dea7-112">A codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="8dea7-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="8dea7-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8dea7-113">MaxReadPoolSize</span></span>  

 <span data-ttu-id="8dea7-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="8dea7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8dea7-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8dea7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8dea7-116">Um inteiro que define quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="8dea7-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="8dea7-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8dea7-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="8dea7-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="8dea7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="8dea7-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8dea7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8dea7-120">Um inteiro que define quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="8dea7-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="8dea7-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8dea7-121">ReaderQuotas</span></span>  

 <span data-ttu-id="8dea7-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8dea7-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="8dea7-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8dea7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8dea7-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="8dea7-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dea7-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8dea7-125">Requirements</span></span>  
  
|<span data-ttu-id="8dea7-126">MOF</span><span class="sxs-lookup"><span data-stu-id="8dea7-126">MOF</span></span>|<span data-ttu-id="8dea7-127">Declarado em ServiceModel. mof.</span><span class="sxs-lookup"><span data-stu-id="8dea7-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8dea7-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="8dea7-128">Namespace</span></span>|<span data-ttu-id="8dea7-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8dea7-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8dea7-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="8dea7-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
