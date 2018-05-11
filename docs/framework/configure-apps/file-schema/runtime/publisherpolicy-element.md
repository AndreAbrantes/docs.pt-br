---
title: '&lt;publisherPolicy&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cc3b7220fe34f5dc049a3da71b160a88f82fdb1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="e6f48-102">&lt;publisherPolicy&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="e6f48-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="e6f48-103">Especifica se o tempo de execução aplica a política do editor.</span><span class="sxs-lookup"><span data-stu-id="e6f48-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="e6f48-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e6f48-104">\<configuration></span></span>  
<span data-ttu-id="e6f48-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="e6f48-105">\<runtime></span></span>  
<span data-ttu-id="e6f48-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="e6f48-106">\<assemblyBinding></span></span>  
<span data-ttu-id="e6f48-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="e6f48-107">\<dependentAssembly></span></span>  
<span data-ttu-id="e6f48-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="e6f48-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f48-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6f48-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6f48-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e6f48-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6f48-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e6f48-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6f48-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e6f48-112">Attributes</span></span>  
  
|<span data-ttu-id="e6f48-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e6f48-113">Attribute</span></span>|<span data-ttu-id="e6f48-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6f48-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="e6f48-115">Especifica se deve aplicar a política do publicador.</span><span class="sxs-lookup"><span data-stu-id="e6f48-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="e6f48-116">Aplicar o atributo</span><span class="sxs-lookup"><span data-stu-id="e6f48-116">apply Attribute</span></span>  
  
|<span data-ttu-id="e6f48-117">Valor</span><span class="sxs-lookup"><span data-stu-id="e6f48-117">Value</span></span>|<span data-ttu-id="e6f48-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6f48-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="e6f48-119">Aplica a política do publicador.</span><span class="sxs-lookup"><span data-stu-id="e6f48-119">Applies publisher policy.</span></span> <span data-ttu-id="e6f48-120">Essa é a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="e6f48-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="e6f48-121">Não se aplica a política de editor.</span><span class="sxs-lookup"><span data-stu-id="e6f48-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6f48-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e6f48-122">Child Elements</span></span>  
 <span data-ttu-id="e6f48-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e6f48-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6f48-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e6f48-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e6f48-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="e6f48-125">Element</span></span>|<span data-ttu-id="e6f48-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6f48-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6f48-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6f48-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e6f48-128">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e6f48-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6f48-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6f48-129">Remarks</span></span>  
 <span data-ttu-id="e6f48-130">Quando um fornecedor de componentes lança uma nova versão de um assembly, o fornecedor pode incluir uma política de editor para que aplicativos que usam a versão antiga agora usar a nova versão.</span><span class="sxs-lookup"><span data-stu-id="e6f48-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="e6f48-131">Para especificar se deseja aplicar a política de editor para um determinado assembly, coloque o  **\<publisherPolicy >** elemento o  **\<dependentAssembly >** elemento.</span><span class="sxs-lookup"><span data-stu-id="e6f48-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="e6f48-132">A configuração padrão para o **aplicar** atributo é **Sim**.</span><span class="sxs-lookup"><span data-stu-id="e6f48-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="e6f48-133">Definindo o **aplicar** atributo **sem** substitui qualquer anterior **Sim** configurações para um assembly.</span><span class="sxs-lookup"><span data-stu-id="e6f48-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="e6f48-134">A permissão é necessária para um aplicativo ignorar explicitamente a política de publicador usando o [ \<publisherPolicy aplicar = "no" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6f48-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="e6f48-135">A permissão é concedida, definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador no <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="e6f48-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="e6f48-136">Para obter mais informações, consulte [permissão de segurança de redirecionamento de associação de Assembly](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="e6f48-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6f48-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6f48-137">Example</span></span>  
 <span data-ttu-id="e6f48-138">O exemplo a seguir desativa a política de editor para o assembly `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e6f48-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6f48-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6f48-139">See Also</span></span>  
 [<span data-ttu-id="e6f48-140">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e6f48-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="e6f48-141">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="e6f48-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e6f48-142">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="e6f48-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="e6f48-143">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="e6f48-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
