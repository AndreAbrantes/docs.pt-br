---
title: Serviço de fachada confiável
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: e9459b4cc26ef85adcc59c308d92491fd2d3acba
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544174"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="7331a-102">Serviço de fachada confiável</span><span class="sxs-lookup"><span data-stu-id="7331a-102">Trusted Facade Service</span></span>
<span data-ttu-id="7331a-103">Este exemplo de cenário demonstra como fluir informações de identidade do chamador de um serviço para outro usando a infraestrutura de segurança do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7331a-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="7331a-104">É um padrão de design comum expor a funcionalidade fornecida por um serviço para a rede pública usando um serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="7331a-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="7331a-105">O serviço de fachada normalmente reside na rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede filtrada) e se comunica com um serviço de back-end que implementa a lógica de negócios e tem acesso a dados internos.</span><span class="sxs-lookup"><span data-stu-id="7331a-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="7331a-106">O canal de comunicação entre o serviço de fachada e o serviço de back-end passa por um firewall e geralmente é limitado apenas para uma única finalidade.</span><span class="sxs-lookup"><span data-stu-id="7331a-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="7331a-107">Este exemplo consiste nos seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="7331a-107">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="7331a-108">Cliente de calculadora</span><span class="sxs-lookup"><span data-stu-id="7331a-108">Calculator client</span></span>  
  
- <span data-ttu-id="7331a-109">Serviço de fachada da calculadora</span><span class="sxs-lookup"><span data-stu-id="7331a-109">Calculator façade service</span></span>  
  
