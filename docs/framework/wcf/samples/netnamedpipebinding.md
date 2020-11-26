---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: 46365c8dbfee66d719b114947f6b04069e0f8870
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235293"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="b31d1-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="b31d1-102">NetNamedPipeBinding</span></span>

<span data-ttu-id="b31d1-103">Este exemplo demonstra a `netNamedPipeBinding` associação, que fornece comunicação entre processos no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="b31d1-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="b31d1-104">Pipes nomeados não funcionam entre computadores.</span><span class="sxs-lookup"><span data-stu-id="b31d1-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="b31d1-105">Este exemplo é baseado no serviço de calculadora de [introdução](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="b31d1-105">This sample is based on The [Getting Started](getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="b31d1-106">Neste exemplo, o serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="b31d1-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="b31d1-107">O cliente e o serviço são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="b31d1-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b31d1-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b31d1-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b31d1-109">A associação é especificada nos arquivos de configuração para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="b31d1-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="b31d1-110">O tipo de associação é especificado no `binding` atributo do [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elemento ou [ \<endpoint> \<client> ](../../configure-apps/file-schema/wcf/endpoint-of-client.md) , conforme mostrado na seguinte configuração de exemplo:</span><span class="sxs-lookup"><span data-stu-id="b31d1-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b31d1-111">O exemplo anterior mostra como configurar um ponto de extremidade para usar a `netNamedPipeBinding` associação com as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="b31d1-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="b31d1-112">Se você quiser configurar a `netNamedPipeBinding` associação e alterar algumas de suas configurações, deverá definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="b31d1-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="b31d1-113">O ponto de extremidade deve referenciar a configuração de associação por nome com um `bindingConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="b31d1-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b31d1-114">Neste exemplo, a configuração de associação é nomeada `Binding1` e tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="b31d1-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="b31d1-115">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="b31d1-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b31d1-116">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b31d1-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b31d1-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b31d1-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b31d1-118">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b31d1-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b31d1-119">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b31d1-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b31d1-120">Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b31d1-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b31d1-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b31d1-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b31d1-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b31d1-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b31d1-123">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b31d1-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b31d1-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b31d1-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
