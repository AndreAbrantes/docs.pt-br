---
title: Configuração do cliente
description: Saiba como usar a configuração do cliente WCF para especificar o endereço, a associação, o comportamento e o contrato de um ponto de extremidade, que é usado para se conectar a um serviço.
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: af9101be0067311fb1a3c0e6e575f186e8ccf161
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265967"
---
# <a name="client-configuration"></a><span data-ttu-id="86abe-103">Configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="86abe-103">Client Configuration</span></span>

<span data-ttu-id="86abe-104">Você pode usar a configuração de cliente do Windows Communication Foundation (WCF) para especificar o endereço, a associação, o comportamento e o contrato, as propriedades "ABC" do ponto de extremidade do cliente, que os clientes usam para se conectar a pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="86abe-104">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="86abe-105">O [\<client>](../../configure-apps/file-schema/wcf/client.md) elemento tem um [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elemento cujos atributos são usados para configurar o ponto de extremidade ABCs.</span><span class="sxs-lookup"><span data-stu-id="86abe-105">The [\<client>](../../configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="86abe-106">Esses atributos são discutidos na seção [Configurando pontos de extremidade](#configuring-endpoints) .</span><span class="sxs-lookup"><span data-stu-id="86abe-106">These attributes are discussed in the [Configuring Endpoints](#configuring-endpoints) section.</span></span>  
  
 <span data-ttu-id="86abe-107">O [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elemento também contém um [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) elemento que é usado para especificar as configurações de importação e exportação de metadados, um [\<headers>](../../configure-apps/file-schema/wcf/headers.md) elemento que contém uma coleção de cabeçalhos de endereço personalizados e um [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elemento que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="86abe-107">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element also contains a [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata, a [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="86abe-108">Os [\<headers>](../../configure-apps/file-schema/wcf/headers.md) [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elementos e são parte do <xref:System.ServiceModel.EndpointAddress> e são discutidos no artigo [endereços](endpoint-addresses.md) .</span><span class="sxs-lookup"><span data-stu-id="86abe-108">The [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](endpoint-addresses.md) article.</span></span> <span data-ttu-id="86abe-109">Links para tópicos que explicam o uso de extensões de metadados são fornecidos na seção [Configurando metadados](#configuring-metadata) .</span><span class="sxs-lookup"><span data-stu-id="86abe-109">Links to topics that explain the use of metadata extensions are provided in the [Configuring Metadata](#configuring-metadata) section.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="86abe-110">Configurando pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="86abe-110">Configuring Endpoints</span></span>  

 <span data-ttu-id="86abe-111">A configuração do cliente foi criada para permitir que o cliente especifique um ou mais pontos de extremidade, cada um com seu próprio nome, endereço e contrato, com cada um referenciando os [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elementos e na configuração do cliente a ser usada para configurar esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="86abe-111">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="86abe-112">O arquivo de configuração do cliente deve ser nomeado "App.config" porque esse é o nome esperado pelo tempo de execução do WCF.</span><span class="sxs-lookup"><span data-stu-id="86abe-112">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="86abe-113">O exemplo a seguir mostra um arquivo de configuração de cliente.</span><span class="sxs-lookup"><span data-stu-id="86abe-113">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
            <!-- Add another endpoint by adding another <endpoint> element. -->
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"
                 bypassProxyOnLocal="false"
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
          <!-- Configure this binding here. -->  
        </binding>  
          </wsHttpBinding>  
     </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="86abe-114">O `name` atributo opcional identifica exclusivamente um ponto de extremidade para um determinado contrato.</span><span class="sxs-lookup"><span data-stu-id="86abe-114">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="86abe-115">Ele é usado pelo <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou pelo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> para especificar qual ponto de extremidade na configuração do cliente está sendo direcionado e deve ser carregado quando um canal é criado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="86abe-115">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="86abe-116">Um nome de configuração de ponto de extremidade curinga " \* " está disponível e indica ao <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> método que ele deve carregar qualquer configuração de ponto de extremidade no arquivo, desde que haja exatamente um disponível e, de outra forma, gere uma exceção.</span><span class="sxs-lookup"><span data-stu-id="86abe-116">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="86abe-117">Se esse atributo for omitido, o ponto de extremidade correspondente será usado como o ponto de extremidade padrão associado ao tipo de contrato especificado.</span><span class="sxs-lookup"><span data-stu-id="86abe-117">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="86abe-118">O valor padrão para o `name` atributo é uma cadeia de caracteres vazia que é igual a qualquer outro nome.</span><span class="sxs-lookup"><span data-stu-id="86abe-118">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="86abe-119">Cada ponto de extremidade deve ter um endereço associado a ele para localizar e identificar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="86abe-119">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="86abe-120">O `address` atributo pode ser usado para especificar a URL que fornece o local do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="86abe-120">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="86abe-121">Mas o endereço para um ponto de extremidade de serviço também pode ser especificado no código criando um Uniform Resource Identifier (URI) e é adicionado ao <xref:System.ServiceModel.ServiceHost> usando um dos <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="86abe-121">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="86abe-122">Para obter mais informações, consulte [endereços](endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="86abe-122">For more information, see [Addresses](endpoint-addresses.md).</span></span> <span data-ttu-id="86abe-123">Como a introdução indica, os [\<headers>](../../configure-apps/file-schema/wcf/headers.md) [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elementos e são parte do <xref:System.ServiceModel.EndpointAddress> e também são discutidos no tópico [endereços](endpoint-addresses.md) .</span><span class="sxs-lookup"><span data-stu-id="86abe-123">As the introduction indicates, the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="86abe-124">O `binding` atributo indica o tipo de associação que o ponto de extremidade espera usar ao se conectar a um serviço.</span><span class="sxs-lookup"><span data-stu-id="86abe-124">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="86abe-125">O tipo deve ter uma seção de configuração registrada se for para ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="86abe-125">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="86abe-126">No exemplo anterior, esta é a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) seção, que indica que o ponto de extremidade usa um <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="86abe-126">In the previous example, this is the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="86abe-127">Mas pode haver mais de uma associação de um determinado tipo que o ponto de extremidade pode usar.</span><span class="sxs-lookup"><span data-stu-id="86abe-127">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="86abe-128">Cada um deles tem seu próprio [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento dentro do elemento do tipo (Associação).</span><span class="sxs-lookup"><span data-stu-id="86abe-128">Each of these has its own [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element within the (binding) type element.</span></span> <span data-ttu-id="86abe-129">O `bindingconfiguration` atributo é usado para distinguir entre associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="86abe-129">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="86abe-130">Seu valor é correspondido com o `name` atributo do [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="86abe-130">Its value is matched with the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span> <span data-ttu-id="86abe-131">Para obter mais informações sobre como configurar uma associação de cliente usando a configuração [do, consulte como especificar uma associação de cliente na configuração](../how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="86abe-131">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="86abe-132">O `behaviorConfiguration` atributo é usado para especificar qual o [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) ponto de extremidade deve usar.</span><span class="sxs-lookup"><span data-stu-id="86abe-132">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="86abe-133">Seu valor é correspondido com o `name` atributo do [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="86abe-133">Its value is matched with the `name` attribute of the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="86abe-134">Para obter um exemplo de como usar a configuração para especificar os comportamentos do cliente, consulte [Configurando comportamentos do cliente](../configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="86abe-134">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="86abe-135">O `contract` atributo especifica qual contrato o ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="86abe-135">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="86abe-136">Esse valor é mapeado para o <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> do <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="86abe-136">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="86abe-137">O valor padrão é o nome completo do tipo da classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="86abe-137">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="86abe-138">Configurando metadados</span><span class="sxs-lookup"><span data-stu-id="86abe-138">Configuring Metadata</span></span>  

 <span data-ttu-id="86abe-139">O [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) elemento é usado para especificar as configurações usadas para registrar extensões de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="86abe-139">The [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="86abe-140">Para obter mais informações sobre como estender o sistema de metadados, consulte [estendendo o sistema de metadados](../extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="86abe-140">For more information about extending the metadata system, see [Extending the Metadata System](../extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86abe-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="86abe-141">See also</span></span>

- [<span data-ttu-id="86abe-142">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="86abe-142">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="86abe-143">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="86abe-143">Configuring Client Behaviors</span></span>](../configuring-client-behaviors.md)
