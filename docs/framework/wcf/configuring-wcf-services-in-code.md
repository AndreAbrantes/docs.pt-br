---
title: Configurando serviços WCF em código
description: Saiba como você pode configurar os serviços WCF usando código em vez de arquivos de configuração para serviços hospedados internamente e Web.
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 975eafea5a153287f5ccc71b9aa342c12391004e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689973"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="be6ec-103">Configurando serviços WCF em código</span><span class="sxs-lookup"><span data-stu-id="be6ec-103">Configuring WCF Services in Code</span></span>
<span data-ttu-id="be6ec-104">Windows Communication Foundation (WCF) permite que os desenvolvedores configurem serviços usando arquivos de configuração ou código.</span><span class="sxs-lookup"><span data-stu-id="be6ec-104">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="be6ec-105">Os arquivos de configuração são úteis quando um serviço precisa ser configurado depois de ser implantado.</span><span class="sxs-lookup"><span data-stu-id="be6ec-105">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="be6ec-106">Ao usar arquivos de configuração, um profissional de TI apenas precisa atualizar o arquivo de configuração, nenhuma recompilação é necessária.</span><span class="sxs-lookup"><span data-stu-id="be6ec-106">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="be6ec-107">Os arquivos de configuração, porém, podem ser complexos e difíceis de manter.</span><span class="sxs-lookup"><span data-stu-id="be6ec-107">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="be6ec-108">Não há suporte para depurar arquivos de configuração e os elementos de configuração são referenciados por nomes, o que torna os arquivos de configuração de criação sujeitos a erros e difíceis.</span><span class="sxs-lookup"><span data-stu-id="be6ec-108">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="be6ec-109">O WCF também permite que você configure serviços no código.</span><span class="sxs-lookup"><span data-stu-id="be6ec-109">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="be6ec-110">Em versões anteriores do WCF (4,0 e anteriores) a configuração de serviços no código era fácil em cenários de hospedagem interna, a <xref:System.ServiceModel.ServiceHost> classe permitia que você configurasse pontos de extremidade e comportamentos antes de chamar ServiceHost. Open.</span><span class="sxs-lookup"><span data-stu-id="be6ec-110">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="be6ec-111">No entanto, em cenários hospedados na Web, você não tem acesso direto à <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="be6ec-111">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="be6ec-112">Para configurar um serviço Web hospedado, você precisava criar um `System.ServiceModel.ServiceHostFactory` que criou o <xref:System.ServiceModel.Activation.ServiceHostFactory> e executar qualquer configuração necessária.</span><span class="sxs-lookup"><span data-stu-id="be6ec-112">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="be6ec-113">A partir do .NET Framework 4,5, o WCF fornece uma maneira mais fácil de configurar os serviços hospedados internamente e Web no código.</span><span class="sxs-lookup"><span data-stu-id="be6ec-113">Starting with .NET Framework 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>

## <a name="the-configure-method"></a><span data-ttu-id="be6ec-114">O método Configure</span><span class="sxs-lookup"><span data-stu-id="be6ec-114">The Configure method</span></span>
 <span data-ttu-id="be6ec-115">Basta definir um método estático público chamado `Configure` com a assinatura a seguir em sua classe de implementação de serviço:</span><span class="sxs-lookup"><span data-stu-id="be6ec-115">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>

```csharp
public static void Configure(ServiceConfiguration config)
```

 <span data-ttu-id="be6ec-116">O método configure usa uma <xref:System.ServiceModel.ServiceConfiguration> instância que permite ao desenvolvedor adicionar pontos de extremidade e comportamentos.</span><span class="sxs-lookup"><span data-stu-id="be6ec-116">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="be6ec-117">Esse método é chamado pelo WCF antes de o host de serviço ser aberto.</span><span class="sxs-lookup"><span data-stu-id="be6ec-117">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="be6ec-118">Quando definido, quaisquer definições de configuração de serviço especificadas em um arquivo de app.config ou web.config serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="be6ec-118">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>

 <span data-ttu-id="be6ec-119">O trecho de código a seguir ilustra como definir o `Configure` método e adicionar um ponto de extremidade de serviço, um comportamento de ponto de extremidade e comportamentos de serviço:</span><span class="sxs-lookup"><span data-stu-id="be6ec-119">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>

