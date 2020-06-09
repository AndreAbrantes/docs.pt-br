---
title: Rastreamento circular
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 1759db28cb024afc04d02c4b128f96d73aefdd87
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585435"
---
# <a name="circular-tracing"></a><span data-ttu-id="20786-102">Rastreamento circular</span><span class="sxs-lookup"><span data-stu-id="20786-102">Circular Tracing</span></span>

<span data-ttu-id="20786-103">Este exemplo demonstra a implementação de um ouvinte de rastreamento de buffer circular.</span><span class="sxs-lookup"><span data-stu-id="20786-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="20786-104">Um cenário comum para os serviços de produção é ter serviços disponíveis por longos períodos de tempo e ter o log de rastreamento habilitado em um nível baixo.</span><span class="sxs-lookup"><span data-stu-id="20786-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="20786-105">Esses serviços consomem muito espaço em disco.</span><span class="sxs-lookup"><span data-stu-id="20786-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="20786-106">Ao solucionar problemas de um serviço, os dados mais recentes no log de rastreamento são relevantes para resolver um problema.</span><span class="sxs-lookup"><span data-stu-id="20786-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="20786-107">Este exemplo demonstra uma implementação de um ouvinte de rastreamento de buffer circular no qual apenas os rastreamentos mais recentes são mantidos em disco até uma quantidade configurável de dados.</span><span class="sxs-lookup"><span data-stu-id="20786-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="20786-108">Este exemplo é baseado na [introdução](getting-started-sample.md) e inclui um ouvinte de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="20786-108">This sample is based on the [Getting Started](getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="20786-109">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="20786-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="20786-110">Este exemplo pressupõe que você esteja familiarizado com o [rastreamento e](tracing-and-message-logging.md) a amostra de log de mensagens e leu a documentação fornecida para o exemplo de [rastreamento e log de mensagens](tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="20786-110">This sample assumes that you are familiar with the [Tracing and Message Logging](tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="20786-111">Ouvinte de rastreamento de buffer circular</span><span class="sxs-lookup"><span data-stu-id="20786-111">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="20786-112">O conceito por trás da implementação do ouvinte de rastreamento de buffer circular é ter dois arquivos que podem armazenar até metade do total de dados de log de rastreamento desejado.</span><span class="sxs-lookup"><span data-stu-id="20786-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="20786-113">O ouvinte cria um arquivo e grava nesse arquivo até atingir o limite de metade do tamanho dos dados, em que ponto ele alterna para um segundo arquivo.</span><span class="sxs-lookup"><span data-stu-id="20786-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="20786-114">Quando o ouvinte atinge o limite do segundo arquivo, ele substitui o primeiro arquivo por novos rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="20786-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="20786-115">Esse ouvinte deriva de `XmlWriteTraceListener` e permite que os logs sejam exibidos com a [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="20786-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="20786-116">Ao tentar exibir os logs, os dois arquivos de log podem ser facilmente recombinados abrindo-se ambos os arquivos de log ao mesmo tempo na ferramenta do Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="20786-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="20786-117">A ferramenta Visualizador de rastreamento de serviço cuida automaticamente da classificação dos rastreamentos para que eles apareçam na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="20786-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="20786-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="20786-118">Configuration</span></span>

<span data-ttu-id="20786-119">Um serviço pode ser configurado para usar o ouvinte de rastreamento de buffer circular adicionando o código a seguir para um ouvinte e elementos de origem.</span><span class="sxs-lookup"><span data-stu-id="20786-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="20786-120">O tamanho máximo do arquivo é especificado definindo o `maxFileSizeKB` atributo na configuração do ouvinte de rastreamento circular.</span><span class="sxs-lookup"><span data-stu-id="20786-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="20786-121">Isso é demonstrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="20786-121">This is demonstrated in the following code.</span></span>

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">
      <listeners>
        <add name="CircularTraceListener" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />
  </sharedListeners>
  <trace autoflush="true" />
</system.diagnostics>
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20786-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="20786-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="20786-123">Certifique-se de ter executado o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20786-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="20786-124">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20786-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="20786-125">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20786-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20786-126">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="20786-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="20786-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="20786-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="20786-128">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="20786-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20786-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="20786-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="20786-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20786-130">See also</span></span>

- <span data-ttu-id="20786-131">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="20786-131">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
