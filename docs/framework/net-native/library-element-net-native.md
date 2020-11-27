---
title: <Library> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: aeaa6b1a9c3c4ceebdd0eab3f331a044971398bf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287911"
---
# <a name="library-element-net-native"></a><span data-ttu-id="f443d-102">\<Library> (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="f443d-102">\<Library> Element (.NET Native)</span></span>

<span data-ttu-id="f443d-103">Define o assembly que contém tipos e membros de tipo cujos metadados estão disponíveis para reflexão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f443d-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="f443d-104">Elemento \<Directives></span><span class="sxs-lookup"><span data-stu-id="f443d-104">\<Directives> Element</span></span>  
<span data-ttu-id="f443d-105">Elemento \<Library></span><span class="sxs-lookup"><span data-stu-id="f443d-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f443d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f443d-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f443d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f443d-107">Attributes and Elements</span></span>  

 <span data-ttu-id="f443d-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f443d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f443d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f443d-109">Attributes</span></span>  
  
|<span data-ttu-id="f443d-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="f443d-110">Attribute</span></span>|<span data-ttu-id="f443d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f443d-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="f443d-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f443d-112">Required attribute.</span></span> <span data-ttu-id="f443d-113">Especifica o nome de um assembly.</span><span class="sxs-lookup"><span data-stu-id="f443d-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="f443d-114">Elementos filhos deste elemento `<Library>` define a política de reflexão do runtime para tipos e membros de tipo encontrados neste assembly.</span><span class="sxs-lookup"><span data-stu-id="f443d-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="f443d-115">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="f443d-115">Name attribute</span></span>  
  
|<span data-ttu-id="f443d-116">Valor</span><span class="sxs-lookup"><span data-stu-id="f443d-116">Value</span></span>|<span data-ttu-id="f443d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f443d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f443d-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="f443d-118">*assembly_name*</span></span>|<span data-ttu-id="f443d-119">O nome simples do assembly, sem a extensão de arquivo.</span><span class="sxs-lookup"><span data-stu-id="f443d-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="f443d-120">Este atributo corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f443d-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f443d-121">Por exemplo, o nome de um assembly denominado Extensions.dll é "Extensions".</span><span class="sxs-lookup"><span data-stu-id="f443d-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="f443d-122">Consulte a seção Comentários para ver uma forma especial de *assembly_name* que dá suporte à inclusão condicional de metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="f443d-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f443d-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f443d-123">Child Elements</span></span>  
  
|<span data-ttu-id="f443d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f443d-124">Element</span></span>|<span data-ttu-id="f443d-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f443d-125">Description</span></span>|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="f443d-126">Aplica a política a todos os tipos em um assembly específico.</span><span class="sxs-lookup"><span data-stu-id="f443d-126">Applies policy to all the types in a particular assembly.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="f443d-127">Aplica a política a todos os tipos em um namespace específico.</span><span class="sxs-lookup"><span data-stu-id="f443d-127">Applies policy to all the types in a particular namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="f443d-128">Aplica a política a um tipo específico, como uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f443d-128">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="f443d-129">Aplica a política a um tipo genérico construído.</span><span class="sxs-lookup"><span data-stu-id="f443d-129">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="f443d-130">Por exemplo, um [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elemento poderia ser usado para definir a política para um `List<String>` tipo.</span><span class="sxs-lookup"><span data-stu-id="f443d-130">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f443d-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f443d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="f443d-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="f443d-132">Element</span></span>|<span data-ttu-id="f443d-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="f443d-133">Description</span></span>|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|<span data-ttu-id="f443d-134">O elemento raiz de um arquivo de diretivas de runtime.</span><span class="sxs-lookup"><span data-stu-id="f443d-134">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f443d-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="f443d-135">Remarks</span></span>  

 <span data-ttu-id="f443d-136">O [\<Directives>](directives-element-net-native.md) elemento pode conter zero, um ou mais `<Library>` elementos.</span><span class="sxs-lookup"><span data-stu-id="f443d-136">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="f443d-137">O elemento `<Library>` serve como um contêiner para definir os elementos do programa cujos metadados são necessária no tempo de execução. Este elemento não expressa política.</span><span class="sxs-lookup"><span data-stu-id="f443d-137">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="f443d-138">No tempo de compilação, as ferramentas do compilador pesquisam somente a biblioteca designada pelo elemento `<Library>` para os elementos do programa identificados por seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="f443d-138">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="f443d-139">Por outro lado, as ferramentas de compilador pesquisam todas as bibliotecas, including.NET Framework Core Libraries, para elementos de programa identificados por elementos filho do [\<Application>](application-element-net-native.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="f443d-139">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="f443d-140">As diretivas `<Library>` podem ser utilizadas condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="f443d-140">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="f443d-141">Se o nome do `<Library>` elemento iniciar e terminar com um asterisco ( \* ), a `<Library>` diretiva terá um efeito somente se o assembly especificado entre os asteriscos for referenciado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f443d-141">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="f443d-142">Por exemplo, a seguinte diretiva de tempo de execução se aplicará somente se o assembly Utilities.dll for referenciado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f443d-142">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f443d-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="f443d-143">See also</span></span>

- [<span data-ttu-id="f443d-144">\<Application> Elementos</span><span class="sxs-lookup"><span data-stu-id="f443d-144">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="f443d-145">\<Directives> Elementos</span><span class="sxs-lookup"><span data-stu-id="f443d-145">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="f443d-146">Referência do arquivo de configuração de diretivas do runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="f443d-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="f443d-147">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="f443d-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
