---
title: Segurança de mensagem com um nome de usuário cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 9447487012cae370d35880e5b780465f9434051b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602616"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="f5d07-102">Segurança de mensagem com um nome de usuário cliente</span><span class="sxs-lookup"><span data-stu-id="f5d07-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="f5d07-103">A ilustração a seguir mostra um serviço de Windows Communication Foundation (WCF) e o cliente protegidos usando a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f5d07-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="f5d07-104">O serviço é autenticado com um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="f5d07-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="f5d07-105">O cliente é autenticado usando um nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="f5d07-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="f5d07-106">Para um aplicativo de exemplo, consulte [segurança da mensagem nome de usuário](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="f5d07-106">For a sample application, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="f5d07-107">![Segurança de mensagem usando autenticação de nome de usuário](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="f5d07-107">![Message security using username authentication](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="f5d07-108">Característica</span><span class="sxs-lookup"><span data-stu-id="f5d07-108">Characteristic</span></span>|<span data-ttu-id="f5d07-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5d07-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f5d07-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="f5d07-110">Security Mode</span></span>|<span data-ttu-id="f5d07-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f5d07-111">Message</span></span>|  
|<span data-ttu-id="f5d07-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="f5d07-112">Interoperability</span></span>|<span data-ttu-id="f5d07-113">Somente Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="f5d07-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="f5d07-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="f5d07-114">Authentication (Server)</span></span>|<span data-ttu-id="f5d07-115">A negociação inicial requer autenticação do servidor</span><span class="sxs-lookup"><span data-stu-id="f5d07-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="f5d07-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="f5d07-116">Authentication (Client)</span></span>|<span data-ttu-id="f5d07-117">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="f5d07-117">User name/password</span></span>|  
|<span data-ttu-id="f5d07-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="f5d07-118">Integrity</span></span>|<span data-ttu-id="f5d07-119">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="f5d07-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="f5d07-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="f5d07-120">Confidentiality</span></span>|<span data-ttu-id="f5d07-121">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="f5d07-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="f5d07-122">Transport</span><span class="sxs-lookup"><span data-stu-id="f5d07-122">Transport</span></span>|<span data-ttu-id="f5d07-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="f5d07-123">HTTP</span></span>|  
|<span data-ttu-id="f5d07-124">Associação</span><span class="sxs-lookup"><span data-stu-id="f5d07-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f5d07-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="f5d07-125">Service</span></span>  
 <span data-ttu-id="f5d07-126">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="f5d07-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f5d07-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="f5d07-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="f5d07-128">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="f5d07-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="f5d07-129">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f5d07-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f5d07-130">Código</span><span class="sxs-lookup"><span data-stu-id="f5d07-130">Code</span></span>  
 <span data-ttu-id="f5d07-131">O código a seguir mostra como criar um ponto de extremidade de serviço que usa a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f5d07-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="f5d07-132">Configuração</span><span class="sxs-lookup"><span data-stu-id="f5d07-132">Configuration</span></span>  
 <span data-ttu-id="f5d07-133">A configuração a seguir pode ser usada em vez do código:</span><span class="sxs-lookup"><span data-stu-id="f5d07-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="f5d07-134">Cliente</span><span class="sxs-lookup"><span data-stu-id="f5d07-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="f5d07-135">Código</span><span class="sxs-lookup"><span data-stu-id="f5d07-135">Code</span></span>  
 <span data-ttu-id="f5d07-136">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="f5d07-136">The following code creates the client.</span></span> <span data-ttu-id="f5d07-137">A associação é a segurança do modo de mensagem e o tipo de credencial do cliente é definido como `UserName` .</span><span class="sxs-lookup"><span data-stu-id="f5d07-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="f5d07-138">O nome de usuário e a senha só podem ser especificados usando código (não é configurável).</span><span class="sxs-lookup"><span data-stu-id="f5d07-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="f5d07-139">O código para retornar o nome de usuário e a senha não é mostrado aqui porque ele deve ser feito no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f5d07-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="f5d07-140">Por exemplo, use uma caixa de diálogo Windows Forms para consultar o usuário para os dados.</span><span class="sxs-lookup"><span data-stu-id="f5d07-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="f5d07-141">Configuração</span><span class="sxs-lookup"><span data-stu-id="f5d07-141">Configuration</span></span>  
 <span data-ttu-id="f5d07-142">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="f5d07-142">The following code configures the client.</span></span> <span data-ttu-id="f5d07-143">A associação é a segurança do modo de mensagem e o tipo de credencial do cliente é definido como `UserName` .</span><span class="sxs-lookup"><span data-stu-id="f5d07-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="f5d07-144">O nome de usuário e a senha só podem ser especificados usando código (não é configurável).</span><span class="sxs-lookup"><span data-stu-id="f5d07-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5d07-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5d07-145">See also</span></span>

- [<span data-ttu-id="f5d07-146">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="f5d07-146">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="f5d07-147">Message Security User Name</span><span class="sxs-lookup"><span data-stu-id="f5d07-147">Message Security User Name</span></span>](../samples/message-security-user-name.md)
- [<span data-ttu-id="f5d07-148">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="f5d07-148">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="f5d07-149">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f5d07-149">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
