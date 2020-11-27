---
title: Segurança de transporte com autenticação básica
description: Examine este cenário WCF, que mostra a autenticação básica para um serviço e cliente WCF. O serviço precisa de um certificado válido que o cliente confie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: e821f8ed3996e9119c6f2c06ec6533c575bf75dd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251835"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="235d1-104">Segurança de transporte com autenticação básica</span><span class="sxs-lookup"><span data-stu-id="235d1-104">Transport Security with Basic Authentication</span></span>

<span data-ttu-id="235d1-105">A ilustração a seguir mostra um serviço e cliente do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="235d1-105">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="235d1-106">O servidor precisa de um certificado X. 509 válido que possa ser usado para protocolo SSL (SSL) e os clientes devem confiar no certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="235d1-106">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="235d1-107">Além disso, o serviço Web já tem uma implementação SSL que pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="235d1-107">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="235d1-108">Para obter mais informações sobre como habilitar a autenticação básica no Serviços de Informações da Internet (IIS), consulte <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> .</span><span class="sxs-lookup"><span data-stu-id="235d1-108">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Captura de tela que mostra a segurança de transporte com autenticação básica.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="235d1-110">Característica</span><span class="sxs-lookup"><span data-stu-id="235d1-110">Characteristic</span></span>|<span data-ttu-id="235d1-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="235d1-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="235d1-112">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="235d1-112">Security Mode</span></span>|<span data-ttu-id="235d1-113">Transport</span><span class="sxs-lookup"><span data-stu-id="235d1-113">Transport</span></span>|  
|<span data-ttu-id="235d1-114">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="235d1-114">Interoperability</span></span>|<span data-ttu-id="235d1-115">Com serviços e clientes de serviços Web existentes</span><span class="sxs-lookup"><span data-stu-id="235d1-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="235d1-116">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="235d1-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="235d1-117">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="235d1-117">Authentication (Client)</span></span>|<span data-ttu-id="235d1-118">Sim (usando HTTPS)</span><span class="sxs-lookup"><span data-stu-id="235d1-118">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="235d1-119">Sim (por nome de usuário/senha)</span><span class="sxs-lookup"><span data-stu-id="235d1-119">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="235d1-120">Integridade</span><span class="sxs-lookup"><span data-stu-id="235d1-120">Integrity</span></span>|<span data-ttu-id="235d1-121">Sim</span><span class="sxs-lookup"><span data-stu-id="235d1-121">Yes</span></span>|  
|<span data-ttu-id="235d1-122">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="235d1-122">Confidentiality</span></span>|<span data-ttu-id="235d1-123">Yes</span><span class="sxs-lookup"><span data-stu-id="235d1-123">Yes</span></span>|  
|<span data-ttu-id="235d1-124">Transport</span><span class="sxs-lookup"><span data-stu-id="235d1-124">Transport</span></span>|<span data-ttu-id="235d1-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="235d1-125">HTTPS</span></span>|  
|<span data-ttu-id="235d1-126">Associação</span><span class="sxs-lookup"><span data-stu-id="235d1-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="235d1-127">Serviço</span><span class="sxs-lookup"><span data-stu-id="235d1-127">Service</span></span>  

 <span data-ttu-id="235d1-128">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="235d1-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="235d1-129">Realize uma destas ações:</span><span class="sxs-lookup"><span data-stu-id="235d1-129">Do one of the following:</span></span>  
  
- <span data-ttu-id="235d1-130">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="235d1-130">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="235d1-131">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="235d1-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="235d1-132">Código</span><span class="sxs-lookup"><span data-stu-id="235d1-132">Code</span></span>  

 <span data-ttu-id="235d1-133">O código a seguir mostra como criar um ponto de extremidade de serviço que usa um nome de usuário de domínio do Windows e uma senha para a segurança da transferência.</span><span class="sxs-lookup"><span data-stu-id="235d1-133">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="235d1-134">Observe que o serviço requer um certificado X. 509 para autenticar no cliente.</span><span class="sxs-lookup"><span data-stu-id="235d1-134">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="235d1-135">Para obter mais informações, consulte [trabalhando com certificados](working-with-certificates.md) e [como configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="235d1-135">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="235d1-136">Configuração</span><span class="sxs-lookup"><span data-stu-id="235d1-136">Configuration</span></span>  

 <span data-ttu-id="235d1-137">O seguinte configura um serviço para usar a autenticação básica com segurança em nível de transporte:</span><span class="sxs-lookup"><span data-stu-id="235d1-137">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="235d1-138">Cliente</span><span class="sxs-lookup"><span data-stu-id="235d1-138">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="235d1-139">Código</span><span class="sxs-lookup"><span data-stu-id="235d1-139">Code</span></span>  

 <span data-ttu-id="235d1-140">O código a seguir mostra o código do cliente que inclui o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="235d1-140">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="235d1-141">Observe que o usuário deve fornecer um nome de usuário e senha do Windows válidos.</span><span class="sxs-lookup"><span data-stu-id="235d1-141">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="235d1-142">O código para retornar o nome de usuário e a senha não é mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="235d1-142">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="235d1-143">Use uma caixa de diálogo ou outra interface para consultar o usuário para obter as informações.</span><span class="sxs-lookup"><span data-stu-id="235d1-143">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="235d1-144">O nome de usuário e a senha só podem ser definidos usando o código.</span><span class="sxs-lookup"><span data-stu-id="235d1-144">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="235d1-145">Configuração</span><span class="sxs-lookup"><span data-stu-id="235d1-145">Configuration</span></span>  

 <span data-ttu-id="235d1-146">O código a seguir mostra a configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="235d1-146">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="235d1-147">Não é possível usar a configuração para definir o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="235d1-147">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="235d1-148">A configuração mostrada aqui deve ser aumentada usando o código para definir o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="235d1-148">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="235d1-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="235d1-149">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="235d1-150">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="235d1-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="235d1-151">Como: configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="235d1-151">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="235d1-152">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="235d1-152">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="235d1-153">[Modelo de segurança para o Windows Server app Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="235d1-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
