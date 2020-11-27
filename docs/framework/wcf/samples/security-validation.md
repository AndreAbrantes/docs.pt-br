---
title: Validação de segurança
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 1260aaa756e7be33ce2aa1bcce5fc79be553c990
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262613"
---
# <a name="security-validation"></a><span data-ttu-id="facc2-102">Validação de segurança</span><span class="sxs-lookup"><span data-stu-id="facc2-102">Security validation</span></span>

<span data-ttu-id="facc2-103">Este exemplo demonstra como usar um comportamento personalizado para validar serviços em um computador para garantir que eles atendam a critérios específicos.</span><span class="sxs-lookup"><span data-stu-id="facc2-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="facc2-104">Neste exemplo, os serviços são validados pelo comportamento personalizado examinando cada ponto de extremidade no serviço e verificando se eles contêm elementos de associação seguros.</span><span class="sxs-lookup"><span data-stu-id="facc2-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="facc2-105">Este exemplo é baseado na [introdução](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="facc2-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="facc2-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="facc2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="facc2-107">Comportamento personalizado de validação do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="facc2-107">Endpoint Validation Custom Behavior</span></span>  

 <span data-ttu-id="facc2-108">Ao adicionar o código de usuário ao `Validate` método contido na <xref:System.ServiceModel.Description.IServiceBehavior> interface, o comportamento personalizado pode ser dado a um serviço ou ponto de extremidade para executar ações definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="facc2-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="facc2-109">O código a seguir é usado para executar um loop por meio de cada ponto de extremidade contido em um serviço, que pesquisa suas coleções de associação para associações seguras.</span><span class="sxs-lookup"><span data-stu-id="facc2-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="facc2-110">Adicionar o código a seguir ao arquivo Web.config adiciona a `serviceValidate` extensão de comportamento para o serviço reconhecer.</span><span class="sxs-lookup"><span data-stu-id="facc2-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>
    ...
</system.serviceModel>
```  
  
 <span data-ttu-id="facc2-111">Depois que a extensão de comportamento é adicionada ao serviço, agora é possível adicionar o `endpointValidate` comportamento à lista de comportamentos no arquivo de Web.config e, portanto, ao serviço.</span><span class="sxs-lookup"><span data-stu-id="facc2-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="facc2-112">Os comportamentos e suas extensões que são adicionados ao arquivo de Web.config aplicam o comportamento a serviços individuais, enquanto quando adicionados ao arquivo de Machine.config aplicam o comportamento a cada serviço ativo no computador.</span><span class="sxs-lookup"><span data-stu-id="facc2-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="facc2-113">Ao adicionar o comportamento a todos os serviços, é recomendável fazer backup do arquivo de Machine.config antes de fazer qualquer alteração.</span><span class="sxs-lookup"><span data-stu-id="facc2-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="facc2-114">Agora, execute o cliente fornecido no diretório client\bin deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="facc2-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="facc2-115">Uma exceção é lançada com a seguinte mensagem: "o serviço solicitado, ' http://localhost/servicemodelsamples/service.svc ' não pôde ser ativado."</span><span class="sxs-lookup"><span data-stu-id="facc2-115">An exception is thrown with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="facc2-116">Isso é esperado porque um ponto de extremidade é considerado inseguro pelo comportamento de validação do ponto de extremidade e impede que o serviço seja iniciado.</span><span class="sxs-lookup"><span data-stu-id="facc2-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="facc2-117">O comportamento também gera uma exceção interna que descreve qual ponto de extremidade é inseguro e grava uma mensagem no sistema Visualizador de Eventos na origem "System. ServiceModel 4.0.0.0" e na categoria "Webhost".</span><span class="sxs-lookup"><span data-stu-id="facc2-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="facc2-118">Também é possível ativar o rastreamento no serviço neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="facc2-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="facc2-119">Isso permite que o usuário exiba as exceções geradas pelo comportamento de validação de ponto de extremidade abrindo os rastreamentos de serviço resultantes usando a ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="facc2-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
### <a name="view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="facc2-120">Exibir mensagens de exceção de validação de ponto de extremidade com falha no Visualizador de Eventos</span><span class="sxs-lookup"><span data-stu-id="facc2-120">View failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="facc2-121">Clique no menu **Iniciar** e selecione **executar...**.</span><span class="sxs-lookup"><span data-stu-id="facc2-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="facc2-122">Digite `eventvwr` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="facc2-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="facc2-123">Na janela Visualizador de Eventos, clique em **aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="facc2-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="facc2-124">Clique duas vezes no evento "System. ServiceModel 4.0.0.0" recentemente adicionado na categoria "Webhost" na janela do **aplicativo** para exibir mensagens de ponto de extremidade inseguras.</span><span class="sxs-lookup"><span data-stu-id="facc2-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="facc2-125">Configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="facc2-125">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="facc2-126">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="facc2-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="facc2-127">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="facc2-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="facc2-128">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="facc2-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="facc2-129">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="facc2-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="facc2-130">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="facc2-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="facc2-131">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="facc2-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="facc2-132">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="facc2-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="facc2-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="facc2-133">See also</span></span>

- <span data-ttu-id="facc2-134">[AppFabric que monitora Exemplos](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="facc2-134">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
