---
title: Representando o cliente
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: b5272d8b4dbac60e14fe87accbb08a2073ed65ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594628"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="212e9-102">Representando o cliente</span><span class="sxs-lookup"><span data-stu-id="212e9-102">Impersonating the Client</span></span>
<span data-ttu-id="212e9-103">O exemplo de representação demonstra como representar o aplicativo chamador no serviço para que o serviço possa acessar recursos do sistema em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="212e9-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="212e9-104">Este exemplo é baseado no exemplo de [hospedagem interna](self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="212e9-104">This sample is based on the [Self-Host](self-host.md) sample.</span></span> <span data-ttu-id="212e9-105">Os arquivos de configuração do serviço e do cliente são os mesmos do exemplo de [hospedagem interna](self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="212e9-105">The service and client configuration files are the same as that of the [Self-Host](self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="212e9-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="212e9-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="212e9-107">O código de serviço foi modificado de modo que o `Add` método no serviço represente o chamador usando o <xref:System.ServiceModel.OperationBehaviorAttribute> , conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="212e9-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="212e9-108">Como resultado, o contexto de segurança do thread em execução é alternado para representar o chamador antes de inserir o `Add` método e revertido ao sair do método.</span><span class="sxs-lookup"><span data-stu-id="212e9-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="212e9-109">O `DisplayIdentityInformation` método mostrado no código de exemplo a seguir é uma função de utilitário que exibe a identidade do chamador.</span><span class="sxs-lookup"><span data-stu-id="212e9-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```csharp
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="212e9-110">O `Subtract` método no serviço representa o chamador usando chamadas obrigatórias, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="212e9-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```csharp
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    Console.WriteLine("Before impersonating");  
    DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs
            // on the system resource are enforced in the caller's context.
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
    Console.WriteLine("After reverting");  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="212e9-111">Observe que, nesse caso, o chamador não é representado para a chamada inteira, mas é representado apenas por uma parte da chamada.</span><span class="sxs-lookup"><span data-stu-id="212e9-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="212e9-112">Em geral, é preferível representar para o menor escopo para a operação inteira.</span><span class="sxs-lookup"><span data-stu-id="212e9-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="212e9-113">Os outros métodos não representam o chamador.</span><span class="sxs-lookup"><span data-stu-id="212e9-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="212e9-114">O código do cliente foi modificado para definir o nível de representação como <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> .</span><span class="sxs-lookup"><span data-stu-id="212e9-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="212e9-115">O cliente especifica o nível de representação a ser usado pelo serviço, usando a <xref:System.Security.Principal.TokenImpersonationLevel> enumeração.</span><span class="sxs-lookup"><span data-stu-id="212e9-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="212e9-116">A enumeração oferece suporte aos seguintes valores <xref:System.Security.Principal.TokenImpersonationLevel.None> : <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> , <xref:System.Security.Principal.TokenImpersonationLevel.Identification> , <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> e <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> .</span><span class="sxs-lookup"><span data-stu-id="212e9-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="212e9-117">Para executar uma verificação de acesso ao acessar um recurso do sistema no computador local que é protegido usando ACLs do Windows, o nível de representação deve ser definido <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> como, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="212e9-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="212e9-118">Quando você executa o exemplo, as solicitações e respostas da operação são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="212e9-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="212e9-119">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="212e9-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="212e9-120">O serviço deve ser executado em uma conta administrativa ou a conta em que ele é executado deve receber direitos para registrar o `http://localhost:8000/ServiceModelSamples` URI com a camada http.</span><span class="sxs-lookup"><span data-stu-id="212e9-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="212e9-121">Esses direitos podem ser concedidos Configurando uma [reserva de namespace](/windows/win32/http/namespace-reservations-registrations-and-routing) usando a [ferramenta Httpcfg. exe](/windows/win32/http/httpcfg-exe).</span><span class="sxs-lookup"><span data-stu-id="212e9-121">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="212e9-122">Em computadores que executam o Windows Server 2003, haverá suporte para a representação apenas se o aplicativo host. exe tiver o privilégio de representação.</span><span class="sxs-lookup"><span data-stu-id="212e9-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="212e9-123">(Por padrão, somente os administradores têm essa permissão.) Para adicionar esse privilégio a uma conta em que o serviço está sendo executado, vá para **Ferramentas administrativas**, abra **política de segurança local**, abra **políticas locais**, clique em **atribuição de direitos de usuário**e selecione **representar um cliente após a autenticação** e clique duas vezes em **Propriedades** para adicionar um usuário ou grupo.</span><span class="sxs-lookup"><span data-stu-id="212e9-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="212e9-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="212e9-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="212e9-125">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="212e9-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="212e9-126">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="212e9-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="212e9-127">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="212e9-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="212e9-128">Para demonstrar que o serviço representa o chamador, execute o cliente em uma conta diferente daquela em que o serviço está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="212e9-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="212e9-129">Para fazer isso, no prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="212e9-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="212e9-130">Em seguida, você será solicitado a fornecer uma senha.</span><span class="sxs-lookup"><span data-stu-id="212e9-130">You are then prompted for a password.</span></span> <span data-ttu-id="212e9-131">Insira a senha para a conta que você especificou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="212e9-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="212e9-132">Quando você executa o cliente, observe a identidade antes e depois de executá-la com credenciais diferentes.</span><span class="sxs-lookup"><span data-stu-id="212e9-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
