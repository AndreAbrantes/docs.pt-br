---
title: Vários contratos
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: e8451c49395a1dad55c5afca419f47a8e856b61f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602499"
---
# <a name="multiple-contracts"></a><span data-ttu-id="1ce86-102">Vários contratos</span><span class="sxs-lookup"><span data-stu-id="1ce86-102">Multiple Contracts</span></span>
<span data-ttu-id="1ce86-103">O exemplo de vários contratos demonstra como implementar mais de um contrato em um serviço e como configurar pontos de extremidade para se comunicar com cada um dos contratos implementados.</span><span class="sxs-lookup"><span data-stu-id="1ce86-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="1ce86-104">Este exemplo é baseado na [introdução](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1ce86-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="1ce86-105">O serviço foi modificado para definir dois contratos, o `ICalculator` contrato e o `ICalculatorSession` contrato.</span><span class="sxs-lookup"><span data-stu-id="1ce86-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ce86-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1ce86-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1ce86-107">A classe de serviço implementa os `ICalculator` `ICalculatorSession` contratos e.</span><span class="sxs-lookup"><span data-stu-id="1ce86-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="1ce86-108">Como um dos contratos requer uma sessão, o serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o estado durante o tempo de vida da sessão.</span><span class="sxs-lookup"><span data-stu-id="1ce86-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="1ce86-109">A configuração de serviço foi modificada para definir dois pontos de extremidade para expor cada contrato.</span><span class="sxs-lookup"><span data-stu-id="1ce86-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="1ce86-110">O `ICalculator` ponto de extremidade é exposto no endereço base usando um `basicHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="1ce86-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="1ce86-111">O `ICalculatorSession` ponto de extremidade é exposto no BaseAddress/Session usando um `wsHttpBinding` com o `bindingConfiguration` atributo definido como `BindingWithSession` , conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="1ce86-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="1ce86-112">O código do cliente gerado agora inclui uma classe de cliente para o `ICalculator` contrato original e para o novo `ICalculatorSession` contrato.</span><span class="sxs-lookup"><span data-stu-id="1ce86-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="1ce86-113">A configuração do cliente e o código foram modificados para se comunicar com cada contrato no ponto de extremidade de serviço apropriado.</span><span class="sxs-lookup"><span data-stu-id="1ce86-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="1ce86-114">O cliente é um aplicativo do Windows do console (. exe).</span><span class="sxs-lookup"><span data-stu-id="1ce86-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="1ce86-115">O serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="1ce86-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="1ce86-116">A janela do console do cliente exibe as operações enviadas para cada um dos pontos de extremidade, primeiro o ponto final básico, seguido pelo ponto de extremidade seguro.</span><span class="sxs-lookup"><span data-stu-id="1ce86-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1ce86-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1ce86-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1ce86-118">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1ce86-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1ce86-119">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1ce86-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1ce86-120">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1ce86-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1ce86-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1ce86-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1ce86-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1ce86-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1ce86-123">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1ce86-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1ce86-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1ce86-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
