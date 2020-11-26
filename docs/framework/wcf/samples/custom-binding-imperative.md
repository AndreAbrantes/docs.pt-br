---
title: Associação personalizada obrigatória
ms.date: 03/30/2017
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
ms.openlocfilehash: 6be5105831fa3845db9a55a14a7ed8821dc1cbc4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241909"
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="2fe8f-102">Associação personalizada obrigatória</span><span class="sxs-lookup"><span data-stu-id="2fe8f-102">Custom Binding Imperative</span></span>

<span data-ttu-id="2fe8f-103">O exemplo demonstra como escrever código imperativo para definir e usar associações personalizadas sem usar um arquivo de configuração ou um cliente do Windows Communication Foundation (WCF) gerado.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-103">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a Windows Communication Foundation (WCF) generated client.</span></span> <span data-ttu-id="2fe8f-104">Este exemplo combina os recursos fornecidos pelo transporte HTTP e o canal de sessão confiável para criar uma associação baseada em HTTP confiável.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-104">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="2fe8f-105">Este exemplo é baseado no [introdução](getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fe8f-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2fe8f-107">No cliente e no serviço, é criada uma associação personalizada que contém dois elementos de ligação (sessão confiável e HTTP):</span><span class="sxs-lookup"><span data-stu-id="2fe8f-107">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="2fe8f-108">No serviço, a associação é usada adicionando um ponto de extremidade ao ServiceHost:</span><span class="sxs-lookup"><span data-stu-id="2fe8f-108">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="2fe8f-109">No cliente, a associação é usada por um <xref:System.ServiceModel.ChannelFactory> para criar um canal para o serviço:</span><span class="sxs-lookup"><span data-stu-id="2fe8f-109">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="2fe8f-110">Esse canal é usado para interagir com o serviço:</span><span class="sxs-lookup"><span data-stu-id="2fe8f-110">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="2fe8f-111">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2fe8f-112">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-112">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2fe8f-113">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2fe8f-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2fe8f-114">Certifique-se de ter executado o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fe8f-114">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2fe8f-115">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fe8f-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2fe8f-116">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fe8f-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2fe8f-117">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2fe8f-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2fe8f-119">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fe8f-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2fe8f-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="2fe8f-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="2fe8f-121">See also</span></span>

- [<span data-ttu-id="2fe8f-122">Exemplos de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="2fe8f-122">Custom Binding Samples</span></span>](custom-binding.md)
