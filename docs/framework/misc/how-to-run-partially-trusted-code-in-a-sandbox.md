---
title: Como executar código parcialmente confiável em uma área restrita
description: Descubra como executar código parcialmente confiável em uma área restrita no .NET. A classe AppDomain é uma maneira eficaz de colocar aplicativos gerenciados em área restrita.
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: baa04a3c55728590b8aa502648a8ab42bf62f903
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288275"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="5899c-104">Como executar código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="5899c-104">How to: Run Partially Trusted Code in a Sandbox</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="5899c-105">A área restrita é a prática de executar código em um ambiente de segurança restrito, que limita as permissões de acesso concedidas ao código.</span><span class="sxs-lookup"><span data-stu-id="5899c-105">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="5899c-106">Por exemplo, se você tiver uma biblioteca gerenciada de uma fonte que não confia completamente, não deverá executá-la como totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="5899c-106">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="5899c-107">Em vez disso, você deve colocar o código em uma área restrita que limita suas permissões para aqueles que você espera que sejam necessários (por exemplo, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão).</span><span class="sxs-lookup"><span data-stu-id="5899c-107">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="5899c-108">Você também pode usar a área restrita para testar o código que será distribuído e que será executado em ambientes parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5899c-108">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="5899c-109">Um <xref:System.AppDomain> é uma maneira eficaz de fornecer uma área restrita para aplicativos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="5899c-109">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="5899c-110">Os domínios de aplicativo que são usados para executar código parcialmente confiável têm permissões que definem os recursos protegidos que estão disponíveis durante a execução dentro dele <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="5899c-110">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="5899c-111">O código que é executado dentro do <xref:System.AppDomain> é associado pelas permissões associadas ao <xref:System.AppDomain> e tem permissão para acessar apenas os recursos especificados.</span><span class="sxs-lookup"><span data-stu-id="5899c-111">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="5899c-112">O <xref:System.AppDomain> também inclui uma <xref:System.Security.Policy.StrongName> matriz que é usada para identificar assemblies que devem ser carregados como totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5899c-112">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="5899c-113">Isso permite que o criador de um <xref:System.AppDomain> inicie um novo domínio em área restrita que permite que assemblies auxiliares específicos sejam totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5899c-113">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="5899c-114">Outra opção para carregar assemblies como totalmente confiável é colocá-los no cache de assembly global; no entanto, isso carregará os assemblies como totalmente confiáveis em todos os domínios de aplicativo criados nesse computador.</span><span class="sxs-lookup"><span data-stu-id="5899c-114">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="5899c-115">A lista de nomes fortes dá suporte a uma por <xref:System.AppDomain> decisão que fornece uma determinação mais restritiva.</span><span class="sxs-lookup"><span data-stu-id="5899c-115">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="5899c-116">Você pode usar a <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> sobrecarga do método para especificar o conjunto de permissões para aplicativos que são executados em uma área restrita.</span><span class="sxs-lookup"><span data-stu-id="5899c-116">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="5899c-117">Essa sobrecarga permite que você especifique o nível exato de segurança de acesso do código desejado.</span><span class="sxs-lookup"><span data-stu-id="5899c-117">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="5899c-118">Os assemblies que são carregados em um usando <xref:System.AppDomain> essa sobrecarga podem ter apenas o Grant Set especificado ou podem ser totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5899c-118">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="5899c-119">O assembly terá confiança total se estiver no cache de assembly global ou listado no `fullTrustAssemblies` parâmetro de matriz (o <xref:System.Security.Policy.StrongName> ).</span><span class="sxs-lookup"><span data-stu-id="5899c-119">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="5899c-120">Somente os assemblies conhecidos como totalmente confiáveis devem ser adicionados à `fullTrustAssemblies` lista.</span><span class="sxs-lookup"><span data-stu-id="5899c-120">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="5899c-121">A sobrecarga tem a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="5899c-121">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="5899c-122">Os parâmetros para a <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> sobrecarga do método especificam o nome do <xref:System.AppDomain> , a evidência para o <xref:System.AppDomain> , o <xref:System.AppDomainSetup> objeto que identifica a base do aplicativo para a área restrita, o conjunto de permissões a ser usado e os nomes fortes para assemblies totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5899c-122">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="5899c-123">Por motivos de segurança, a base do aplicativo especificada no `info` parâmetro não deve ser a base do aplicativo para o aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="5899c-123">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="5899c-124">Para o `grantSet` parâmetro, você pode especificar um conjunto de permissões que você criou explicitamente ou um conjunto de permissões padrão criado pelo <xref:System.Security.SecurityManager.GetStandardSandbox%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5899c-124">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="5899c-125">Ao contrário <xref:System.AppDomain> da maioria das cargas, a evidência para o <xref:System.AppDomain> (que é fornecida pelo `securityInfo` parâmetro) não é usada para determinar o conjunto de concessão para os assemblies parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5899c-125">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="5899c-126">Em vez disso, ele é especificado independentemente pelo `grantSet` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5899c-126">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="5899c-127">No entanto, a evidência pode ser usada para outras finalidades, como determinar o escopo de armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="5899c-127">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="5899c-128">Para executar um aplicativo em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="5899c-128">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="5899c-129">Crie o conjunto de permissões a ser concedido ao aplicativo não confiável.</span><span class="sxs-lookup"><span data-stu-id="5899c-129">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="5899c-130">A permissão mínima que você pode conceder é a <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão.</span><span class="sxs-lookup"><span data-stu-id="5899c-130">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="5899c-131">Você também pode conceder permissões adicionais que você ache que podem ser seguras para código não confiável; por exemplo, <xref:System.Security.Permissions.IsolatedStorageFilePermission> .</span><span class="sxs-lookup"><span data-stu-id="5899c-131">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="5899c-132">O código a seguir cria um novo conjunto de permissões com apenas a <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão.</span><span class="sxs-lookup"><span data-stu-id="5899c-132">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="5899c-133">Como alternativa, você pode usar um conjunto de permissões nomeadas existente, como a Internet.</span><span class="sxs-lookup"><span data-stu-id="5899c-133">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="5899c-134">O <xref:System.Security.SecurityManager.GetStandardSandbox%2A> método retorna um `Internet` conjunto de permissões ou um `LocalIntranet` conjunto de permissões dependendo da zona na evidência.</span><span class="sxs-lookup"><span data-stu-id="5899c-134">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="5899c-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> também constrói permissões de identidade para alguns dos objetos de evidência passados como referências.</span><span class="sxs-lookup"><span data-stu-id="5899c-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="5899c-136">Assine o assembly que contém a classe de hospedagem (denominada `Sandboxer` neste exemplo) que chama o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="5899c-136">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="5899c-137">Adicione o <xref:System.Security.Policy.StrongName> usado para assinar o assembly à <xref:System.Security.Policy.StrongName> matriz do `fullTrustAssemblies` parâmetro da <xref:System.AppDomain.CreateDomain%2A> chamada.</span><span class="sxs-lookup"><span data-stu-id="5899c-137">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="5899c-138">A classe de hospedagem deve ser executada como totalmente confiável para habilitar a execução do código de confiança parcial ou para oferecer serviços ao aplicativo de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="5899c-138">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="5899c-139">É assim que você lê o <xref:System.Security.Policy.StrongName> de um assembly:</span><span class="sxs-lookup"><span data-stu-id="5899c-139">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="5899c-140">.NET Framework assemblies como mscorlib e System.dll não precisam ser adicionados à lista de confiança total porque eles são carregados como totalmente confiáveis do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="5899c-140">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="5899c-141">Inicialize o <xref:System.AppDomainSetup> parâmetro do <xref:System.AppDomain.CreateDomain%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5899c-141">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="5899c-142">Com esse parâmetro, você pode controlar muitas das configurações do novo <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="5899c-142">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="5899c-143">A <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade é uma configuração importante e deve ser diferente da <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade para o <xref:System.AppDomain> do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="5899c-143">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="5899c-144">Se as <xref:System.AppDomainSetup.ApplicationBase%2A> configurações forem as mesmas, o aplicativo de confiança parcial poderá fazer com que o aplicativo de hospedagem seja carregado (como totalmente confiável) uma exceção que ele define, explorando-o.</span><span class="sxs-lookup"><span data-stu-id="5899c-144">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="5899c-145">Essa é outra razão pela qual uma captura (exceção) não é recomendada.</span><span class="sxs-lookup"><span data-stu-id="5899c-145">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="5899c-146">Definir a base de aplicativos do host de forma diferente da base de aplicativos do aplicativo de área restrita reduz o risco de explorações.</span><span class="sxs-lookup"><span data-stu-id="5899c-146">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="5899c-147">Chame a <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> sobrecarga do método para criar o domínio do aplicativo usando os parâmetros que especificamos.</span><span class="sxs-lookup"><span data-stu-id="5899c-147">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="5899c-148">A assinatura para esse método é:</span><span class="sxs-lookup"><span data-stu-id="5899c-148">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="5899c-149">Informações adicionais:</span><span class="sxs-lookup"><span data-stu-id="5899c-149">Additional information:</span></span>  
  
    - <span data-ttu-id="5899c-150">Essa é a única sobrecarga do <xref:System.AppDomain.CreateDomain%2A> método que usa um <xref:System.Security.PermissionSet> como parâmetro e, portanto, a única sobrecarga que permite carregar um aplicativo em uma configuração de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="5899c-150">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="5899c-151">O `evidence` parâmetro não é usado para calcular um conjunto de permissões; ele é usado para identificação por outros recursos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5899c-151">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="5899c-152">A definição da <xref:System.AppDomainSetup.ApplicationBase%2A> Propriedade do `info` parâmetro é obrigatória para essa sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="5899c-152">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="5899c-153">O `fullTrustAssemblies` parâmetro tem a `params` palavra-chave, o que significa que não é necessário criar uma <xref:System.Security.Policy.StrongName> matriz.</span><span class="sxs-lookup"><span data-stu-id="5899c-153">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="5899c-154">Passar 0, 1 ou nomes mais fortes como parâmetros é permitido.</span><span class="sxs-lookup"><span data-stu-id="5899c-154">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="5899c-155">O código para criar o domínio do aplicativo é:</span><span class="sxs-lookup"><span data-stu-id="5899c-155">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="5899c-156">Carregue o código na área restrita <xref:System.AppDomain> que você criou.</span><span class="sxs-lookup"><span data-stu-id="5899c-156">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="5899c-157">Isso pode ser feito de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="5899c-157">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="5899c-158">Chame o <xref:System.AppDomain.ExecuteAssembly%2A> método para o assembly.</span><span class="sxs-lookup"><span data-stu-id="5899c-158">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="5899c-159">Use o <xref:System.Activator.CreateInstanceFrom%2A> método para criar uma instância de uma classe derivada de <xref:System.MarshalByRefObject> no novo <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="5899c-159">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="5899c-160">O segundo método é preferível, pois torna mais fácil passar parâmetros para a nova <xref:System.AppDomain> instância.</span><span class="sxs-lookup"><span data-stu-id="5899c-160">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="5899c-161">O <xref:System.Activator.CreateInstanceFrom%2A> método fornece dois recursos importantes:</span><span class="sxs-lookup"><span data-stu-id="5899c-161">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="5899c-162">Você pode usar uma base de código que aponta para um local que não contém seu assembly.</span><span class="sxs-lookup"><span data-stu-id="5899c-162">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="5899c-163">Você pode fazer a criação em um <xref:System.Security.CodeAccessPermission.Assert%2A> para confiança total ( <xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType> ), que permite criar uma instância de uma classe crítica.</span><span class="sxs-lookup"><span data-stu-id="5899c-163">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="5899c-164">(Isso ocorre sempre que seu assembly não tem marcações de transparência e é carregado como totalmente confiável.) Portanto, você precisa ter cuidado para criar apenas o código em que confia com essa função e é recomendável criar apenas instâncias de classes totalmente confiáveis no novo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5899c-164">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="5899c-165">Para criar uma instância de uma classe em um novo domínio, a classe deve estender a <xref:System.MarshalByRefObject> classe.</span><span class="sxs-lookup"><span data-stu-id="5899c-165">To create an instance of a class in a new domain, the class must extend the <xref:System.MarshalByRefObject> class.</span></span>
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="5899c-166">Desenvolva a nova instância de domínio em uma referência neste domínio.</span><span class="sxs-lookup"><span data-stu-id="5899c-166">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="5899c-167">Essa referência é usada para executar o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="5899c-167">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="5899c-168">Chame o `ExecuteUntrustedCode` método na instância da `Sandboxer` classe que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="5899c-168">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="5899c-169">Essa chamada é executada no domínio de aplicativo em área restrita, que tem permissões restritas.</span><span class="sxs-lookup"><span data-stu-id="5899c-169">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <span data-ttu-id="5899c-170"><xref:System.Reflection> é usado para obter um identificador de um método no assembly parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="5899c-170"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="5899c-171">O identificador pode ser usado para executar código de forma segura com permissões mínimas.</span><span class="sxs-lookup"><span data-stu-id="5899c-171">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="5899c-172">No código anterior, observe o <xref:System.Security.PermissionSet.Assert%2A> para a permissão de confiança total antes de imprimir o <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="5899c-172">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="5899c-173">A declaração de confiança total é usada para obter informações estendidas do <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="5899c-173">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="5899c-174">Sem o <xref:System.Security.PermissionSet.Assert%2A> , o <xref:System.Security.SecurityException.ToString%2A> método do <xref:System.Security.SecurityException> irá descobrir que há código parcialmente confiável na pilha e restringirá as informações retornadas.</span><span class="sxs-lookup"><span data-stu-id="5899c-174">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="5899c-175">Isso pode causar problemas de segurança se o código de confiança parcial pudesse ler essas informações, mas o risco é mitigado não concedendo <xref:System.Security.Permissions.UIPermission> .</span><span class="sxs-lookup"><span data-stu-id="5899c-175">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="5899c-176">A declaração de confiança total deve ser usada com moderação e somente quando você tiver certeza de que não está permitindo que o código de confiança parcial eleve a confiança total.</span><span class="sxs-lookup"><span data-stu-id="5899c-176">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="5899c-177">Como regra, não chame o código que você não confia na mesma função e depois de chamar uma declaração para confiança total.</span><span class="sxs-lookup"><span data-stu-id="5899c-177">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="5899c-178">É recomendável sempre reverter a declaração quando terminar de usá-la.</span><span class="sxs-lookup"><span data-stu-id="5899c-178">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5899c-179">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5899c-179">Example</span></span>  

 <span data-ttu-id="5899c-180">O exemplo a seguir implementa o procedimento na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="5899c-180">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="5899c-181">No exemplo, um projeto chamado `Sandboxer` em uma solução do Visual Studio também contém um projeto chamado `UntrustedCode` , que implementa a classe `UntrustedClass` .</span><span class="sxs-lookup"><span data-stu-id="5899c-181">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="5899c-182">Esse cenário pressupõe que você tenha baixado um assembly de biblioteca que contém um método que deve retornar `true` ou `false` para indicar se o número fornecido é um número Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="5899c-182">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="5899c-183">Em vez disso, o método tenta ler um arquivo do seu computador.</span><span class="sxs-lookup"><span data-stu-id="5899c-183">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="5899c-184">O exemplo a seguir mostra o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="5899c-184">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="5899c-185">O exemplo a seguir mostra o `Sandboxer` código do aplicativo que executa o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="5899c-185">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5899c-186">Veja também</span><span class="sxs-lookup"><span data-stu-id="5899c-186">See also</span></span>

- [<span data-ttu-id="5899c-187">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="5899c-187">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
