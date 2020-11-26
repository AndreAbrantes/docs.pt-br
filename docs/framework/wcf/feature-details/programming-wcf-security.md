---
title: Programação de segurança do WCF
description: Saiba como criar um aplicativo WCF seguro, incluindo autenticação, confidencialidade e integridade.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 4ffbf6a05abd3ed9ebcea4b2e85f0dc305a4f2db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244763"
---
# <a name="programming-wcf-security"></a><span data-ttu-id="8d39e-103">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="8d39e-103">Programming WCF Security</span></span>

<span data-ttu-id="8d39e-104">Este tópico descreve as tarefas de programação fundamentais usadas para criar um aplicativo de Windows Communication Foundation de segurança (WCF).</span><span class="sxs-lookup"><span data-stu-id="8d39e-104">This topic describes the fundamental programming tasks used to create a secure Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="8d39e-105">Este tópico aborda somente autenticação, confidencialidade e integridade, coletivamente conhecido como *segurança de transferência*.</span><span class="sxs-lookup"><span data-stu-id="8d39e-105">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="8d39e-106">Este tópico não abrange a autorização (o controle de acesso a recursos ou serviços); para obter informações sobre autorização, consulte [Authorization](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="8d39e-106">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d39e-107">Para obter uma introdução valiosa aos conceitos de segurança, especialmente em relação ao WCF, consulte o conjunto de tutoriais de padrões e práticas no MSDN em [cenários, padrões e diretrizes de implementação para o WSE (Web Services Enhancements) 3,0](/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="8d39e-107">For a valuable introduction to security concepts, especially in regard to WCF, see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="8d39e-108">A programação da segurança do WCF baseia-se em três etapas definindo o seguinte: o modo de segurança, um tipo de credencial de cliente e os valores de credencial.</span><span class="sxs-lookup"><span data-stu-id="8d39e-108">Programming WCF security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="8d39e-109">Você pode executar essas etapas por meio de código ou configuração.</span><span class="sxs-lookup"><span data-stu-id="8d39e-109">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="8d39e-110">Configurando o modo de segurança</span><span class="sxs-lookup"><span data-stu-id="8d39e-110">Setting the Security Mode</span></span>  

 <span data-ttu-id="8d39e-111">O seguinte explica as etapas gerais para a programação com o modo de segurança no WCF:</span><span class="sxs-lookup"><span data-stu-id="8d39e-111">The following explains the general steps for programming with the security mode in WCF:</span></span>  
  
1. <span data-ttu-id="8d39e-112">Selecione uma das associações predefinidas apropriadas para os requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8d39e-112">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="8d39e-113">Para obter uma lista das opções de associação, consulte [associações fornecidas pelo sistema](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="8d39e-113">For a list of the binding choices, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="8d39e-114">Por padrão, quase todas as ligações têm segurança habilitada.</span><span class="sxs-lookup"><span data-stu-id="8d39e-114">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="8d39e-115">A única exceção é a <xref:System.ServiceModel.BasicHttpBinding> classe (usando a configuração, o [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ).</span><span class="sxs-lookup"><span data-stu-id="8d39e-115">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="8d39e-116">A associação selecionada determina o transporte.</span><span class="sxs-lookup"><span data-stu-id="8d39e-116">The binding you select determines the transport.</span></span> <span data-ttu-id="8d39e-117">Por exemplo, <xref:System.ServiceModel.WSHttpBinding> usa http como o transporte; <xref:System.ServiceModel.NetTcpBinding> usa TCP.</span><span class="sxs-lookup"><span data-stu-id="8d39e-117">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2. <span data-ttu-id="8d39e-118">Selecione um dos modos de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="8d39e-118">Select one of the security modes for the binding.</span></span> <span data-ttu-id="8d39e-119">Observe que a associação selecionada determina as opções de modo disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8d39e-119">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="8d39e-120">Por exemplo, o <xref:System.ServiceModel.WSDualHttpBinding> não permite a segurança de transporte (não é uma opção).</span><span class="sxs-lookup"><span data-stu-id="8d39e-120">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="8d39e-121">Da mesma forma, nem o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nem o <xref:System.ServiceModel.NetNamedPipeBinding> permite a segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="8d39e-121">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="8d39e-122">Você tem três opções:</span><span class="sxs-lookup"><span data-stu-id="8d39e-122">You have three choices:</span></span>  
  
    1. `Transport`  
  
         <span data-ttu-id="8d39e-123">A segurança de transporte depende do mecanismo que a associação que você selecionou usa.</span><span class="sxs-lookup"><span data-stu-id="8d39e-123">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="8d39e-124">Por exemplo, se você estiver usando `WSHttpBinding` , o mecanismo de segurança será protocolo SSL (SSL) (também o mecanismo para o protocolo HTTPS).</span><span class="sxs-lookup"><span data-stu-id="8d39e-124">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="8d39e-125">Em termos gerais, a principal vantagem da segurança de transporte é que ela fornece uma boa taxa de transferência, não importa qual transporte você está usando.</span><span class="sxs-lookup"><span data-stu-id="8d39e-125">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="8d39e-126">No entanto, ele tem duas limitações: a primeira é que o mecanismo de transporte determina o tipo de credencial usado para autenticar um usuário.</span><span class="sxs-lookup"><span data-stu-id="8d39e-126">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="8d39e-127">Essa é uma desvantagem somente se um serviço precisar interoperar com outros serviços que exigem diferentes tipos de credenciais.</span><span class="sxs-lookup"><span data-stu-id="8d39e-127">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="8d39e-128">A segunda é que, como a segurança não é aplicada no nível de mensagem, a segurança é implementada de uma maneira de salto a ponta em vez de ponta a extremidade.</span><span class="sxs-lookup"><span data-stu-id="8d39e-128">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="8d39e-129">Essa última limitação é um problema somente se o caminho da mensagem entre o cliente e o serviço inclui intermediários.</span><span class="sxs-lookup"><span data-stu-id="8d39e-129">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="8d39e-130">Para obter mais informações sobre qual transporte usar, consulte [escolhendo um transporte](choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="8d39e-130">For more information about which transport to use, see [Choosing a Transport](choosing-a-transport.md).</span></span> <span data-ttu-id="8d39e-131">Para obter mais informações sobre como usar a segurança de transporte, consulte [visão geral de segurança de transporte](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8d39e-131">For more information about using transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>  
  
    2. `Message`  
  
         <span data-ttu-id="8d39e-132">Segurança de mensagem significa que cada mensagem inclui os cabeçalhos e os dados necessários para manter a mensagem segura.</span><span class="sxs-lookup"><span data-stu-id="8d39e-132">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="8d39e-133">Como a composição dos cabeçalhos varia, você pode incluir qualquer número de credenciais.</span><span class="sxs-lookup"><span data-stu-id="8d39e-133">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="8d39e-134">Isso se torna um fator se você estiver Interoperando com outros serviços que exigem um tipo de credencial específico que um mecanismo de transporte não pode fornecer, ou se a mensagem deve ser usada com mais de um serviço, em que cada serviço exige um tipo de credencial diferente.</span><span class="sxs-lookup"><span data-stu-id="8d39e-134">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="8d39e-135">Para obter mais informações, consulte [segurança da mensagem](message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="8d39e-135">For more information, see [Message Security](message-security-in-wcf.md).</span></span>  
  
    3. `TransportWithMessageCredential`  
  
         <span data-ttu-id="8d39e-136">Essa escolha usa a camada de transporte para proteger a transferência de mensagens, enquanto cada mensagem inclui as credenciais avançadas de que outros serviços precisam.</span><span class="sxs-lookup"><span data-stu-id="8d39e-136">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="8d39e-137">Isso combina a vantagem de desempenho da segurança de transporte com as valiosas vantagens das credenciais de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8d39e-137">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="8d39e-138">Isso está disponível com as seguintes associações: <xref:System.ServiceModel.BasicHttpBinding> ,, <xref:System.ServiceModel.WSFederationHttpBinding> <xref:System.ServiceModel.NetPeerTcpBinding> e <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="8d39e-138">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="8d39e-139">Se você decidir usar a segurança de transporte para HTTP (em outras palavras, HTTPS), também deverá configurar o host com um certificado SSL e habilitar o SSL em uma porta.</span><span class="sxs-lookup"><span data-stu-id="8d39e-139">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="8d39e-140">Para obter mais informações, consulte [segurança de transporte http](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="8d39e-140">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
4. <span data-ttu-id="8d39e-141">Se você estiver usando o <xref:System.ServiceModel.WSHttpBinding> e não precisar estabelecer uma sessão segura, defina a <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedade como `false` .</span><span class="sxs-lookup"><span data-stu-id="8d39e-141">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="8d39e-142">Uma sessão segura ocorre quando um cliente e um serviço criam um canal usando uma chave simétrica (tanto o cliente quanto o servidor usam a mesma chave para o comprimento de uma conversa, até que a caixa de diálogo seja fechada).</span><span class="sxs-lookup"><span data-stu-id="8d39e-142">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="8d39e-143">Configurando o tipo de credencial do cliente</span><span class="sxs-lookup"><span data-stu-id="8d39e-143">Setting the Client Credential Type</span></span>  

 <span data-ttu-id="8d39e-144">Selecione um tipo de credencial de cliente conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="8d39e-144">Select a client credential type as appropriate.</span></span> <span data-ttu-id="8d39e-145">Para obter mais informações, consulte [selecionando um tipo de credencial](selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="8d39e-145">For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).</span></span> <span data-ttu-id="8d39e-146">Os seguintes tipos de credencial do cliente estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="8d39e-146">The following client credential types are available:</span></span>  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 <span data-ttu-id="8d39e-147">Dependendo de como você define o modo, você deve definir o tipo de credencial.</span><span class="sxs-lookup"><span data-stu-id="8d39e-147">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="8d39e-148">Por exemplo, se você selecionou o `wsHttpBinding` e definiu o modo como "Message", você também pode definir o `clientCredentialType` atributo do elemento Message para um dos seguintes valores:,,, `None` `Windows` `UserName` `Certificate` e `IssuedToken` , conforme mostrado no exemplo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d39e-148">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="8d39e-149">Ou no código:</span><span class="sxs-lookup"><span data-stu-id="8d39e-149">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="8d39e-150">Definindo valores de credenciais de serviço</span><span class="sxs-lookup"><span data-stu-id="8d39e-150">Setting Service Credential Values</span></span>  

 <span data-ttu-id="8d39e-151">Depois de selecionar um tipo de credencial de cliente, você deve definir as credenciais reais para o serviço e o cliente a serem usados.</span><span class="sxs-lookup"><span data-stu-id="8d39e-151">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="8d39e-152">No serviço, as credenciais são definidas usando a <xref:System.ServiceModel.Description.ServiceCredentials> classe e retornadas pela <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade da <xref:System.ServiceModel.ServiceHostBase> classe.</span><span class="sxs-lookup"><span data-stu-id="8d39e-152">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="8d39e-153">A associação em uso implica o tipo de credencial de serviço, o modo de segurança escolhido e o tipo de credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="8d39e-153">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="8d39e-154">O código a seguir define um certificado para uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="8d39e-154">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="8d39e-155">Definindo valores de credenciais de cliente</span><span class="sxs-lookup"><span data-stu-id="8d39e-155">Setting Client Credential Values</span></span>  

 <span data-ttu-id="8d39e-156">No cliente, defina os valores de credencial do cliente usando a <xref:System.ServiceModel.Description.ClientCredentials> classe e retornados pela <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade da <xref:System.ServiceModel.ClientBase%601> classe.</span><span class="sxs-lookup"><span data-stu-id="8d39e-156">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="8d39e-157">O código a seguir define um certificado como uma credencial em um cliente usando o protocolo TCP.</span><span class="sxs-lookup"><span data-stu-id="8d39e-157">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8d39e-158">Veja também</span><span class="sxs-lookup"><span data-stu-id="8d39e-158">See also</span></span>

- [<span data-ttu-id="8d39e-159">Programação de WCF básica</span><span class="sxs-lookup"><span data-stu-id="8d39e-159">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="8d39e-160">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="8d39e-160">Common Security Scenarios</span></span>](common-security-scenarios.md)
