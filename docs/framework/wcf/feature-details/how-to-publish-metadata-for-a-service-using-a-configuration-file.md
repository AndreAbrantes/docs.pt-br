---
title: Como publicar metadados para um serviço usando um arquivo de configuração
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 976e1e0bb2c6479f7599165a1c6fe83bae4e17c1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596975"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="710b9-102">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="710b9-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="710b9-103">Este é um dos dois tópicos de instruções que demonstram a publicação de metadados para um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="710b9-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="710b9-104">Há duas maneiras de especificar como um serviço deve publicar metadados, usando um arquivo de configuração e usando código.</span><span class="sxs-lookup"><span data-stu-id="710b9-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="710b9-105">Este tópico mostra como publicar metadados para um serviço usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="710b9-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="710b9-106">Este tópico mostra como publicar metadados de maneira não segura.</span><span class="sxs-lookup"><span data-stu-id="710b9-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="710b9-107">Qualquer cliente pode recuperar os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="710b9-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="710b9-108">Se você precisar que seu serviço publique metadados de maneira segura, consulte [ponto de extremidade de metadados seguro personalizado](../samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="710b9-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="710b9-109">Para obter mais informações sobre como publicar metadados no código, consulte [como publicar metadados para um serviço usando código](how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="710b9-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="710b9-110">A publicação de metadados permite que os clientes recuperem os metadados usando uma solicitação WS-Transfer GET ou uma solicitação HTTP/GET usando a `?wsdl` cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="710b9-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="710b9-111">Para ter certeza de que o código está funcionando, crie um serviço WCF básico.</span><span class="sxs-lookup"><span data-stu-id="710b9-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="710b9-112">Para simplificar, um serviço auto-hospedado básico é fornecido no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="710b9-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="710b9-113">Esse serviço é um serviço hospedado automaticamente, que é configurado usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="710b9-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="710b9-114">O arquivo de configuração a seguir serve como ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="710b9-114">The following configuration file serves as a starting point.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="710b9-115">Para publicar metadados para um serviço WCF usando um arquivo de configuração de aplicativo</span><span class="sxs-lookup"><span data-stu-id="710b9-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="710b9-116">No arquivo app. config, após o elemento de fechamento `</services>` , crie um `<behaviors>` elemento.</span><span class="sxs-lookup"><span data-stu-id="710b9-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="710b9-117">Dentro do elemento `<behaviors>`, adicione um elemento `<serviceBehaviors>`.</span><span class="sxs-lookup"><span data-stu-id="710b9-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="710b9-118">Adicione um `<behavior>` elemento ao `<serviceBehaviors>` elemento e especifique um valor para o `name` atributo do `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="710b9-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="710b9-119">Adicione um `<serviceMetadata>` elemento ao `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="710b9-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="710b9-120">Defina o `httpGetEnabled` atributo como `true` e o `policyVersion` atributo como Policy15.</span><span class="sxs-lookup"><span data-stu-id="710b9-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="710b9-121">`httpGetEnabled`permite que o serviço responda a solicitações de metadados feitas por uma solicitação HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="710b9-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="710b9-122">`policyVersion`instrui o serviço a estar em conformidade com o WS-Policy 1,5 ao gerar metadados.</span><span class="sxs-lookup"><span data-stu-id="710b9-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="710b9-123">Adicione um `behaviorConfiguration` atributo ao `<service>` elemento e especifique o `name` atributo do `<behavior>` elemento adicionado na etapa 1, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="710b9-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. <span data-ttu-id="710b9-124">Adicione um ou mais `<endpoint>` elementos com o contrato definido como `IMetadataExchange` , conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="710b9-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. <span data-ttu-id="710b9-125">Para os pontos de extremidade de metadados adicionados na etapa anterior, defina o `binding` atributo como um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="710b9-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="710b9-126">`mexHttpBinding`para publicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="710b9-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="710b9-127">`mexHttpsBinding`para publicação HTTPS.</span><span class="sxs-lookup"><span data-stu-id="710b9-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="710b9-128">`mexNamedPipeBinding`para publicação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="710b9-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="710b9-129">`mexTcpBinding`para publicação de TCP.</span><span class="sxs-lookup"><span data-stu-id="710b9-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="710b9-130">Para os pontos de extremidade de metadados adicionados em uma etapa anterior, defina o endereço igual a:</span><span class="sxs-lookup"><span data-stu-id="710b9-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="710b9-131">Uma cadeia de caracteres vazia para usar o endereço base do aplicativo host como o ponto de publicação se o endereço base for o mesmo que a associação de metadados.</span><span class="sxs-lookup"><span data-stu-id="710b9-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="710b9-132">Um endereço relativo se o aplicativo host tiver um endereço base.</span><span class="sxs-lookup"><span data-stu-id="710b9-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="710b9-133">Um endereço absoluto.</span><span class="sxs-lookup"><span data-stu-id="710b9-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="710b9-134">Crie e execute o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="710b9-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="710b9-135">Use o Internet Explorer para navegar até o endereço base do serviço ( `http://localhost:8001/MetadataSample` neste exemplo) e verificar se a publicação de metadados está ativada.</span><span class="sxs-lookup"><span data-stu-id="710b9-135">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="710b9-136">Caso contrário, uma mensagem na parte superior da página resultante será exibida: "a publicação de metadados para este serviço está atualmente desabilitada".</span><span class="sxs-lookup"><span data-stu-id="710b9-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="710b9-137">Para usar pontos de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="710b9-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="710b9-138">Para configurar metadados em um serviço que usa pontos de extremidade padrão, especifique o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> no arquivo de configuração como no exemplo anterior, mas não especifique nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="710b9-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="710b9-139">O arquivo de configuração teria a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="710b9-139">The configuration file would then look like this.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="710b9-140">Como o serviço tem um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> com o `httpGetEnabled` definido como `true` , o serviço tem metadados de publicação habilitados e, como nenhum ponto de extremidade foi explicitamente adicionado, o tempo de execução adiciona os pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="710b9-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="710b9-141">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../simplified-configuration.md) e [Configuração simplificada para serviços WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="710b9-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="710b9-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="710b9-142">Example</span></span>  
 <span data-ttu-id="710b9-143">O exemplo de código a seguir mostra a implementação de um serviço WCF básico e o arquivo de configuração que publica metadados para o serviço.</span><span class="sxs-lookup"><span data-stu-id="710b9-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="710b9-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="710b9-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="710b9-145">Como hospedar um serviço do WCF em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="710b9-145">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="710b9-146">Self-Host</span><span class="sxs-lookup"><span data-stu-id="710b9-146">Self-Host</span></span>](../samples/self-host.md)
- [<span data-ttu-id="710b9-147">Visão geral da arquitetura de metadados</span><span class="sxs-lookup"><span data-stu-id="710b9-147">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="710b9-148">Utilizando metadados</span><span class="sxs-lookup"><span data-stu-id="710b9-148">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="710b9-149">Como publicar metadados utilizando código para um serviço</span><span class="sxs-lookup"><span data-stu-id="710b9-149">How to: Publish Metadata for a Service Using Code</span></span>](how-to-publish-metadata-for-a-service-using-code.md)
