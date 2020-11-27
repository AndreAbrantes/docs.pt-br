---
title: 'Como: configurar o comportamento ocioso com WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 8491fccee9f148412aed89280ccd20b315d25da6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257360"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="44597-102">Como: configurar o comportamento ocioso com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="44597-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>

<span data-ttu-id="44597-103">Os fluxos de trabalho ficam ociosos quando encontram um indicador que deve ser retomado por algum estímulo externo, por exemplo, quando a instância do fluxo de trabalho está aguardando a entrega de uma mensagem usando uma <xref:System.ServiceModel.Activities.Receive> atividade.</span><span class="sxs-lookup"><span data-stu-id="44597-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="44597-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> é um comportamento que permite que você especifique o tempo entre quando uma instância de serviço fica ociosa e quando a instância é persistente ou descarregada.</span><span class="sxs-lookup"><span data-stu-id="44597-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="44597-105">Ele contém duas propriedades que permitem que você defina esses intervalos de tempo.</span><span class="sxs-lookup"><span data-stu-id="44597-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="44597-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> Especifica o período de tempo entre o momento em que uma instância do serviço de fluxo de trabalho fica ociosa e quando a instância do serviço de fluxo de trabalho é persistida.</span><span class="sxs-lookup"><span data-stu-id="44597-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="44597-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> Especifica o período de tempo entre quando uma instância do serviço de fluxo de trabalho fica ociosa e quando a instância do serviço de fluxo de trabalho é descarregada, em que Unload significa persistir a instância para o repositório de instância e removê-la da memória.</span><span class="sxs-lookup"><span data-stu-id="44597-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="44597-108">Este tópico explica como configurar o <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="44597-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="44597-109">Para configurar o WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="44597-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="44597-110">Adicione um `workflowIdle` elemento <> ao `behavior` elemento> <dentro do elemento <> `serviceBehaviors` , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="44597-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="44597-111">O `timeToUnload` atributo especifica o período de tempo entre o momento em que uma instância do serviço de fluxo de trabalho fica ociosa e quando o serviço de fluxo de trabalho é descarregado.</span><span class="sxs-lookup"><span data-stu-id="44597-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="44597-112">O `timeToPersist` atributo especifica o período de tempo entre o momento em que uma instância do serviço de fluxo de trabalho fica ociosa e quando a instância do serviço de fluxo de trabalho é persistida.</span><span class="sxs-lookup"><span data-stu-id="44597-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="44597-113">O valor padrão para `timeToUnload` é de 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="44597-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="44597-114">O valor padrão para `timeToPersist` é <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="44597-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="44597-115">Se você quiser manter instâncias ociosas na memória, mas mantê-las para robustez, defina valores para que `timeToPersist`  <  `timeToUnload` .</span><span class="sxs-lookup"><span data-stu-id="44597-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="44597-116">Se você quiser impedir que instâncias ociosas sejam descarregadas, defina `timeToUnload` como <xref:System.TimeSpan.MaxValue> .</span><span class="sxs-lookup"><span data-stu-id="44597-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="44597-117">Para obter mais informações sobre o <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> , consulte [extensibilidade do host do serviço de fluxo de trabalho](workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="44597-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="44597-118">O exemplo de configuração anterior está usando uma configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="44597-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="44597-119">Para obter mais informações, consulte [configuração simplificada](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="44597-119">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="44597-120">Para alterar o comportamento ocioso no código</span><span class="sxs-lookup"><span data-stu-id="44597-120">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="44597-121">O exemplo a seguir altera o tempo de espera antes de persistir e descarregar programaticamente.</span><span class="sxs-lookup"><span data-stu-id="44597-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="44597-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="44597-122">See also</span></span>

- [<span data-ttu-id="44597-123">Extensibilidade de host de serviço do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44597-123">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="44597-124">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="44597-124">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="44597-125">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="44597-125">Workflow Services</span></span>](workflow-services.md)
