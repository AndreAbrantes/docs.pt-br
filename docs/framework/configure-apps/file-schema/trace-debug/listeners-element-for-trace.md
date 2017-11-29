---
title: '&lt;ouvintes de&gt; elemento para &lt;rastreamento&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 97d6673fddb20e99454bf97c87254049b82f0000
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistenersgt-element-for-lttracegt"></a><span data-ttu-id="bd9f7-102">&lt;ouvintes de&gt; elemento para &lt;rastreamento&gt;</span><span class="sxs-lookup"><span data-stu-id="bd9f7-102">&lt;listeners&gt; Element for &lt;trace&gt;</span></span>
<span data-ttu-id="bd9f7-103">Especifica um ouvinte que coleta, armazena e roteamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="bd9f7-104">Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="bd9f7-105">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="bd9f7-105">\<configuration> Element</span></span>  
<span data-ttu-id="bd9f7-106">\<System. Diagnostics > elemento</span><span class="sxs-lookup"><span data-stu-id="bd9f7-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="bd9f7-107">\<rastreamento > elemento</span><span class="sxs-lookup"><span data-stu-id="bd9f7-107">\<trace> Element</span></span>  
<span data-ttu-id="bd9f7-108">\<ouvintes > elemento \<rastreamento ></span><span class="sxs-lookup"><span data-stu-id="bd9f7-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd9f7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd9f7-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd9f7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bd9f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd9f7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd9f7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="bd9f7-112">Attributes</span></span>  
 <span data-ttu-id="bd9f7-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bd9f7-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bd9f7-114">Child Elements</span></span>  
  
|<span data-ttu-id="bd9f7-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd9f7-115">Element</span></span>|<span data-ttu-id="bd9f7-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd9f7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd9f7-117">\<add></span><span class="sxs-lookup"><span data-stu-id="bd9f7-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="bd9f7-118">Adiciona um ouvinte na coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="bd9f7-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="bd9f7-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="bd9f7-120">Limpa a coleção `Listeners` do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="bd9f7-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="bd9f7-121">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="bd9f7-122">Remove um ouvinte do `Listeners` coleção.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd9f7-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bd9f7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bd9f7-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd9f7-124">Element</span></span>|<span data-ttu-id="bd9f7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd9f7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bd9f7-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bd9f7-127">Especifica o elemento raiz para a seção de configuração do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="bd9f7-128">Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd9f7-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd9f7-129">Remarks</span></span>  
 <span data-ttu-id="bd9f7-130">O <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> classes compartilham o mesmo **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="bd9f7-131">Se você adicionar um objeto de ouvinte para a coleção em uma dessas classes, de outra classe usa o mesmo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="bd9f7-132">As classes de ouvinte fornecidas com o .NET Framework derivam de <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bd9f7-133">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="bd9f7-133">Configuration File</span></span>  
 <span data-ttu-id="bd9f7-134">Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd9f7-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd9f7-135">Example</span></span>  
 <span data-ttu-id="bd9f7-136">O exemplo a seguir mostra como usar o  **\<ouvintes >** elemento para adicionar os ouvintes `MyListener` e `MyEventListener` para o **ouvintes** coleção.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="bd9f7-137">`MyListener`cria um arquivo chamado `MyListener.log` e grava a saída para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="bd9f7-138">`MyEventListener`cria uma entrada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="bd9f7-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd9f7-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd9f7-139">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="bd9f7-140">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="bd9f7-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
