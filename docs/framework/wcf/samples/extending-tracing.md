---
title: Estendendo rastreamento
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: e61265210640d2b801ad55b9dc5a357cc4f161a7
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728391"
---
# <a name="extend-tracing"></a><span data-ttu-id="7f699-102">Estender rastreamento</span><span class="sxs-lookup"><span data-stu-id="7f699-102">Extend tracing</span></span>

<span data-ttu-id="7f699-103">Este exemplo demonstra como estender o recurso de rastreamento de Windows Communication Foundation (WCF) gravando rastreamentos de atividade definidos pelo usuário no código do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="7f699-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="7f699-104">A gravação de rastreamentos de atividade definidos pelo usuário permite que o usuário crie atividades de rastreamento e rastreamentos de grupo em unidades lógicas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7f699-104">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="7f699-105">Também é possível correlacionar atividades por meio de transferências (dentro do mesmo ponto de extremidade) e da propagação (entre pontos de extremidade).</span><span class="sxs-lookup"><span data-stu-id="7f699-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="7f699-106">Neste exemplo, o rastreamento está habilitado para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="7f699-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="7f699-107">Para obter mais informações sobre como habilitar o rastreamento em arquivos de configuração de cliente e serviço, consulte [rastreamento e log de mensagens](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="7f699-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="7f699-108">Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7f699-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f699-109">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="7f699-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7f699-110">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7f699-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7f699-111">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7f699-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7f699-112">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="7f699-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7f699-113">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7f699-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="7f699-114">Rastreamento e propagação de atividade</span><span class="sxs-lookup"><span data-stu-id="7f699-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="7f699-115">O rastreamento de atividade definido pelo usuário permite que o usuário crie suas próprias atividades de rastreamento para agrupar rastreamentos em unidades lógicas de trabalho, correlacionar atividades por meio de transferências e propagação e diminuir o custo de desempenho do rastreamento do WCF (por exemplo, o custo de espaço em disco de um arquivo de log).</span><span class="sxs-lookup"><span data-stu-id="7f699-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="7f699-116">Adicionar fontes personalizadas</span><span class="sxs-lookup"><span data-stu-id="7f699-116">Add custom sources</span></span>  
 <span data-ttu-id="7f699-117">Os rastreamentos definidos pelo usuário podem ser adicionados ao código do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="7f699-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="7f699-118">A adição de fontes de rastreamento aos arquivos de configuração do cliente ou do serviço permite que esses rastreamentos personalizados sejam registrados e exibidos na [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7f699-118">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="7f699-119">O código a seguir mostra como adicionar uma fonte de rastreamento definida pelo usuário `ServerCalculatorTraceSource` chamada ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7f699-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="7f699-120">Correlacionar atividades</span><span class="sxs-lookup"><span data-stu-id="7f699-120">Correlate activities</span></span>  
 <span data-ttu-id="7f699-121">Para correlacionar atividades diretamente entre pontos de extremidade, `propagateActivity` o atributo deve ser definido `true` como na `System.ServiceModel` origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7f699-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="7f699-122">Além disso, para propagar rastreamentos sem passar pelas atividades do WCF, o rastreamento de atividade de ServiceModel deve ser desativado.</span><span class="sxs-lookup"><span data-stu-id="7f699-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="7f699-123">Isso pode ser visto no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7f699-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f699-124">Desativar o rastreamento de atividade de ServiceModel não é o mesmo que ter o nível de rastreamento, indicado pela `switchValue` Propriedade, definido como desativado.</span><span class="sxs-lookup"><span data-stu-id="7f699-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="7f699-125">Reduzir o custo de desempenho</span><span class="sxs-lookup"><span data-stu-id="7f699-125">Lessen performance cost</span></span>  
 <span data-ttu-id="7f699-126">Definir `ActivityTracing` como off na origem `System.ServiceModel` do rastreamento gera um arquivo de rastreamento que contém apenas rastreamentos de atividade definidos pelo usuário, sem nenhum dos rastreamentos de atividade de ServiceModel incluídos.</span><span class="sxs-lookup"><span data-stu-id="7f699-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="7f699-127">A exclusão de rastreamentos de atividade de ServiceModel resulta em um arquivo de log muito menor.</span><span class="sxs-lookup"><span data-stu-id="7f699-127">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="7f699-128">No entanto, a oportunidade de correlacionar rastreamentos de processamento do WCF é perdida.</span><span class="sxs-lookup"><span data-stu-id="7f699-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="7f699-129">Configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7f699-129">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7f699-130">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f699-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7f699-131">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f699-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7f699-132">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f699-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f699-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f699-133">See also</span></span>

- <span data-ttu-id="7f699-134">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7f699-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
