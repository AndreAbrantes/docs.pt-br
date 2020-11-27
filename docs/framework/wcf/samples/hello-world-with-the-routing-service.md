---
title: Olá Mundo com o serviço de roteamento
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 3d91634d72481427f04e958f6dc2734829b6158b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253850"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="93d9b-102">Olá Mundo com o serviço de roteamento</span><span class="sxs-lookup"><span data-stu-id="93d9b-102">Hello World with the Routing Service</span></span>

<span data-ttu-id="93d9b-103">Este exemplo demonstra o serviço de roteamento do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="93d9b-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="93d9b-104">O serviço de roteamento é um componente WCF que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93d9b-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="93d9b-105">Este exemplo adapta a amostra de calculadora padrão do WCF para se comunicar usando o serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="93d9b-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="93d9b-106">Neste exemplo, o cliente da calculadora está configurado para enviar mensagens para um ponto de extremidade exposto pelo roteador.</span><span class="sxs-lookup"><span data-stu-id="93d9b-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="93d9b-107">O serviço de roteamento é configurado para aceitar todas as mensagens enviadas a ele e encaminhá-las a um ponto de extremidade que corresponde ao serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="93d9b-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="93d9b-108">Portanto, as mensagens enviadas do cliente são recebidas pelo roteador e roteadas novamente para o serviço de calculadora real.</span><span class="sxs-lookup"><span data-stu-id="93d9b-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="93d9b-109">As mensagens do serviço de calculadora são enviadas de volta para o roteador, que, por sua vez, passa-as de volta para o cliente da calculadora.</span><span class="sxs-lookup"><span data-stu-id="93d9b-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="93d9b-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="93d9b-110">To use this sample</span></span>

1. <span data-ttu-id="93d9b-111">Usando o Visual Studio 2012, abra HelloRoutingService. sln.</span><span class="sxs-lookup"><span data-stu-id="93d9b-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="93d9b-112">Pressione F5 ou CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="93d9b-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="93d9b-113">Se você pressionar F5, o cliente da calculadora será iniciado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="93d9b-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="93d9b-114">Se você pressionar CTRL + SHIFT + B (Build), deverá iniciar os aplicativos a seguir por conta própria.</span><span class="sxs-lookup"><span data-stu-id="93d9b-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="93d9b-115">Cliente de calculadora (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="93d9b-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="93d9b-116">Serviço de calculadora (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="93d9b-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="93d9b-117">Serviço de roteamento (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="93d9b-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="93d9b-118">Pressione ENTER para iniciar o cliente.</span><span class="sxs-lookup"><span data-stu-id="93d9b-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="93d9b-119">Você deve ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="93d9b-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="93d9b-120">Configurável por meio de código ou App.Config</span><span class="sxs-lookup"><span data-stu-id="93d9b-120">Configurable via Code or App.Config</span></span>

 <span data-ttu-id="93d9b-121">O exemplo é fornecido configurado para usar um arquivo de App.config para definir o comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="93d9b-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="93d9b-122">Você também pode alterar o nome do arquivo de App.config para algo diferente para que ele não seja reconhecido e remova o comentário da chamada de método para ConfigureRouterViaCode ().</span><span class="sxs-lookup"><span data-stu-id="93d9b-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="93d9b-123">O método resulta no mesmo comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="93d9b-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="93d9b-124">Cenário</span><span class="sxs-lookup"><span data-stu-id="93d9b-124">Scenario</span></span>

 <span data-ttu-id="93d9b-125">Este exemplo demonstra o roteador que atua como uma bomba básica de mensagem.</span><span class="sxs-lookup"><span data-stu-id="93d9b-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="93d9b-126">O serviço de roteamento atua como um nó de proxy transparente configurado para passar mensagens diretamente para um conjunto pré-configurado de pontos de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="93d9b-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="93d9b-127">Cenário do mundo real</span><span class="sxs-lookup"><span data-stu-id="93d9b-127">Real World Scenario</span></span>

 <span data-ttu-id="93d9b-128">A contoso deseja aumentar a flexibilidade que tem na nomenclatura, no endereçamento, na configuração e na segurança de seus serviços.</span><span class="sxs-lookup"><span data-stu-id="93d9b-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="93d9b-129">Para fazer isso, eles colocam uma bomba básica de mensagens na frente de seus serviços para atuar como um ponto de extremidade voltado para o público.</span><span class="sxs-lookup"><span data-stu-id="93d9b-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="93d9b-130">Isso permite que eles coloquem segurança adicional na frente de seus serviços reais e facilitam a implementação de soluções expandidas ou controle de versão de serviço em uma data posterior.</span><span class="sxs-lookup"><span data-stu-id="93d9b-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93d9b-131">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="93d9b-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="93d9b-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="93d9b-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="93d9b-133">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="93d9b-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93d9b-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="93d9b-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="93d9b-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="93d9b-135">See also</span></span>

- <span data-ttu-id="93d9b-136">[Hospedagem de AppFabric e persistência Exemplos](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="93d9b-136">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
