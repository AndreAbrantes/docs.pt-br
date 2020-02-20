---
title: Elemento <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: 454314bf1002a9648f669cc708c8ac42461fccaf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452260"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="deffb-102">\<elemento de > loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="deffb-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="deffb-103">Especifica se os assemblies carregados de fontes remotas devem receber confiança total no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="deffb-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="deffb-104">Se você foi direcionado para este artigo devido a uma mensagem de erro na lista de erros do projeto do Visual Studio ou um erro de compilação, consulte [como: usar um assembly da Web no Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="deffb-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="deffb-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="deffb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="deffb-106">> &nbsp;de [ **\<de tempo de execução**](runtime-element.md) do &nbsp;</span><span class="sxs-lookup"><span data-stu-id="deffb-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="deffb-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<loadFromRemoteSources >**</span><span class="sxs-lookup"><span data-stu-id="deffb-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deffb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="deffb-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="deffb-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="deffb-109">Attributes and elements</span></span>
 <span data-ttu-id="deffb-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="deffb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="deffb-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="deffb-111">Attributes</span></span>  
  
|<span data-ttu-id="deffb-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="deffb-112">Attribute</span></span>|<span data-ttu-id="deffb-113">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="deffb-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="deffb-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="deffb-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="deffb-115">Especifica se um assembly que é carregado de uma fonte remota deve receber confiança total.</span><span class="sxs-lookup"><span data-stu-id="deffb-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="deffb-116">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="deffb-116">enabled attribute</span></span>  
  
|<span data-ttu-id="deffb-117">Valor</span><span class="sxs-lookup"><span data-stu-id="deffb-117">Value</span></span>|<span data-ttu-id="deffb-118">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="deffb-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="deffb-119">Não conceda confiança total a aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="deffb-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="deffb-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="deffb-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="deffb-121">Conceda confiança total a aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="deffb-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="deffb-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="deffb-122">Child elements</span></span>  
 <span data-ttu-id="deffb-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="deffb-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="deffb-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="deffb-124">Parent elements</span></span>  
  
|<span data-ttu-id="deffb-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="deffb-125">Element</span></span>|<span data-ttu-id="deffb-126">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="deffb-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="deffb-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="deffb-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="deffb-128">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="deffb-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deffb-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="deffb-129">Remarks</span></span>

