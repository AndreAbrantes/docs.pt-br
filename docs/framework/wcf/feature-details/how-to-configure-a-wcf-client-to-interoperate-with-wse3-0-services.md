---
title: Como configurar um cliente do WCF para interoperar com serviços WSE3.0
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 7dd50fcc07c6c090042cf87acb4aa5d2b5321a68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579573"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="50a6f-102">Como configurar um cliente do WCF para interoperar com serviços WSE3.0</span><span class="sxs-lookup"><span data-stu-id="50a6f-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="50a6f-103">Os clientes do Windows Communication Foundation (WCF) são compatíveis com o nível de conexão com os serviços do WSE (Web Services Enhancements 3,0 for Microsoft .NET) quando os clientes WCF são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="50a6f-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="50a6f-104">Para configurar um cliente WCF para interoperar com um serviço Web WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="50a6f-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="50a6f-105">Execute a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um cliente WCF para o serviço Web WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="50a6f-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="50a6f-106">Para um serviço Web do WSE, uma classe de cliente WCF é criada.</span><span class="sxs-lookup"><span data-stu-id="50a6f-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="50a6f-107">Para obter detalhes sobre como criar um cliente WCF, consulte o [How to: criar um cliente](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="50a6f-107">For details about creating a WCF client, see the [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="50a6f-108">Crie uma classe que represente uma associação que possa se comunicar com os serviços Web do WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="50a6f-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="50a6f-109">A classe a seguir faz parte do exemplo de [interoperação com o WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) .</span><span class="sxs-lookup"><span data-stu-id="50a6f-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1. <span data-ttu-id="50a6f-110">Crie uma classe que derive da classe <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="50a6f-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="50a6f-111">O exemplo de código a seguir cria uma classe chamada `WseHttpBinding` derivada da <xref:System.ServiceModel.Channels.Binding> classe.</span><span class="sxs-lookup"><span data-stu-id="50a6f-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="50a6f-112">Adicione Propriedades à classe que especifica a declaração ativada do WSE, se as chaves derivadas são necessárias, se as sessões seguras são usadas, se as confirmações de assinatura são necessárias e as configurações de proteção de mensagem.</span><span class="sxs-lookup"><span data-stu-id="50a6f-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="50a6f-113">O exemplo de código a seguir define as `SecurityAssertion` `RequireDerivedKeys` Propriedades,, e `EstablishSecurityContext` `MessageProtectionOrder` .</span><span class="sxs-lookup"><span data-stu-id="50a6f-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="50a6f-114">Eles especificam a declaração do WSE pronto, independentemente de as chaves derivadas serem necessárias, se as sessões seguras são usadas, se as confirmações de assinatura são necessárias e as configurações de proteção de mensagem, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="50a6f-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="50a6f-115">Substitua o <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método para definir as propriedades de associação.</span><span class="sxs-lookup"><span data-stu-id="50a6f-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="50a6f-116">O exemplo de código a seguir especifica as configurações de transporte, codificação de mensagem e proteção de mensagem obtendo os valores das `SecurityAssertion` `MessageProtectionOrder` Propriedades e.</span><span class="sxs-lookup"><span data-stu-id="50a6f-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="50a6f-117">No código do aplicativo cliente, adicione o código para definir as propriedades de associação.</span><span class="sxs-lookup"><span data-stu-id="50a6f-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="50a6f-118">O exemplo de código a seguir especifica que o cliente WCF deve usar a proteção e a autenticação de mensagens conforme definido pela declaração de segurança do WSE 3,0 pronto para uso `AnonymousForCertificate` .</span><span class="sxs-lookup"><span data-stu-id="50a6f-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="50a6f-119">Além disso, as sessões seguras e as chaves derivadas são necessárias.</span><span class="sxs-lookup"><span data-stu-id="50a6f-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="50a6f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50a6f-120">Example</span></span>  
 <span data-ttu-id="50a6f-121">O exemplo de código a seguir define uma associação personalizada que expõe propriedades que correspondem às propriedades de uma declaração de segurança do WSE 3,0 pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="50a6f-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="50a6f-122">A associação personalizada, que é nomeada `WseHttpBinding` , é usada para especificar as propriedades de associação para um cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="50a6f-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="50a6f-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50a6f-123">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="50a6f-124">Interoperação com o WSE</span><span class="sxs-lookup"><span data-stu-id="50a6f-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
