---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abaacfb6541d41019a8d0cd6df53913c6b7911f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="6983c-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="6983c-102">OneWayBindingElement</span></span>
<span data-ttu-id="6983c-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="6983c-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6983c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6983c-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6983c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6983c-105">Methods</span></span>  
 <span data-ttu-id="6983c-106">A classe OneWayBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="6983c-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6983c-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6983c-107">Properties</span></span>  
 <span data-ttu-id="6983c-108">A classe OneWayBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6983c-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="6983c-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6983c-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="6983c-110">Tipo de dados: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6983c-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="6983c-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6983c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6983c-112">As configurações de pool do canal.</span><span class="sxs-lookup"><span data-stu-id="6983c-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="6983c-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="6983c-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="6983c-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="6983c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="6983c-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6983c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6983c-116">O número máximo de canais aceitos.</span><span class="sxs-lookup"><span data-stu-id="6983c-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="6983c-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="6983c-117">PacketRoutable</span></span>  
 <span data-ttu-id="6983c-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="6983c-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6983c-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6983c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6983c-120">Um valor que indica se o pacote é roteável.</span><span class="sxs-lookup"><span data-stu-id="6983c-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6983c-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6983c-121">Requirements</span></span>  
  
|<span data-ttu-id="6983c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6983c-122">MOF</span></span>|<span data-ttu-id="6983c-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6983c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6983c-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="6983c-124">Namespace</span></span>|<span data-ttu-id="6983c-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6983c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6983c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6983c-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