- <span data-ttu-id="7331a-110">Serviço de back-end da calculadora</span><span class="sxs-lookup"><span data-stu-id="7331a-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="7331a-111">O serviço de fachada é responsável por validar a solicitação e autenticar o chamador.</span><span class="sxs-lookup"><span data-stu-id="7331a-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="7331a-112">Após a autenticação e a validação bem-sucedidas, ele encaminha a solicitação para o serviço de back-end usando o canal de comunicação controlado da rede de perímetro para a rede interna.</span><span class="sxs-lookup"><span data-stu-id="7331a-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="7331a-113">Como parte da solicitação encaminhada, o serviço de fachada inclui informações sobre a identidade do chamador para que o serviço de back-end possa usar essas informações em seu processamento.</span><span class="sxs-lookup"><span data-stu-id="7331a-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="7331a-114">A identidade do chamador é transmitida usando um `Username` token de segurança dentro do cabeçalho da mensagem `Security` .</span><span class="sxs-lookup"><span data-stu-id="7331a-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="7331a-115">O exemplo usa a infraestrutura de segurança do WCF para transmitir e extrair essas informações do `Security` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="7331a-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7331a-116">O serviço de back-end confia no serviço de fachada para autenticar o chamador.</span><span class="sxs-lookup"><span data-stu-id="7331a-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="7331a-117">Por isso, o serviço de back-end não autentica o chamador novamente; Ele usa as informações de identidade fornecidas pelo serviço de fachada na solicitação encaminhada.</span><span class="sxs-lookup"><span data-stu-id="7331a-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="7331a-118">Devido a essa relação de confiança, o serviço de back-end deve autenticar o serviço de fachada para garantir que a mensagem encaminhada venha de uma fonte confiável – nesse caso, o serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="7331a-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="7331a-119">Implementação</span><span class="sxs-lookup"><span data-stu-id="7331a-119">Implementation</span></span>  
 <span data-ttu-id="7331a-120">Há dois caminhos de comunicação neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="7331a-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="7331a-121">O primeiro é entre o cliente e o serviço de fachada, o segundo é entre o serviço de fachada e o serviço de back-end.</span><span class="sxs-lookup"><span data-stu-id="7331a-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="7331a-122">Caminho de comunicação entre o cliente e o serviço de fachada</span><span class="sxs-lookup"><span data-stu-id="7331a-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="7331a-123">O cliente para o caminho de comunicação do serviço de fachada usa `wsHttpBinding` com um `UserName` tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="7331a-124">Isso significa que o cliente usa o nome de usuário e a senha para autenticar o serviço de fachada e o serviço de fachada usa o certificado X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="7331a-125">A configuração de associação é semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7331a-125">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="7331a-126">O serviço de fachada autentica o chamador usando a `UserNamePasswordValidator` implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="7331a-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="7331a-127">Para fins de demonstração, a autenticação só garante que o nome de usuário do chamador corresponda à senha apresentada.</span><span class="sxs-lookup"><span data-stu-id="7331a-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="7331a-128">Na situação do mundo real, o usuário provavelmente é autenticado usando Active Directory ou provedor de associação ASP.NET personalizado.</span><span class="sxs-lookup"><span data-stu-id="7331a-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="7331a-129">A implementação do validador reside no `FacadeService.cs` arquivo.</span><span class="sxs-lookup"><span data-stu-id="7331a-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7331a-130">O validador personalizado está configurado para ser usado dentro do `serviceCredentials` comportamento no arquivo de configuração do serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="7331a-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="7331a-131">Esse comportamento também é usado para configurar o certificado X. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="7331a-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="7331a-132">Caminho de comunicação entre o serviço de fachada e de back-end</span><span class="sxs-lookup"><span data-stu-id="7331a-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="7331a-133">O serviço de fachada para o caminho de comunicação do serviço de back-end usa um `customBinding` que consiste em vários elementos de ligação.</span><span class="sxs-lookup"><span data-stu-id="7331a-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="7331a-134">Essa associação realiza duas coisas.</span><span class="sxs-lookup"><span data-stu-id="7331a-134">This binding accomplishes two things.</span></span> <span data-ttu-id="7331a-135">Ele autentica o serviço de fachada e o serviço de back-end para garantir que a comunicação seja segura e proveniente de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="7331a-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="7331a-136">Além disso, ele também transmite a identidade do chamador inicial dentro do `Username` token de segurança.</span><span class="sxs-lookup"><span data-stu-id="7331a-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="7331a-137">Nesse caso, somente o nome de usuário do chamador inicial é transmitido para o serviço de back-end, a senha não é incluída na mensagem.</span><span class="sxs-lookup"><span data-stu-id="7331a-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="7331a-138">Isso ocorre porque o serviço de back-end confia no serviço de fachada para autenticar o chamador antes de encaminhar a solicitação para ele.</span><span class="sxs-lookup"><span data-stu-id="7331a-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="7331a-139">Como o serviço de fachada se autentica no serviço de back-end, o serviço de back-end pode confiar nas informações contidas na solicitação encaminhada.</span><span class="sxs-lookup"><span data-stu-id="7331a-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="7331a-140">A seguir está a configuração de associação para este caminho de comunicação.</span><span class="sxs-lookup"><span data-stu-id="7331a-140">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="7331a-141">O [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemento Binding cuida da transmissão e da extração do nome de usuário do chamador inicial.</span><span class="sxs-lookup"><span data-stu-id="7331a-141">The [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="7331a-142">O [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md) e [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) cuidam da autenticação de serviços de fachada e de back-end e proteção de mensagens.</span><span class="sxs-lookup"><span data-stu-id="7331a-142">The [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="7331a-143">Para encaminhar a solicitação, a implementação do serviço de fachada deve fornecer o nome de usuário do chamador inicial para que a infraestrutura de segurança do WCF possa colocá-la na mensagem encaminhada.</span><span class="sxs-lookup"><span data-stu-id="7331a-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="7331a-144">O nome de usuário do chamador inicial é fornecido na implementação do serviço de fachada, definindo-o na `ClientCredentials` Propriedade na instância de proxy do cliente que o serviço de fachada usa para se comunicar com o serviço de back-end.</span><span class="sxs-lookup"><span data-stu-id="7331a-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="7331a-145">O código a seguir mostra como o `GetCallerIdentity` método é implementado no serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="7331a-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="7331a-146">Outros métodos usam o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="7331a-146">Other methods use the same pattern.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="7331a-147">Conforme mostrado no código anterior, a senha não é definida na `ClientCredentials` propriedade, somente o nome de usuário é definido.</span><span class="sxs-lookup"><span data-stu-id="7331a-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="7331a-148">A infraestrutura de segurança do WCF cria um token de segurança de nome de usuário sem uma senha nesse caso, que é exatamente o que é necessário nesse cenário.</span><span class="sxs-lookup"><span data-stu-id="7331a-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="7331a-149">No serviço de back-end, as informações contidas no token de segurança de nome de usuário devem ser autenticadas.</span><span class="sxs-lookup"><span data-stu-id="7331a-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="7331a-150">Por padrão, a segurança do WCF tenta mapear o usuário para uma conta do Windows usando a senha fornecida.</span><span class="sxs-lookup"><span data-stu-id="7331a-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="7331a-151">Nesse caso, não há nenhuma senha fornecida e o serviço de back-end não é necessário para autenticar o nome de usuário porque a autenticação já foi executada pelo serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="7331a-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="7331a-152">Para implementar essa funcionalidade no WCF, `UserNamePasswordValidator` é fornecido um personalizado que apenas impõe que um nome de usuário seja especificado no token e não execute nenhuma autenticação adicional.</span><span class="sxs-lookup"><span data-stu-id="7331a-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7331a-153">O validador personalizado está configurado para ser usado dentro do `serviceCredentials` comportamento no arquivo de configuração do serviço de fachada.</span><span class="sxs-lookup"><span data-stu-id="7331a-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="7331a-154">Para extrair as informações de nome de usuário e informações sobre a conta de serviço de fachada confiável, a implementação do serviço de back-end usa a `ServiceSecurityContext` classe.</span><span class="sxs-lookup"><span data-stu-id="7331a-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="7331a-155">O código a seguir mostra como o `GetCallerIdentity` método é implementado.</span><span class="sxs-lookup"><span data-stu-id="7331a-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="7331a-156">As informações da conta do serviço de fachada são extraídas usando a `ServiceSecurityContext.Current.WindowsIdentity` propriedade.</span><span class="sxs-lookup"><span data-stu-id="7331a-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="7331a-157">Para acessar as informações sobre o chamador inicial, o serviço de back-end usa a `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` propriedade.</span><span class="sxs-lookup"><span data-stu-id="7331a-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="7331a-158">Ele procura uma `Identity` declaração com um tipo `Name` .</span><span class="sxs-lookup"><span data-stu-id="7331a-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="7331a-159">Essa declaração é gerada automaticamente pela infraestrutura de segurança do WCF por meio das informações contidas no `Username` token de segurança.</span><span class="sxs-lookup"><span data-stu-id="7331a-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="7331a-160">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="7331a-160">Running the sample</span></span>  
 <span data-ttu-id="7331a-161">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7331a-162">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="7331a-163">Você pode pressionar ENTER nas janelas do console do serviço de back-end e de fachada para desligar os serviços.</span><span class="sxs-lookup"><span data-stu-id="7331a-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7331a-164">O arquivo em lote Setup.bat incluído com o exemplo de cenário fachada confiável permite que você configure o servidor com um certificado relevante para executar o serviço de fachada que requer segurança baseada em certificado para se autenticar no cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="7331a-165">Consulte o procedimento de instalação no final deste tópico para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="7331a-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="7331a-166">Veja a seguir uma breve visão geral das diferentes seções dos arquivos em lotes.</span><span class="sxs-lookup"><span data-stu-id="7331a-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="7331a-167">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="7331a-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="7331a-168">As linhas a seguir do arquivo de Setup.bat lote criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="7331a-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="7331a-169">A `%SERVER_NAME%` variável especifica o nome do servidor-o valor padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="7331a-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="7331a-170">O certificado é armazenado no armazenamento LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="7331a-170">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="7331a-171">Instalar o certificado do serviço de fachada no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="7331a-172">A linha a seguir copia o certificado do serviço de fachada para o repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="7331a-173">Essa etapa é necessária porque os certificados gerados por Makecert.exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7331a-174">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="7331a-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7331a-175">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7331a-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7331a-176">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7331a-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7331a-177">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7331a-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="7331a-178">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="7331a-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="7331a-179">Verifique se o caminho inclui a pasta onde Makecert.exe está localizado.</span><span class="sxs-lookup"><span data-stu-id="7331a-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="7331a-180">Execute Setup.bat na pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="7331a-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="7331a-181">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="7331a-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="7331a-182">Iniciar o BackendService.exe do diretório \BackendService\bin em uma janela de console separada</span><span class="sxs-lookup"><span data-stu-id="7331a-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="7331a-183">Iniciar o FacadeService.exe do diretório \FacadeService\bin em uma janela de console separada</span><span class="sxs-lookup"><span data-stu-id="7331a-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="7331a-184">Iniciar Client.exe de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="7331a-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="7331a-185">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="7331a-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="7331a-186">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7331a-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7331a-187">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="7331a-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="7331a-188">Execute Cleanup.bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="7331a-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7331a-189">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7331a-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7331a-190">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7331a-190">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7331a-191">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7331a-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7331a-192">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7331a-192">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`