<span data-ttu-id="deffb-130">No .NET Framework 3,5 e versões anteriores, se você carregar um assembly de um local remoto, o código no assembly será executado em confiança parcial com um conjunto de concessão que depende da zona da qual ele está carregado.</span><span class="sxs-lookup"><span data-stu-id="deffb-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="deffb-131">Por exemplo, se você carregar um assembly de um site, ele será carregado na zona da Internet e terá o conjunto de permissões da Internet.</span><span class="sxs-lookup"><span data-stu-id="deffb-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="deffb-132">Em outras palavras, ele é executado em uma área restrita da Internet.</span><span class="sxs-lookup"><span data-stu-id="deffb-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="deffb-133">A partir do .NET Framework 4, a política de CAS (segurança de acesso ao código) é desabilitada e os assemblies são carregados em confiança total.</span><span class="sxs-lookup"><span data-stu-id="deffb-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="deffb-134">Normalmente, isso concederia confiança total a assemblies carregados com o método <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> que anteriormente estava na área restrita.</span><span class="sxs-lookup"><span data-stu-id="deffb-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="deffb-135">Para evitar isso, a capacidade de executar código em assemblies carregados de uma fonte remota é desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="deffb-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="deffb-136">Por padrão, se você tentar carregar um assembly remoto, um <xref:System.IO.FileLoadException> com uma mensagem de exceção semelhante à seguinte será lançada:</span><span class="sxs-lookup"><span data-stu-id="deffb-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="deffb-137">Para carregar o assembly e executar seu código, você deve:</span><span class="sxs-lookup"><span data-stu-id="deffb-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="deffb-138">Crie explicitamente uma área restrita para o assembly (consulte [como: executar código parcialmente confiável em uma área restrita](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span><span class="sxs-lookup"><span data-stu-id="deffb-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="deffb-139">Execute o código do assembly em confiança total.</span><span class="sxs-lookup"><span data-stu-id="deffb-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="deffb-140">Você faz isso Configurando o elemento `<loadFromRemoteSources>`.</span><span class="sxs-lookup"><span data-stu-id="deffb-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="deffb-141">Ele permite que você especifique que os assemblies que são executados em confiança parcial em versões anteriores do .NET Framework agora são executados com confiança total no .NET Framework 4 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="deffb-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="deffb-142">Se o assembly não deve ser executado com confiança total, não defina este elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="deffb-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="deffb-143">Em vez disso, crie uma <xref:System.AppDomain> em área restrita na qual carregar o assembly.</span><span class="sxs-lookup"><span data-stu-id="deffb-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="deffb-144">O atributo `enabled` para o elemento `<loadFromRemoteSources>` é efetivo somente quando a segurança de acesso ao código (CAS) está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="deffb-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="deffb-145">Por padrão, a política de CAS é desabilitada no .NET Framework 4 e em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="deffb-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="deffb-146">Se você definir `enabled` como `true`, os assemblies remotos terão confiança total.</span><span class="sxs-lookup"><span data-stu-id="deffb-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="deffb-147">Se `enabled` não estiver definido como `true`, um <xref:System.IO.FileLoadException> será lançado sob uma das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="deffb-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="deffb-148">O comportamento de área restrita do domínio atual é diferente do seu comportamento no .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="deffb-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="deffb-149">Isso requer que a política de CAS seja desabilitada e o domínio atual não seja colocado em área restrita.</span><span class="sxs-lookup"><span data-stu-id="deffb-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="deffb-150">O assembly que está sendo carregado não é da zona de `MyComputer`.</span><span class="sxs-lookup"><span data-stu-id="deffb-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="deffb-151">A definição do elemento `<loadFromRemoteSources>` como `true` impede que essa exceção seja gerada.</span><span class="sxs-lookup"><span data-stu-id="deffb-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="deffb-152">Ele permite que você especifique que você não depende do Common Language Runtime para colocar os assemblies carregados em área restrita para segurança e que eles podem ter permissão para serem executados em confiança total.</span><span class="sxs-lookup"><span data-stu-id="deffb-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="deffb-153">Observações</span><span class="sxs-lookup"><span data-stu-id="deffb-153">Notes</span></span>

- <span data-ttu-id="deffb-154">No .NET Framework 4,5 e versões posteriores, os assemblies em compartilhamentos de rede local são executados em confiança total por padrão; Você não precisa habilitar o elemento `<loadFromRemoteSources>`.</span><span class="sxs-lookup"><span data-stu-id="deffb-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="deffb-155">Se um aplicativo tiver sido copiado da Web, ele será sinalizado pelo Windows como sendo um aplicativo Web, mesmo que ele resida no computador local.</span><span class="sxs-lookup"><span data-stu-id="deffb-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="deffb-156">Você pode alterar essa designação alterando suas propriedades de arquivo ou pode usar o elemento `<loadFromRemoteSources>` para conceder confiança total ao assembly.</span><span class="sxs-lookup"><span data-stu-id="deffb-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="deffb-157">Como alternativa, você pode usar o método <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> para carregar um assembly local que o sistema operacional tenha sinalizado como tendo sido carregado da Web.</span><span class="sxs-lookup"><span data-stu-id="deffb-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="deffb-158">Você pode obter um <xref:System.IO.FileLoadException> em um aplicativo que está sendo executado em um aplicativo do Windows Virtual PC.</span><span class="sxs-lookup"><span data-stu-id="deffb-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="deffb-159">Isso pode acontecer quando você tenta carregar um arquivo de pastas vinculadas no computador host.</span><span class="sxs-lookup"><span data-stu-id="deffb-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="deffb-160">Ele também pode ocorrer quando você tenta carregar um arquivo de uma pasta vinculada por [serviços de área de trabalho remota](/windows/win32/termserv/terminal-services-portal) (serviços de terminal).</span><span class="sxs-lookup"><span data-stu-id="deffb-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="deffb-161">Para evitar a exceção, defina `enabled` como `true`.</span><span class="sxs-lookup"><span data-stu-id="deffb-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="deffb-162">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="deffb-162">Configuration file</span></span>

<span data-ttu-id="deffb-163">Esse elemento é normalmente usado no arquivo de configuração do aplicativo, mas pode ser usado em outros arquivos de configuração, dependendo do contexto.</span><span class="sxs-lookup"><span data-stu-id="deffb-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="deffb-164">Para obter mais informações, consulte o artigo [usos mais implícitos da política de CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) no blog de segurança do .net.</span><span class="sxs-lookup"><span data-stu-id="deffb-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="deffb-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="deffb-165">Example</span></span>

<span data-ttu-id="deffb-166">O exemplo a seguir mostra como conceder confiança total a assemblies carregados de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="deffb-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="deffb-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="deffb-167">See also</span></span>

- [<span data-ttu-id="deffb-168">Mais usos implícitos da política de CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="deffb-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="deffb-169">Como executar código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="deffb-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="deffb-170">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="deffb-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="deffb-171">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="deffb-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
