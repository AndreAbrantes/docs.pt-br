---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 968cfa8e5402458afd6f13545ed999a472adf2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151904"
---
# <a name="tracking"></a><span data-ttu-id="1e25e-101">\<rastreando></span><span class="sxs-lookup"><span data-stu-id="1e25e-101">\<tracking></span></span>
<span data-ttu-id="1e25e-102">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1e25e-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="1e25e-103">Para obter mais informações sobre o rastreamento do fluxo de trabalho e sua configuração, consulte [Rastreamento e rastreamento de fluxo de trabalho e](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) [configuração de rastreamento para um fluxo de trabalho](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1e25e-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="1e25e-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e25e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e25e-105">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="1e25e-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="1e25e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<rastreando>**</span><span class="sxs-lookup"><span data-stu-id="1e25e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e25e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e25e-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e25e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1e25e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1e25e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1e25e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e25e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e25e-110">Attributes</span></span>  
 <span data-ttu-id="1e25e-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1e25e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e25e-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e25e-112">Child Elements</span></span>  
  
|<span data-ttu-id="1e25e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e25e-113">Element</span></span>|<span data-ttu-id="1e25e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e25e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e25e-115">\<participantes></span><span class="sxs-lookup"><span data-stu-id="1e25e-115">\<participants></span></span>](participants.md)|<span data-ttu-id="1e25e-116">Uma coleção de elementos de configuração definindo os participantes que assinar a acompanhar registros.</span><span class="sxs-lookup"><span data-stu-id="1e25e-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="1e25e-117">Os participantes de rastreamento contém a lógica para processar a carga de registros de rastreamento (por exemplo, eles poderiam optar por gravar em um arquivo).</span><span class="sxs-lookup"><span data-stu-id="1e25e-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="1e25e-118">\<>de rastreamentoPerfil</span><span class="sxs-lookup"><span data-stu-id="1e25e-118">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="1e25e-119">Um perfil de rastreamento para filtrar registros de rastreamento emitida de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1e25e-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e25e-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1e25e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1e25e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e25e-121">Element</span></span>|<span data-ttu-id="1e25e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e25e-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e25e-123">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1e25e-123">system.ServiceModel</span></span>|<span data-ttu-id="1e25e-124">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1e25e-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e25e-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e25e-125">Remarks</span></span>  
 <span data-ttu-id="1e25e-126">Rastreamento fornece a capacidade de examinar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1e25e-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="1e25e-127">A infra-estrutura de controle de fluxo de trabalho implementa um fluxo de trabalho para emitir registros que refletem eventos chave durante a execução.</span><span class="sxs-lookup"><span data-stu-id="1e25e-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="1e25e-128">Por exemplo, quando uma instância de fluxo de trabalho inicia ou termina registros de rastreamento são emitidos.</span><span class="sxs-lookup"><span data-stu-id="1e25e-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="1e25e-129">Rastreamento também pode extrair dados relevantes de negócios associados as variáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1e25e-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="1e25e-130">Por exemplo, se o fluxo de trabalho representa um sistema de processamento de pedidos a identificação do pedido pode ser extraída juntamente com o registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1e25e-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="1e25e-131">Em geral, habilitar o rastreamento de WF facilita diagnóstico ou análise comercial sobre uma execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1e25e-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e25e-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="1e25e-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="1e25e-133">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1e25e-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
