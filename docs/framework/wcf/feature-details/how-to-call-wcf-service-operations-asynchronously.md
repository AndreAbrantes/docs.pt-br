---
title: Como chamar operações de serviço do WCF de maneira assíncrona
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 5eae08ab6b8dee5ebece66a1c41c87ebab3387bc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963274"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="e9d7e-102">Como chamar operações de serviço do WCF de maneira assíncrona</span><span class="sxs-lookup"><span data-stu-id="e9d7e-102">How to: Call WCF Service Operations Asynchronously</span></span>

<span data-ttu-id="e9d7e-103">Este artigo aborda como um cliente pode acessar uma operação de serviço de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-103">This article covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="e9d7e-104">O serviço neste artigo implementa a interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-104">The service in this article implements the `ICalculator` interface.</span></span> <span data-ttu-id="e9d7e-105">O cliente pode chamar as operações nessa interface de forma assíncrona usando o modelo de chamada assíncrona controlado por evento.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="e9d7e-106">(Para obter mais informações sobre o modelo de chamada assíncrona baseado em evento, consulte [programação multi-threaded com o padrão assíncrono baseado em evento](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span><span class="sxs-lookup"><span data-stu-id="e9d7e-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span></span> <span data-ttu-id="e9d7e-107">Para obter um exemplo que mostra como implementar uma operação de forma assíncrona em um serviço, consulte [como implementar uma operação de serviço assíncrono](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="e9d7e-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="e9d7e-108">Para obter mais informações sobre operações síncronas e assíncronas, consulte operações síncronas [e](../synchronous-and-asynchronous-operations.md)assíncronas.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9d7e-109">Não há suporte para o modelo de chamada assíncrona controlado por evento ao usar um <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="e9d7e-110">Para obter informações sobre como fazer chamadas assíncronas usando o <xref:System.ServiceModel.ChannelFactory%601>, consulte [como: chamar operações de forma assíncrona usando uma fábrica de canais](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="e9d7e-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e9d7e-111">Procedimento</span><span class="sxs-lookup"><span data-stu-id="e9d7e-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="e9d7e-112">Para chamar operações do serviço WCF de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="e9d7e-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="e9d7e-113">Execute a ferramenta [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com as opções de comando `/async` e `/tcv:Version35` juntas, conforme mostrado no comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="e9d7e-114">Isso gera, além das operações assíncronas padrão síncronas e baseadas em delegados, uma classe de cliente WCF que contém:</span><span class="sxs-lookup"><span data-stu-id="e9d7e-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="e9d7e-115">Dois <`operationName`>`Async` operações para uso com a abordagem de chamada assíncrona baseada em evento.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="e9d7e-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e9d7e-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="e9d7e-117">A operação conclui eventos do formulário <`operationName`>`Completed` para uso com a abordagem de chamada assíncrona baseada em evento.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="e9d7e-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e9d7e-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="e9d7e-119"><xref:System.EventArgs?displayProperty=nameWithType> tipos para cada operação (do formulário <`operationName`>`CompletedEventArgs`) para uso com a abordagem de chamada assíncrona baseada em evento.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="e9d7e-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e9d7e-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="e9d7e-121">No aplicativo de chamada, crie um método de retorno de chamada a ser chamado quando a operação assíncrona for concluída, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="e9d7e-122">Antes de chamar a operação, use um novo <xref:System.EventHandler%601?displayProperty=nameWithType> genérico do tipo <`operationName`>`EventArgs` para adicionar o método de manipulador (criado na etapa anterior) ao evento <`operationName`>`Completed`.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="e9d7e-123">Em seguida, chame o método <`operationName`>`Async`.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="e9d7e-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e9d7e-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="e9d7e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9d7e-125">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9d7e-126">As diretrizes de design do modelo assíncrono baseado em eventos declaram que, se mais de um valor for retornado, um valor será retornado como a propriedade `Result` e os outros serão retornados como propriedades no objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="e9d7e-127">Um dos resultados disso é que, se um cliente importar metadados usando as opções de comando assíncrono baseadas em eventos e a operação retornar mais de um valor, o objeto de <xref:System.EventArgs> padrão retornará um valor, pois a propriedade `Result` e o resto são propriedades do objeto <xref:System.EventArgs>. Se você quiser receber o objeto Message como a propriedade `Result` e tiver os valores retornados como propriedades nesse objeto, use a opção de comando `/messageContract`.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="e9d7e-128">Isso gera uma assinatura que retorna a mensagem de resposta como a propriedade `Result` no objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="e9d7e-129">Todos os valores de retorno internos são propriedades do objeto da mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="e9d7e-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e9d7e-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="e9d7e-130">See also</span></span>

- [<span data-ttu-id="e9d7e-131">Como implementar uma operação de serviço assíncrona</span><span class="sxs-lookup"><span data-stu-id="e9d7e-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
