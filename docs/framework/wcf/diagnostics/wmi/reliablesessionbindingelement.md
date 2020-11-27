---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: f91e38ab88cd9f93e9bec0e3a6ca65254bc49570
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273315"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="c0ffc-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="c0ffc-102">ReliableSessionBindingElement</span></span>

<span data-ttu-id="c0ffc-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="c0ffc-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0ffc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0ffc-104">Syntax</span></span>  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c0ffc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c0ffc-105">Methods</span></span>  

 <span data-ttu-id="c0ffc-106">A classe ReliableSessionBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c0ffc-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c0ffc-107">Properties</span></span>  

 <span data-ttu-id="c0ffc-108">A classe ReliableSessionBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c0ffc-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="c0ffc-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="c0ffc-109">AcknowledgementInterval</span></span>  

 <span data-ttu-id="c0ffc-110">Tipo de dados: DateTime</span><span class="sxs-lookup"><span data-stu-id="c0ffc-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="c0ffc-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c0ffc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0ffc-112">O intervalo de tempo que um destino aguarda antes de enviar uma confirmação para a origem da mensagem em canais confiáveis que são criados pela fábrica.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="c0ffc-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="c0ffc-113">FlowControlEnabled</span></span>  

 <span data-ttu-id="c0ffc-114">Tipo de dados: booliano</span><span class="sxs-lookup"><span data-stu-id="c0ffc-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="c0ffc-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c0ffc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0ffc-116">Um valor booliano que especifica se o controle de fluxo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="c0ffc-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="c0ffc-117">InactivityTimeout</span></span>  

 <span data-ttu-id="c0ffc-118">Tipo de dados: DateTime</span><span class="sxs-lookup"><span data-stu-id="c0ffc-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="c0ffc-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c0ffc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0ffc-120">Especifica a duração máxima que o canal irá permitir que a outra parte de comunicação não envie nenhuma mensagem antes de falhar o canal.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="c0ffc-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="c0ffc-121">MaxPendingChannels</span></span>  

 <span data-ttu-id="c0ffc-122">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c0ffc-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="c0ffc-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c0ffc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0ffc-124">O número máximo de canais que podem aguardar para serem aceitos no ouvinte.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="c0ffc-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="c0ffc-125">MaxRetryCount</span></span>  

 <span data-ttu-id="c0ffc-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c0ffc-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="c0ffc-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c0ffc-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0ffc-128">O número máximo de vezes que um canal confiável tenta retransmitir uma mensagem para a qual não recebeu uma confirmação, chamando `Send` em seu canal subjacente.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="c0ffc-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="c0ffc-129">MaxTransferWindowSize</span></span>  

 <span data-ttu-id="c0ffc-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c0ffc-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="c0ffc-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c0ffc-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0ffc-132">O tamanho máximo da janela de transferência para a sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="c0ffc-133">Encomendado</span><span class="sxs-lookup"><span data-stu-id="c0ffc-133">Ordered</span></span>  

 <span data-ttu-id="c0ffc-134">Tipo de dados: booliano</span><span class="sxs-lookup"><span data-stu-id="c0ffc-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="c0ffc-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c0ffc-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0ffc-136">Um valor booliano que especifica se as mensagens são garantidas de chegar na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="c0ffc-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="c0ffc-137">ReliableMessagingVersion</span></span>  

 <span data-ttu-id="c0ffc-138">Tipo de dados: inteiro</span><span class="sxs-lookup"><span data-stu-id="c0ffc-138">Data type: integer</span></span>  
  
 <span data-ttu-id="c0ffc-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c0ffc-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0ffc-140">Um inteiro que especifica a versão do protocolo WS-ReliableMessaging usada na sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0ffc-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0ffc-141">Requirements</span></span>  
  
|<span data-ttu-id="c0ffc-142">MOF</span><span class="sxs-lookup"><span data-stu-id="c0ffc-142">MOF</span></span>|<span data-ttu-id="c0ffc-143">Declarado em ServiceModel. mof.</span><span class="sxs-lookup"><span data-stu-id="c0ffc-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c0ffc-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="c0ffc-144">Namespace</span></span>|<span data-ttu-id="c0ffc-145">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c0ffc-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0ffc-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0ffc-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
