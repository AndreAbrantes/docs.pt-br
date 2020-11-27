---
title: 'Como: criar um token de contexto de segurança para uma sessão segura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 87156eb4c8d28180b492c7ff445b3334515f4a7f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286494"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="50c52-102">Como: criar um token de contexto de segurança para uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="50c52-102">How to: Create a Security Context Token for a Secure Session</span></span>

<span data-ttu-id="50c52-103">Usando um símbolo de contexto de segurança com estado (SCT) em uma sessão segura, a sessão pode resistir ao serviço que está sendo reciclado.</span><span class="sxs-lookup"><span data-stu-id="50c52-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="50c52-104">Por exemplo, quando um SCT sem estado é usado em uma sessão segura e Serviços de Informações da Internet (IIS) é redefinido, os dados de sessão associados ao serviço são perdidos.</span><span class="sxs-lookup"><span data-stu-id="50c52-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="50c52-105">Esses dados de sessão incluem um cache de token SCT.</span><span class="sxs-lookup"><span data-stu-id="50c52-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="50c52-106">Assim, na próxima vez que um cliente envia o serviço a um SCT sem estado, um erro é retornado, pois a chave associada ao SCT não pode ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="50c52-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="50c52-107">Se, no entanto, um SCT com estado for usado, a chave que está associada ao SCT está contida no SCT.</span><span class="sxs-lookup"><span data-stu-id="50c52-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="50c52-108">Como a chave está contida no SCT e, portanto, contida na mensagem, a sessão segura não é afetada pelo serviço que está sendo reciclado.</span><span class="sxs-lookup"><span data-stu-id="50c52-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="50c52-109">Por padrão, Windows Communication Foundation (WCF) usa SCTs sem estado em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="50c52-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="50c52-110">Este tópico fornece detalhes sobre como usar SCTs com estado em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="50c52-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50c52-111">O estado SCTs não pode ser usado em uma sessão segura que envolve um contrato derivado de <xref:System.ServiceModel.Channels.IDuplexChannel> .</span><span class="sxs-lookup"><span data-stu-id="50c52-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50c52-112">Para aplicativos que usam SCTs com estado em uma sessão segura, a identidade do thread para o serviço deve ser uma conta de usuário que tenha um perfil de usuário associado.</span><span class="sxs-lookup"><span data-stu-id="50c52-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="50c52-113">Quando o serviço é executado em uma conta que não tem um perfil de usuário, como `Local Service` , uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="50c52-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50c52-114">Quando a representação é necessária no Windows XP, use uma sessão segura sem um SCT com estado.</span><span class="sxs-lookup"><span data-stu-id="50c52-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="50c52-115">Quando SCTs com estado são usados com representação, um <xref:System.InvalidOperationException> é gerado.</span><span class="sxs-lookup"><span data-stu-id="50c52-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="50c52-116">Para obter mais informações, consulte [cenários sem suporte](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="50c52-116">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="50c52-117">Para usar SCTs com estado em uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="50c52-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="50c52-118">Crie uma associação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura que usa um SCT com estado.</span><span class="sxs-lookup"><span data-stu-id="50c52-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="50c52-119">Defina uma associação personalizada adicionando uma [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ao arquivo de configuração para o serviço.</span><span class="sxs-lookup"><span data-stu-id="50c52-119">Define a custom binding, by adding a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. <span data-ttu-id="50c52-120">Adicione um [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elemento filho ao [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="50c52-120">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) child element to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="50c52-121">Especifique um nome de associação definindo o `name` atributo como um nome exclusivo dentro do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="50c52-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. <span data-ttu-id="50c52-122">Especifique o modo de autenticação para as mensagens enviadas para e desse serviço adicionando um [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento filho ao [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="50c52-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="50c52-123">Especifique que uma sessão segura é usada definindo o `authenticationMode` atributo como `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="50c52-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="50c52-124">Especifique que SCTs com estado são usados definindo o `requireSecurityContextCancellation` atributo como `false` .</span><span class="sxs-lookup"><span data-stu-id="50c52-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. <span data-ttu-id="50c52-125">Especifique como o cliente é autenticado enquanto a sessão segura é estabelecida adicionando um [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento filho ao [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="50c52-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="50c52-126">Especifique como o cliente é autenticado definindo o `authenticationMode` atributo.</span><span class="sxs-lookup"><span data-stu-id="50c52-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="50c52-127">Especifique a codificação de mensagem adicionando um elemento de codificação, como [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="50c52-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="50c52-128">Especifique o transporte adicionando um elemento de transporte, como o [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="50c52-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="50c52-129">O exemplo de código a seguir usa a configuração para especificar uma associação personalizada que as mensagens podem usar com estado SCTs em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="50c52-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="50c52-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50c52-130">Example</span></span>  

 <span data-ttu-id="50c52-131">O exemplo de código a seguir cria uma associação personalizada que usa o <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> modo de autenticação para inicializar uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="50c52-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="50c52-132">Quando a autenticação do Windows é usada em combinação com um SCT com estado, o WCF não preenche a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade com a identidade do chamador real, mas, em vez disso, define a propriedade como anônima.</span><span class="sxs-lookup"><span data-stu-id="50c52-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="50c52-133">Como a segurança do WCF deve recriar o conteúdo do contexto de segurança do serviço para cada solicitação da SCT de entrada, o servidor não mantém o controle da sessão de segurança na memória.</span><span class="sxs-lookup"><span data-stu-id="50c52-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="50c52-134">Como é impossível serializar a <xref:System.Security.Principal.WindowsIdentity> instância no SCT, a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade retorna uma identidade anônima.</span><span class="sxs-lookup"><span data-stu-id="50c52-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="50c52-135">A configuração a seguir exibe esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="50c52-135">The following configuration exhibits this behavior.</span></span>  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
        </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50c52-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="50c52-136">See also</span></span>

- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
