---
title: Serviço e cliente de internet desprotegido
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 017744d692d6fd4183fde3c21e71fcee2f35844e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535352"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="a029e-102">Serviço e cliente de internet desprotegido</span><span class="sxs-lookup"><span data-stu-id="a029e-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="a029e-103">A ilustração a seguir mostra um exemplo de um cliente e serviço de Windows Communication Foundation (WCF) não seguros e público:</span><span class="sxs-lookup"><span data-stu-id="a029e-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Captura de tela que mostra um cenário de Internet não seguro](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="a029e-105">Característica</span><span class="sxs-lookup"><span data-stu-id="a029e-105">Characteristic</span></span>|<span data-ttu-id="a029e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a029e-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a029e-107">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="a029e-107">Security Mode</span></span>|<span data-ttu-id="a029e-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a029e-108">None</span></span>|  
|<span data-ttu-id="a029e-109">Transport</span><span class="sxs-lookup"><span data-stu-id="a029e-109">Transport</span></span>|<span data-ttu-id="a029e-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="a029e-110">HTTP</span></span>|  
|<span data-ttu-id="a029e-111">Associação</span><span class="sxs-lookup"><span data-stu-id="a029e-111">Binding</span></span>|<span data-ttu-id="a029e-112"><xref:System.ServiceModel.BasicHttpBinding> no código, ou o [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) elemento na configuração.</span><span class="sxs-lookup"><span data-stu-id="a029e-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="a029e-113">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a029e-113">Interoperability</span></span>|<span data-ttu-id="a029e-114">Com serviços e clientes de serviços Web existentes</span><span class="sxs-lookup"><span data-stu-id="a029e-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="a029e-115">Autenticação</span><span class="sxs-lookup"><span data-stu-id="a029e-115">Authentication</span></span>|<span data-ttu-id="a029e-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a029e-116">None</span></span>|  
|<span data-ttu-id="a029e-117">Integridade</span><span class="sxs-lookup"><span data-stu-id="a029e-117">Integrity</span></span>|<span data-ttu-id="a029e-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a029e-118">None</span></span>|  
|<span data-ttu-id="a029e-119">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="a029e-119">Confidentiality</span></span>|<span data-ttu-id="a029e-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a029e-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="a029e-121">Serviço</span><span class="sxs-lookup"><span data-stu-id="a029e-121">Service</span></span>  
 <span data-ttu-id="a029e-122">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="a029e-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a029e-123">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="a029e-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="a029e-124">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="a029e-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="a029e-125">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a029e-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a029e-126">Código</span><span class="sxs-lookup"><span data-stu-id="a029e-126">Code</span></span>  
 <span data-ttu-id="a029e-127">O código a seguir mostra como criar um ponto de extremidade sem segurança.</span><span class="sxs-lookup"><span data-stu-id="a029e-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="a029e-128">Por padrão, o <xref:System.ServiceModel.BasicHttpBinding> tem o modo de segurança definido como <xref:System.ServiceModel.BasicHttpSecurityMode.None> .</span><span class="sxs-lookup"><span data-stu-id="a029e-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="a029e-129">Configuração de Serviço</span><span class="sxs-lookup"><span data-stu-id="a029e-129">Service Configuration</span></span>  
 <span data-ttu-id="a029e-130">O código a seguir configura o mesmo ponto de extremidade usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="a029e-130">The following code sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="a029e-131">Cliente</span><span class="sxs-lookup"><span data-stu-id="a029e-131">Client</span></span>  
 <span data-ttu-id="a029e-132">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="a029e-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a029e-133">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="a029e-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="a029e-134">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="a029e-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="a029e-135">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a029e-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a029e-136">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="a029e-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a029e-137">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a029e-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="a029e-138">Código</span><span class="sxs-lookup"><span data-stu-id="a029e-138">Code</span></span>  
 <span data-ttu-id="a029e-139">O código a seguir mostra um cliente WCF básico que acessa um ponto de extremidade não seguro.</span><span class="sxs-lookup"><span data-stu-id="a029e-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="a029e-140">Configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="a029e-140">Client Configuration</span></span>  
 <span data-ttu-id="a029e-141">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="a029e-141">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a029e-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="a029e-142">See also</span></span>

- [<span data-ttu-id="a029e-143">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="a029e-143">Common Security Scenarios</span></span>](common-security-scenarios.md)
- [<span data-ttu-id="a029e-144">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="a029e-144">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="a029e-145">[Modelo de segurança para o Windows Server app Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a029e-145">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
