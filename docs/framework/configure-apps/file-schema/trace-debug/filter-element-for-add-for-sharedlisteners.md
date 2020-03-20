---
title: <filter>Elemento <add> para para<sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153447"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="5043e-102">\<filtrar> \<Elemento \<para adicionar> para> de ouvintes compartilhados</span><span class="sxs-lookup"><span data-stu-id="5043e-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="5043e-103">Adiciona um filtro a um ouvinte na coleção `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="5043e-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="5043e-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5043e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5043e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="5043e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="5043e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de ouvintes compartilhados**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="5043e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="5043e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<adicionar>**](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="5043e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="5043e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de filtro**</span><span class="sxs-lookup"><span data-stu-id="5043e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5043e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5043e-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5043e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5043e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5043e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5043e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5043e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5043e-112">Attributes</span></span>  
  
|<span data-ttu-id="5043e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5043e-113">Attribute</span></span>|<span data-ttu-id="5043e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5043e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5043e-115">**type**</span><span class="sxs-lookup"><span data-stu-id="5043e-115">**type**</span></span>|<span data-ttu-id="5043e-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="5043e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="5043e-117">Especifica o tipo do filtro.</span><span class="sxs-lookup"><span data-stu-id="5043e-117">Specifies the type of the filter.</span></span> <span data-ttu-id="5043e-118">Você pode usar apenas o nome completo do <xref:System.Type.FullName%2A?displayProperty=nameWithType> tipo (no formato da propriedade), ou você pode usar o <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> nome do tipo totalmente qualificado, incluindo as informações de montagem (no formato da propriedade).</span><span class="sxs-lookup"><span data-stu-id="5043e-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="5043e-119">Para obter informações sobre a criação de um nome de tipo totalmente qualificado, consulte [Especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="5043e-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="5043e-120">**Initializedata**</span><span class="sxs-lookup"><span data-stu-id="5043e-120">**initializeData**</span></span>|<span data-ttu-id="5043e-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="5043e-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5043e-122">A seqüência passou para o construtor para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="5043e-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5043e-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5043e-123">Child Elements</span></span>  
 <span data-ttu-id="5043e-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5043e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5043e-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5043e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5043e-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="5043e-126">Element</span></span>|<span data-ttu-id="5043e-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="5043e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5043e-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5043e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5043e-129">Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.</span><span class="sxs-lookup"><span data-stu-id="5043e-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="5043e-130">Uma coleção de ouvintes que qualquer fonte ou elemento de rastreamento pode referenciar.</span><span class="sxs-lookup"><span data-stu-id="5043e-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="5043e-131">Adiciona um ouvinte à coleção **compartilhadaListeners.**</span><span class="sxs-lookup"><span data-stu-id="5043e-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5043e-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="5043e-132">Remarks</span></span>  
 <span data-ttu-id="5043e-133">Se um ouvinte é `<add>` definido em `<sharedListeners>` um elemento do elemento, o filtro `<filter>` para esse ouvinte `<add>` deve ser definido em um elemento que é filho do elemento.</span><span class="sxs-lookup"><span data-stu-id="5043e-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="5043e-134">Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5043e-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5043e-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5043e-135">Example</span></span>  
 <span data-ttu-id="5043e-136">O exemplo a seguir `<filter>` mostra como usar o elemento `console` para `sharedListeners` adicionar um filtro ao ouvinte de rastreamento na coleção.</span><span class="sxs-lookup"><span data-stu-id="5043e-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5043e-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="5043e-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="5043e-138">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="5043e-138">Trace and Debug Settings Schema</span></span>](index.md)
