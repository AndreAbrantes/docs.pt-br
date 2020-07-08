---
title: Como usar TraceSource e filtros com ouvintes de rastreamento
description: Use a classe de rastreamento e os filtros com ouvintes de rastreamento no .NET. O rastreador substitui os métodos estáticos das classes de rastreamento e depuração mais antigas.
ms.date: 03/30/2017
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
ms.openlocfilehash: 432c866f7c3ca1fd59f8f3d36acd61740b6584c0
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051253"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="6f87c-104">Como usar TraceSource e filtros com ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6f87c-104">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="6f87c-105">Um dos novos recursos do .NET Framework versão 2.0 é um sistema de rastreamento aprimorado.</span><span class="sxs-lookup"><span data-stu-id="6f87c-105">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="6f87c-106">A premissa básica permanece inalterada: mensagens de rastreamento são enviadas por meio de comutadores para ouvintes, que relatam os dados para um meio de saída associado.</span><span class="sxs-lookup"><span data-stu-id="6f87c-106">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="6f87c-107">Uma diferença principal para a versão 2.0 é que os rastreamentos podem ser iniciados por meio de instâncias da classe <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="6f87c-107">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="6f87c-108">A <xref:System.Diagnostics.TraceSource> destina-se a funcionar como um sistema de rastreamento aprimorado e pode ser usada no lugar dos métodos estáticos das classes de rastreamento antigas <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug>.</span><span class="sxs-lookup"><span data-stu-id="6f87c-108"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="6f87c-109">As classes <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> familiares ainda existem, mas a prática recomendada é usar a classe <xref:System.Diagnostics.TraceSource> para o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6f87c-109">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="6f87c-110">Este tópico descreve o uso de um <xref:System.Diagnostics.TraceSource> juntamente com um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f87c-110">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="6f87c-111">É possível, embora não recomendado, rastrear usando um <xref:System.Diagnostics.TraceSource> sem o uso de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6f87c-111">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="6f87c-112">Para obter informações sobre rastreamento sem um arquivo de configuração, consulte [Como criar e inicializar origens de rastreamento](how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="6f87c-112">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="6f87c-113">Criar e inicializar a origem do rastreamento</span><span class="sxs-lookup"><span data-stu-id="6f87c-113">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="6f87c-114">A primeira etapa para instrumentar um aplicativo com o rastreamento é criar uma origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6f87c-114">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="6f87c-115">Em projetos grandes com vários componentes, você pode criar uma origem do rastreamento separada para cada componente.</span><span class="sxs-lookup"><span data-stu-id="6f87c-115">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="6f87c-116">A prática recomendada é usar o nome do aplicativo como o nome da origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6f87c-116">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="6f87c-117">Isso tornará mais fácil manter os rastreamentos diferentes separados.</span><span class="sxs-lookup"><span data-stu-id="6f87c-117">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="6f87c-118">O código a seguir cria uma nova origem do rastreamento (`mySource)`) e chama um método (`Activity1`) que rastreia eventos.</span><span class="sxs-lookup"><span data-stu-id="6f87c-118">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="6f87c-119">As mensagens de rastreamento são gravadas pelo ouvinte de rastreamento padrão.</span><span class="sxs-lookup"><span data-stu-id="6f87c-119">The trace messages are written by the default trace listener.</span></span>  
  
    ```csharp
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="6f87c-120">Criar e inicializar ouvintes de rastreamento e filtros</span><span class="sxs-lookup"><span data-stu-id="6f87c-120">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="6f87c-121">O código no primeiro procedimento não identifica programaticamente nenhum ouvinte de rastreamento ou filtro.</span><span class="sxs-lookup"><span data-stu-id="6f87c-121">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="6f87c-122">O resultado do código, por si só, é que as mensagens de rastreamento são gravadas para o ouvinte de rastreamento padrão.</span><span class="sxs-lookup"><span data-stu-id="6f87c-122">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="6f87c-123">Para configurar os ouvintes de rastreamento específicos e os respectivos filtros associados, edite o arquivo de configuração que corresponde ao nome do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f87c-123">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="6f87c-124">Nesse arquivo, você pode adicionar ou remover um ouvinte, definir as propriedades e o filtro para um ouvinte ou remover ouvintes.</span><span class="sxs-lookup"><span data-stu-id="6f87c-124">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="6f87c-125">O exemplo de arquivo de configuração a seguir mostra como inicializar um ouvinte de rastreamento do console e um ouvinte de rastreamento do text writer na origem de rastreamento criada no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="6f87c-125">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="6f87c-126">Além de configurar os ouvintes de rastreamento, o arquivo de configuração cria filtros para ambos os ouvintes e cria uma opção de origem para a origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6f87c-126">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="6f87c-127">Duas técnicas são mostradas para a adição de ouvintes de rastreamento: adicionar o ouvinte diretamente à origem de rastreamento e adicionar um ouvinte à coleção de ouvintes compartilhados e, em seguida, adicioná-lo pelo nome à origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6f87c-127">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="6f87c-128">Os filtros identificados para os dois ouvintes são inicializados com níveis de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="6f87c-128">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="6f87c-129">Isso resulta na gravação de algumas mensagens por apenas um dos dois ouvintes.</span><span class="sxs-lookup"><span data-stu-id="6f87c-129">This results in some messages being written by only one of the two listeners.</span></span>  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"
            switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"
            type="System.Diagnostics.TextWriterTraceListener"
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="6f87c-130">Para alterar o nível no qual um ouvinte grava uma mensagem de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6f87c-130">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="6f87c-131">O arquivo de configuração inicializa as configurações para a origem de rastreamento no momento em que o aplicativo é inicializado.</span><span class="sxs-lookup"><span data-stu-id="6f87c-131">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="6f87c-132">Para alterar essas configurações, você deve alterar o arquivo de configuração e reiniciar o aplicativo ou atualizar o aplicativo de forma programática usando o método <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f87c-132">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6f87c-133">O aplicativo pode alterar dinamicamente as propriedades definidas pelo arquivo de configuração para substituir as configurações especificadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6f87c-133">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="6f87c-134">Por exemplo, talvez você deseje assegurar que as mensagens críticas sejam sempre enviadas para um arquivo de texto, independentemente das definições de configuração atuais.</span><span class="sxs-lookup"><span data-stu-id="6f87c-134">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
    ```csharp
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners
                // for all event types. This statement will override
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6f87c-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f87c-135">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="6f87c-136">Como criar e inicializar fontes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6f87c-136">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="6f87c-137">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6f87c-137">Trace Listeners</span></span>](trace-listeners.md)
