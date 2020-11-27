---
title: Endereçando
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 77a1321f2babb93ab39eeac944de06fc8c2634c3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249690"
---
# <a name="addressing"></a><span data-ttu-id="5cbfc-102">Endereçando</span><span class="sxs-lookup"><span data-stu-id="5cbfc-102">Addressing</span></span>

<span data-ttu-id="5cbfc-103">O exemplo de endereçamento demonstra vários aspectos e recursos de endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="5cbfc-104">O exemplo é baseado na [introdução](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5cbfc-104">The sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="5cbfc-105">Neste exemplo, o serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="5cbfc-106">O serviço e o cliente são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="5cbfc-107">O serviço define vários pontos de extremidade usando uma combinação de endereços de ponto de extremidades relativos e absolutos.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cbfc-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5cbfc-109">O arquivo de configuração de serviço especifica um endereço base e quatro pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="5cbfc-110">O endereço base é especificado usando o elemento add, em Service/host/baseAddresss, conforme demonstrado na configuração de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="5cbfc-111">A primeira definição de ponto de extremidade mostrada na seguinte configuração de exemplo especifica um endereço relativo, o que significa que o endereço do ponto de extremidade é uma combinação do endereço base e do endereço relativo seguindo as regras de composição de URI.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="5cbfc-112">Nesse caso, o endereço relativo está vazio (""), portanto, o endereço do ponto de extremidade é o mesmo que o endereço base.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="5cbfc-113">O endereço do ponto de extremidade real é `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="5cbfc-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="5cbfc-114">A segunda definição de ponto de extremidade também especifica um endereço relativo, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="5cbfc-115">O endereço relativo, "Test", é anexado ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="5cbfc-116">O endereço do ponto de extremidade real é `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="5cbfc-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="5cbfc-117">A terceira definição de ponto de extremidade especifica um endereço absoluto, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="5cbfc-118">O endereço base não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-118">The base address plays no role in the address.</span></span> <span data-ttu-id="5cbfc-119">O endereço do ponto de extremidade real é `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="5cbfc-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="5cbfc-120">O quarto endereço do ponto de extremidade especifica um endereço absoluto e um transporte diferente — TCP.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="5cbfc-121">O endereço base não desempenha nenhuma função no endereço.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-121">The base address plays no role in the address.</span></span> <span data-ttu-id="5cbfc-122">O endereço do ponto de extremidade real é `net.tcp://localhost:9000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="5cbfc-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="5cbfc-123">O cliente acessa apenas um dos quatro pontos de extremidade de serviço, mas todos os quatro são definidos em seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="5cbfc-124">O cliente seleciona um ponto de extremidade quando cria o `CalculatorProxy` objeto.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="5cbfc-125">Ao alterar o nome da configuração de `CalculatorEndpoint1` até o `CalculatorEndpoint4` , você pode exercitar cada um dos pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="5cbfc-126">Quando você executa o exemplo, o serviço enumera o endereço, o nome da associação e o nome do contrato para cada um de seus pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="5cbfc-127">O ponto de extremidade de intercâmbio de metadados (MEX) é apenas outro ponto de extremidade da perspectiva do ServiceHost, então ele aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```console  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="5cbfc-128">Quando você executa o cliente do, as solicitações de operação e as respostas são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5cbfc-129">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5cbfc-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5cbfc-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5cbfc-131">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cbfc-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5cbfc-132">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cbfc-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5cbfc-133">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cbfc-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5cbfc-134">Se você usar Svcutil.exe para regenerar a configuração para este exemplo, certifique-se de modificar o nome do ponto de extremidade na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5cbfc-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5cbfc-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5cbfc-137">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5cbfc-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5cbfc-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
