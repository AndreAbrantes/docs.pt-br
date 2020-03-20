---
title: Elemento <bindingRedirect>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154290"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="e7c21-102">\<vinculaçãoRedirecionar> Elemento</span><span class="sxs-lookup"><span data-stu-id="e7c21-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="e7c21-103">Redireciona uma versão do assembly para outra.</span><span class="sxs-lookup"><span data-stu-id="e7c21-103">Redirects one assembly version to another.</span></span>  
  
<span data-ttu-id="e7c21-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7c21-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e7c21-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7c21-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e7c21-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<montagem>vinculante**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="e7c21-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="e7c21-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependente>de montagem**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7c21-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="e7c21-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<vinculaçãoRedirecionar>**</span><span class="sxs-lookup"><span data-stu-id="e7c21-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c21-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7c21-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7c21-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e7c21-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e7c21-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e7c21-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7c21-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e7c21-112">Attributes</span></span>  
  
|<span data-ttu-id="e7c21-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e7c21-113">Attribute</span></span>|<span data-ttu-id="e7c21-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7c21-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="e7c21-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e7c21-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="e7c21-116">Especifica a versão do assembly que foi originalmente solicitada.</span><span class="sxs-lookup"><span data-stu-id="e7c21-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="e7c21-117">O formato de um número de versão de montagem é *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="e7c21-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="e7c21-118">Os valores válidos para cada parte desse número de versão estão entre 0 e 65535.</span><span class="sxs-lookup"><span data-stu-id="e7c21-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="e7c21-119">Você também pode especificar um intervalo de versões no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="e7c21-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="e7c21-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="e7c21-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="e7c21-121">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e7c21-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="e7c21-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="e7c21-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="e7c21-123">Esse valor pode especificar uma versão anterior do `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="e7c21-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7c21-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e7c21-124">Child Elements</span></span>  
  
|<span data-ttu-id="e7c21-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="e7c21-125">Element</span></span>|<span data-ttu-id="e7c21-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7c21-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7c21-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e7c21-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="e7c21-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e7c21-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e7c21-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="e7c21-129">Element</span></span>|<span data-ttu-id="e7c21-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7c21-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="e7c21-131">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="e7c21-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="e7c21-132">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7c21-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="e7c21-133">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="e7c21-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="e7c21-134">Use um elemento dependentAssembly para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="e7c21-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="e7c21-135">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e7c21-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7c21-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7c21-136">Remarks</span></span>  
 <span data-ttu-id="e7c21-137">Ao criar um aplicativo .NET Framework com base em um assembly com nome forte, o aplicativo usará essa versão do assembly em tempo de execução por padrão, mesmo se uma nova versão estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="e7c21-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="e7c21-138">No entanto, você pode configurar o aplicativo para ser executado com base em uma versão mais nova do assembly.</span><span class="sxs-lookup"><span data-stu-id="e7c21-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="e7c21-139">Para obter detalhes sobre como o tempo de execução usa esses arquivos para determinar qual versão de montagem usar, consulte [Como o Runtime localiza conjuntos](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="e7c21-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="e7c21-140">Você pode redirecionar mais de uma versão do assembly ao incluir vários elementos `bindingRedirect` em um elemento `dependentAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e7c21-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="e7c21-141">Você também pode redirecionar de uma versão mais recente para uma versão anterior do assembly.</span><span class="sxs-lookup"><span data-stu-id="e7c21-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="e7c21-142">O redirecionamento de associação de assembly explícito em um arquivo de configuração do aplicativo requer uma permissão de segurança.</span><span class="sxs-lookup"><span data-stu-id="e7c21-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="e7c21-143">Isso se aplica ao redirecionamento de assemblies do .NET Framework e assemblies de terceiros.</span><span class="sxs-lookup"><span data-stu-id="e7c21-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="e7c21-144">A permissão é <xref:System.Security.Permissions.SecurityPermissionFlag> concedida definindo a bandeira no <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="e7c21-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="e7c21-145">Para obter mais informações, consulte [A permissão de segurança de redirecionamento de vinculação do conjunto](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="e7c21-145">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7c21-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7c21-146">Example</span></span>  
 <span data-ttu-id="e7c21-147">O exemplo a seguir mostra como redirecionar uma versão do assembly para outra.</span><span class="sxs-lookup"><span data-stu-id="e7c21-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7c21-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="e7c21-148">See also</span></span>

- [<span data-ttu-id="e7c21-149">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="e7c21-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7c21-150">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="e7c21-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e7c21-151">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="e7c21-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
