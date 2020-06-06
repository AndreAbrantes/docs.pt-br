---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399777"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="25a36-102">\<security> de \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="25a36-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="25a36-103">Contém as definições de segurança associadas a um canal de pares, incluindo o tipo de autenticação utilizada e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="25a36-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="25a36-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25a36-104">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25a36-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="25a36-105">Attributes and Elements</span></span>  
 <span data-ttu-id="25a36-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="25a36-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25a36-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="25a36-107">Attributes</span></span>  
  
|<span data-ttu-id="25a36-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="25a36-108">Attribute</span></span>|<span data-ttu-id="25a36-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="25a36-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="25a36-110">Especifica o tipo de segurança a ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="25a36-110">Specifies the type of security to be applied.</span></span> <span data-ttu-id="25a36-111">O valor padrão é Message.</span><span class="sxs-lookup"><span data-stu-id="25a36-111">The default value is Message.</span></span> <span data-ttu-id="25a36-112">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="25a36-112">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="25a36-113">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="25a36-113">mode Attribute</span></span>  
  
|<span data-ttu-id="25a36-114">Valor</span><span class="sxs-lookup"><span data-stu-id="25a36-114">Value</span></span>|<span data-ttu-id="25a36-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="25a36-115">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="25a36-116">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="25a36-116">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="25a36-117">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="25a36-117">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="25a36-118">A segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="25a36-118">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="25a36-119">O HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="25a36-119">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="25a36-120">As mensagens SOAP fornecem tipos de credenciais avançados.</span><span class="sxs-lookup"><span data-stu-id="25a36-120">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25a36-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="25a36-121">Child Elements</span></span>  
  
|<span data-ttu-id="25a36-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="25a36-122">Element</span></span>|<span data-ttu-id="25a36-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="25a36-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="25a36-124">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="25a36-124">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="25a36-125">Esse elemento tem um `clientCredentialType` atributo que especifica as credenciais a serem usadas ao interagir com um serviço.</span><span class="sxs-lookup"><span data-stu-id="25a36-125">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="25a36-126">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="25a36-126">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="25a36-127">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="25a36-127">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25a36-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="25a36-128">Parent Elements</span></span>  
  
|<span data-ttu-id="25a36-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="25a36-129">Element</span></span>|<span data-ttu-id="25a36-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="25a36-130">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="25a36-131">Define um transporte de mesmo nível para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="25a36-131">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25a36-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="25a36-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="25a36-133">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="25a36-133">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="25a36-134">Transportes</span><span class="sxs-lookup"><span data-stu-id="25a36-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="25a36-135">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="25a36-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="25a36-136">Associações</span><span class="sxs-lookup"><span data-stu-id="25a36-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="25a36-137">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="25a36-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="25a36-138">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="25a36-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
