---
title: Associações personalizadas
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 062aba26227fedeea3e5f462ebf5d55cf0cba56c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539991"
---
# <a name="custom-bindings"></a><span data-ttu-id="09893-102">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="09893-102">Custom Bindings</span></span>

<span data-ttu-id="09893-103">Você pode usar a <xref:System.ServiceModel.Channels.CustomBinding> classe quando uma das associações fornecidas pelo sistema não atender aos requisitos do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="09893-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="09893-104">Todas as associações são construídas a partir de um conjunto ordenado de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="09893-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="09893-105">Associações personalizadas podem ser criadas a partir de um conjunto de elementos de associação fornecidos pelo sistema ou podem incluir elementos de associação personalizados definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="09893-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="09893-106">Você pode usar elementos de associação personalizados, por exemplo, para habilitar o uso de novos transportes ou codificadores em um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="09893-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="09893-107">Para obter exemplos de funcionamento, consulte [exemplos de associação personalizada](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="09893-107">For working examples, see [Custom Binding Samples](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="09893-108">Para obter mais informações, consulte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="09893-108">For more information, see [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="09893-109">Construção de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="09893-109">Construction of a Custom Binding</span></span>

<span data-ttu-id="09893-110">Uma associação personalizada é criada usando o <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> Construtor de uma coleção de elementos de associação que são "empilhados" em uma ordem específica:</span><span class="sxs-lookup"><span data-stu-id="09893-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="09893-111">Na parte superior, há uma <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> classe opcional que permite transações de fluxo.</span><span class="sxs-lookup"><span data-stu-id="09893-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>

- <span data-ttu-id="09893-112">A seguir é uma <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> classe opcional que fornece um mecanismo de sessão e ordenação, conforme definido na especificação WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="09893-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="09893-113">Uma sessão pode cruzar o SOAP e transportar intermediários.</span><span class="sxs-lookup"><span data-stu-id="09893-113">A session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="09893-114">A seguir é uma <xref:System.ServiceModel.Channels.SecurityBindingElement> classe opcional que fornece recursos de segurança como autorização, autenticação, proteção e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="09893-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>

- <span data-ttu-id="09893-115">A seguir é uma <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> classe opcional que fornece a capacidade de ter duas vias de comunicação duplex com um protocolo de transporte que não ofereça suporte à comunicação duplex nativamente, como http.</span><span class="sxs-lookup"><span data-stu-id="09893-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>

- <span data-ttu-id="09893-116">A seguir é uma <xref:System.ServiceModel.Channels.OneWayBindingElement> classe opcional) que fornece comunicação unidirecional.</span><span class="sxs-lookup"><span data-stu-id="09893-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>

- <span data-ttu-id="09893-117">A seguir é um elemento de associação de segurança de fluxo opcional que pode ser um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="09893-117">Next is an optional stream security binding element which can be one of the following.</span></span>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="09893-118">A seguir está um elemento de associação de codificação de mensagem necessário.</span><span class="sxs-lookup"><span data-stu-id="09893-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="09893-119">Você pode usar seu próprio codificador de mensagem ou uma das três associações de codificação de mensagem:</span><span class="sxs-lookup"><span data-stu-id="09893-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

<span data-ttu-id="09893-120">Na parte inferior, há um elemento Transport necessário.</span><span class="sxs-lookup"><span data-stu-id="09893-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="09893-121">Você pode usar seu próprio transporte ou um dos seguintes elementos de ligação de transporte Windows Communication Foundation (WCF) fornece:</span><span class="sxs-lookup"><span data-stu-id="09893-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

<span data-ttu-id="09893-122">A tabela a seguir resume as opções para cada camada.</span><span class="sxs-lookup"><span data-stu-id="09893-122">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="09893-123">Camada</span><span class="sxs-lookup"><span data-stu-id="09893-123">Layer</span></span>|<span data-ttu-id="09893-124">Opções</span><span class="sxs-lookup"><span data-stu-id="09893-124">Options</span></span>|<span data-ttu-id="09893-125">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="09893-125">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="09893-126">Transactions</span><span class="sxs-lookup"><span data-stu-id="09893-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="09893-127">No</span><span class="sxs-lookup"><span data-stu-id="09893-127">No</span></span>|
|<span data-ttu-id="09893-128">Confiabilidade</span><span class="sxs-lookup"><span data-stu-id="09893-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="09893-129">No</span><span class="sxs-lookup"><span data-stu-id="09893-129">No</span></span>|
|<span data-ttu-id="09893-130">Segurança</span><span class="sxs-lookup"><span data-stu-id="09893-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="09893-131">No</span><span class="sxs-lookup"><span data-stu-id="09893-131">No</span></span>|
|<span data-ttu-id="09893-132">Codificação</span><span class="sxs-lookup"><span data-stu-id="09893-132">Encoding</span></span>|<span data-ttu-id="09893-133">Texto, binário, mecanismo de otimização de transmissão de mensagens (MTOM), personalizado</span><span class="sxs-lookup"><span data-stu-id="09893-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="09893-134">Yes</span><span class="sxs-lookup"><span data-stu-id="09893-134">Yes</span></span>|
|<span data-ttu-id="09893-135">Transport</span><span class="sxs-lookup"><span data-stu-id="09893-135">Transport</span></span>|<span data-ttu-id="09893-136">TCP, HTTP, HTTPS, pipes nomeados (também conhecido como IPC), ponto a ponto (P2P), Enfileiramento de mensagens (também conhecido como MSMQ), personalizado</span><span class="sxs-lookup"><span data-stu-id="09893-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="09893-137">Yes</span><span class="sxs-lookup"><span data-stu-id="09893-137">Yes</span></span>|

<span data-ttu-id="09893-138">Além disso, você pode definir seus próprios elementos de ligação e inseri-los entre as camadas definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="09893-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

## <a name="see-also"></a><span data-ttu-id="09893-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="09893-139">See also</span></span>

- [<span data-ttu-id="09893-140">Visão geral de criação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="09893-140">Endpoint Creation Overview</span></span>](../endpoint-creation-overview.md)
- [<span data-ttu-id="09893-141">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="09893-141">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="09893-142">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="09893-142">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="09893-143">Como: personalizar uma associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="09893-143">How to: Customize a System-Provided Binding</span></span>](how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="09893-144">Associação personalizado</span><span class="sxs-lookup"><span data-stu-id="09893-144">Custom Binding</span></span>](../samples/custom-binding.md)