```csharp
public class Service1 : IService1
    {
        public static void Configure(ServiceConfiguration config)
        {
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));
            se.Behaviors.Add(new MyEndpointBehavior());
            config.AddServiceEndpoint(se);

            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });
        }

        public string GetData(int value)
        {
            return $"You entered: {value}";
        }

        public CompositeType GetDataUsingDataContract(CompositeType composite)
        {
            if (composite == null)
            {
                throw new ArgumentNullException("composite");
            }
            if (composite.BoolValue)
            {
                composite.StringValue += "Suffix";
            }
            return composite;
        }
    }
```

 <span data-ttu-id="be6ec-120">Para habilitar um protocolo como https para um serviço, você pode adicionar explicitamente um ponto de extremidade que usa o protocolo ou pode adicionar pontos de extremidades automaticamente chamando ServiceContract. EnableProtocol (Binding), que adiciona um ponto de extremidade para cada endereço base compatível com o protocolo e cada contrato de serviço definido.</span><span class="sxs-lookup"><span data-stu-id="be6ec-120">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="be6ec-121">O código a seguir ilustra como usar o método imconfiguration. EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="be6ec-121">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>

```csharp
public class Service1 : IService1
{
    public string GetData(int value);
    public static void Configure(ServiceConfiguration config)
    {
        // Enable "Add Service Reference" support
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });
       // set up support for http, https, net.tcp, net.pipe
       config.EnableProtocol(new BasicHttpBinding());
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```

 <span data-ttu-id="be6ec-122">As configurações na seção <`protocolMappings`> só serão usadas se nenhum ponto de extremidade do aplicativo for adicionado ao <xref:System.ServiceModel.ServiceConfiguration> programaticamente. Opcionalmente, você pode carregar a configuração de serviço do arquivo de configuração de aplicativo padrão chamando <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> e, em seguida, alterando as configurações.</span><span class="sxs-lookup"><span data-stu-id="be6ec-122">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="be6ec-123">A <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> classe também permite que você carregue a configuração de uma configuração centralizada.</span><span class="sxs-lookup"><span data-stu-id="be6ec-123">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="be6ec-124">O código a seguir ilustra como implementar isso:</span><span class="sxs-lookup"><span data-stu-id="be6ec-124">The following code illustrates how to implement this:</span></span>

```csharp
public class Service1 : IService1
{
    public void DoWork();
    public static void Configure(ServiceConfiguration config)
    {
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="be6ec-125">Observe que o <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignora <`host` configurações de> na <`service`> marca de <`system.serviceModel`>.</span><span class="sxs-lookup"><span data-stu-id="be6ec-125">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="be6ec-126">Conceitualmente, <`host`> é sobre a configuração do host, não a configuração do serviço e é carregada antes da execução do método configure.</span><span class="sxs-lookup"><span data-stu-id="be6ec-126">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>

## <a name="see-also"></a><span data-ttu-id="be6ec-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="be6ec-127">See also</span></span>

- [<span data-ttu-id="be6ec-128">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="be6ec-128">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="be6ec-129">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="be6ec-129">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="be6ec-130">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="be6ec-130">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="be6ec-131">Configuration</span><span class="sxs-lookup"><span data-stu-id="be6ec-131">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="be6ec-132">Ativação com base em configuração no ISS e WAS</span><span class="sxs-lookup"><span data-stu-id="be6ec-132">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="be6ec-133">Configuração e suporte de metadados</span><span class="sxs-lookup"><span data-stu-id="be6ec-133">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="be6ec-134">Configuration</span><span class="sxs-lookup"><span data-stu-id="be6ec-134">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="be6ec-135">Como: especificar uma associação de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="be6ec-135">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="be6ec-136">Como: criar um ponto de extremidade de serviço em configuração</span><span class="sxs-lookup"><span data-stu-id="be6ec-136">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="be6ec-137">Como: publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="be6ec-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="be6ec-138">Como: especificar uma associação de cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="be6ec-138">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
