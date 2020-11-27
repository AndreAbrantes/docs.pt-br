---
title: 'Como: especificar credenciais de segurança de canal'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 9236985ef461044e480847003d9d249b7e232783
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266760"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="ae425-102">Como: especificar credenciais de segurança de canal</span><span class="sxs-lookup"><span data-stu-id="ae425-102">How to: Specify Channel Security Credentials</span></span>

<span data-ttu-id="ae425-103">O moniker do serviço Windows Communication Foundation (WCF) permite que aplicativos COM chamem serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="ae425-103">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="ae425-104">A maioria dos serviços WCF exige que o cliente especifique credenciais para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="ae425-104">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="ae425-105">Ao chamar um serviço WCF de um cliente WCF, você pode especificar essas credenciais em código gerenciado ou em um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae425-105">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="ae425-106">Ao chamar um serviço WCF de um aplicativo COM, você pode usar a <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface para especificar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="ae425-106">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="ae425-107">Este tópico ilustra várias maneiras de especificar credenciais usando a <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span><span class="sxs-lookup"><span data-stu-id="ae425-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae425-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> é uma interface baseada em IDispatch e você não terá a funcionalidade do IntelliSense no ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae425-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="ae425-109">Este artigo usará o serviço WCF definido no [exemplo de segurança de mensagem](../samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ae425-109">This article will use the WCF service defined in the [Message Security Sample](../samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="ae425-110">Para especificar um certificado de cliente</span><span class="sxs-lookup"><span data-stu-id="ae425-110">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="ae425-111">Execute o arquivo de Setup.bat no diretório de segurança da mensagem para criar e instalar os certificados de teste necessários.</span><span class="sxs-lookup"><span data-stu-id="ae425-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="ae425-112">Abra o projeto de segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ae425-112">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="ae425-113">Adicione `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` à `ICalculator` definição de interface.</span><span class="sxs-lookup"><span data-stu-id="ae425-113">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="ae425-114">Adicione `bindingNamespace="http://Microsoft.ServiceModel.Samples"` à marca do ponto de extremidade no App.config para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ae425-114">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="ae425-115">Crie o exemplo de segurança de mensagem e execute Service.exe.</span><span class="sxs-lookup"><span data-stu-id="ae425-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="ae425-116">Use o Internet Explorer e navegue até o URI do serviço ( `http://localhost:8000/ServiceModelSamples/Service` ) para garantir que o serviço esteja funcionando.</span><span class="sxs-lookup"><span data-stu-id="ae425-116">Use Internet Explorer and browse to the service's URI (`http://localhost:8000/ServiceModelSamples/Service`) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="ae425-117">Abra Visual Basic 6,0 e crie um novo arquivo Standard. exe.</span><span class="sxs-lookup"><span data-stu-id="ae425-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="ae425-118">Adicione um botão ao formulário e clique duas vezes no botão para adicionar o seguinte código ao manipulador de cliques:</span><span class="sxs-lookup"><span data-stu-id="ae425-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7. <span data-ttu-id="ae425-119">Execute o aplicativo Visual Basic e verifique os resultados.</span><span class="sxs-lookup"><span data-stu-id="ae425-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="ae425-120">O aplicativo Visual Basic exibirá uma caixa de mensagem com o resultado de chamar Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="ae425-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="ae425-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> ou <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> também pode ser usado no lugar de <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> para definir o certificado do cliente:</span><span class="sxs-lookup"><span data-stu-id="ae425-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```vb  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> <span data-ttu-id="ae425-122">Para que essa chamada funcione, o certificado do cliente precisa ser confiável no computador em que o cliente está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="ae425-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae425-123">Se o moniker estiver malformado ou se o serviço estiver indisponível, a chamada para retornará `GetObject` um erro dizendo "sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="ae425-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="ae425-124">Se você receber esse erro, verifique se o moniker que você está usando está correto e se o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="ae425-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="ae425-125">Para especificar o nome de usuário e a senha</span><span class="sxs-lookup"><span data-stu-id="ae425-125">To specify user name and password</span></span>  
  
1. <span data-ttu-id="ae425-126">Modifique o arquivo de App.config de serviço para usar o `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="ae425-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="ae425-127">Isso é necessário para a validação de nome de usuário e senha:</span><span class="sxs-lookup"><span data-stu-id="ae425-127">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="ae425-128">Defina o `clientCredentialType` como nome de usuário:</span><span class="sxs-lookup"><span data-stu-id="ae425-128">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="ae425-129">Abra Visual Basic 6,0 e crie um novo arquivo Standard. exe.</span><span class="sxs-lookup"><span data-stu-id="ae425-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="ae425-130">Adicione um botão ao formulário e clique duas vezes no botão para adicionar o seguinte código ao manipulador de cliques:</span><span class="sxs-lookup"><span data-stu-id="ae425-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4. <span data-ttu-id="ae425-131">Execute o aplicativo Visual Basic e verifique os resultados.</span><span class="sxs-lookup"><span data-stu-id="ae425-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="ae425-132">O aplicativo Visual Basic exibirá uma caixa de mensagem com o resultado de chamar Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="ae425-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ae425-133">A associação especificada no moniker do serviço neste exemplo foi alterada para WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="ae425-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="ae425-134">Observe também que você deve fornecer um nome de usuário e senha válidos na chamada para <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="ae425-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="ae425-135">Para especificar as credenciais do Windows</span><span class="sxs-lookup"><span data-stu-id="ae425-135">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="ae425-136">Defina `clientCredentialType` como Windows no arquivo de App.config de serviço:</span><span class="sxs-lookup"><span data-stu-id="ae425-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="ae425-137">Abra Visual Basic 6,0 e crie um novo arquivo Standard. exe.</span><span class="sxs-lookup"><span data-stu-id="ae425-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="ae425-138">Adicione um botão ao formulário e clique duas vezes no botão para adicionar o seguinte código ao manipulador de cliques:</span><span class="sxs-lookup"><span data-stu-id="ae425-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="ae425-139">Execute o aplicativo Visual Basic e verifique os resultados.</span><span class="sxs-lookup"><span data-stu-id="ae425-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="ae425-140">O aplicativo Visual Basic exibirá uma caixa de mensagem com o resultado de chamar Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="ae425-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ae425-141">Você deve substituir "Domain", "userID" e "password" por valores válidos.</span><span class="sxs-lookup"><span data-stu-id="ae425-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="ae425-142">Para especificar um token de problema</span><span class="sxs-lookup"><span data-stu-id="ae425-142">To specify an issue token</span></span>  
  
1. <span data-ttu-id="ae425-143">Tokens de emissão são usados somente para aplicativos que usam segurança federada.</span><span class="sxs-lookup"><span data-stu-id="ae425-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="ae425-144">Para obter mais informações sobre segurança federada, consulte [Federação e tokens emitidos](federation-and-issued-tokens.md) e [exemplo de Federação](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ae425-144">For more information about federated security, see [Federation and Issued Tokens](federation-and-issued-tokens.md) and [Federation Sample](../samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="ae425-145">O exemplo de código a seguir Visual Basic ilustra como chamar o <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> método:</span><span class="sxs-lookup"><span data-stu-id="ae425-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```vb
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="ae425-146">Para obter mais informações sobre os parâmetros para esse método, consulte <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="ae425-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae425-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="ae425-147">See also</span></span>

- [<span data-ttu-id="ae425-148">Federação</span><span class="sxs-lookup"><span data-stu-id="ae425-148">Federation</span></span>](federation.md)
- [<span data-ttu-id="ae425-149">Como: configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="ae425-149">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="ae425-150">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="ae425-150">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="ae425-151">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="ae425-151">Message Security</span></span>](message-security-in-wcf.md)
- [<span data-ttu-id="ae425-152">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="ae425-152">Bindings and Security</span></span>](bindings-and-security.md)
