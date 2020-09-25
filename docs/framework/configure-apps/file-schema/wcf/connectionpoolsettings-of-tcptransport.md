---
title: <connectionPoolSettings> de <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 53523fd550ecad931bfb2af5eb9beb71c60d44f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176000"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="ec071-102">\<connectionPoolSettings> de \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="ec071-102">\<connectionPoolSettings> of \<tcpTransport></span></span>

<span data-ttu-id="ec071-103">Especifica configurações de pool de conexões adicionais para um transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="ec071-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="ec071-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec071-104">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec071-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec071-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ec071-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ec071-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec071-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec071-107">Attributes</span></span>  
  
|<span data-ttu-id="ec071-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ec071-108">Attribute</span></span>|<span data-ttu-id="ec071-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec071-109">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="ec071-110">Uma cadeia de caracteres que define o nome do pool de conexões usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="ec071-110">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="ec071-111">No modo de fluxo, as conexões não são compartilhadas, o que significa que o pool de conexões está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="ec071-111">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="ec071-112">O padrão é uma cadeia de caracteres "padrão".</span><span class="sxs-lookup"><span data-stu-id="ec071-112">The default is a "default" string.</span></span> <span data-ttu-id="ec071-113">Você pode modificar esse valor para isolar as conexões de um cliente específico em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="ec071-113">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="ec071-114">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="ec071-114">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="ec071-115">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="ec071-115">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="ec071-116">Um <xref:System.TimeSpan> que especifica o tempo após o qual uma conexão ativa é fechada.</span><span class="sxs-lookup"><span data-stu-id="ec071-116">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="ec071-117">O padrão é 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="ec071-117">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="ec071-118">Uma conexão é fechada depois de ser retornada ao cache de conexão e não durante a transmissão ativa.</span><span class="sxs-lookup"><span data-stu-id="ec071-118">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="ec071-119">O cache de conexão usado pelo transporte TCP cria novas conexões conforme necessário para cada ponto de extremidade, até o limite de cache definido por `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="ec071-119">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="ec071-120">Um inteiro positivo que especifica o número máximo de conexões com um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="ec071-120">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="ec071-121">As conexões que excedem o limite são enfileiradas até que um espaço abaixo do limite fique disponível.</span><span class="sxs-lookup"><span data-stu-id="ec071-121">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="ec071-122">O `idleTimeout` limita a duração em que as conexões permanecem enfileiradas antes que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="ec071-122">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="ec071-123">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="ec071-123">The default is 10.</span></span><br /><br /> <span data-ttu-id="ec071-124">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="ec071-124">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="ec071-125">Se esse valor for excedido por ter mais conexões de cliente ativas, o serviço poderá parecer sem resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ec071-125">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="ec071-126">Nesse caso, esse valor deve ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperadas para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="ec071-126">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec071-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ec071-127">Child Elements</span></span>  

 <span data-ttu-id="ec071-128">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ec071-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec071-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec071-129">Parent Elements</span></span>  
  
|<span data-ttu-id="ec071-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec071-130">Element</span></span>|<span data-ttu-id="ec071-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec071-131">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="ec071-132">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="ec071-132">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec071-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec071-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ec071-134">Transportes</span><span class="sxs-lookup"><span data-stu-id="ec071-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="ec071-135">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="ec071-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="ec071-136">Associações</span><span class="sxs-lookup"><span data-stu-id="ec071-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ec071-137">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="ec071-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ec071-138">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ec071-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
