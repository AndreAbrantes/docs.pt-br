---
title: Controlando o registro em log no .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58a9c0d02f4a24acc0df4d4a36d65e02f8bb7603
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396205"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="fab74-102">Controlando o registro em log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fab74-102">Controlling .NET Framework Logging</span></span>
<span data-ttu-id="fab74-103">Você pode usar o ETW (Rastreamento de Eventos para Windows) para registrar eventos de CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="fab74-103">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="fab74-104">Você pode criar e exibir rastros usando as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="fab74-104">You can create and view traces by using the following tools:</span></span>  
  
-   <span data-ttu-id="fab74-105">As ferramentas de linha de comando [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) e [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919), ambas incluídas no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="fab74-105">The [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) and [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) command-line tools, which are included with the Windows operating system.</span></span>  
  
-   <span data-ttu-id="fab74-106">As ferramentas [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) no [Windows Performance Toolkit](http://msdn.microsoft.com/library/windows/hardware/hh162945.aspx).</span><span class="sxs-lookup"><span data-stu-id="fab74-106">The [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) tools in the [Windows Performance Toolkit](http://msdn.microsoft.com/library/windows/hardware/hh162945.aspx).</span></span> <span data-ttu-id="fab74-107">Para obter mais informações sobre o Xperf, visite o [blog de Desempenho do Windows](http://go.microsoft.com/fwlink/?LinkId=179509).</span><span class="sxs-lookup"><span data-stu-id="fab74-107">For more information about Xperf, see the [Windows Performance blog](http://go.microsoft.com/fwlink/?LinkId=179509).</span></span>  
  
 <span data-ttu-id="fab74-108">Para capturar informações de eventos de CLR, o provedor de CLR deve estar instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="fab74-108">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="fab74-109">Para confirmar que o provedor está instalado, digite `logman query providers` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="fab74-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="fab74-110">Uma lista de provedores é exibida.</span><span class="sxs-lookup"><span data-stu-id="fab74-110">A list of providers is displayed.</span></span> <span data-ttu-id="fab74-111">Essa lista deve conter uma entrada para o provedor CLR, conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="fab74-111">This list should contain an entry for the CLR provider, as follows.</span></span>  
  
```  
Provider                                 GUID  
-------------------------------------------------------------------------------  
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.  
```  
  
 <span data-ttu-id="fab74-112">Se o provedor CLR não estiver listado, você poderá instalá-lo no Windows Vista e em sistemas operacionais posteriores usando a ferramenta de linha de comando [Wevtutil](http://go.microsoft.com/fwlink/?LinkID=150915) do Windows.</span><span class="sxs-lookup"><span data-stu-id="fab74-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](http://go.microsoft.com/fwlink/?LinkID=150915) command-line tool.</span></span> <span data-ttu-id="fab74-113">Abra a janela do Prompt de Comando como administrador.</span><span class="sxs-lookup"><span data-stu-id="fab74-113">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="fab74-114">Altere o diretório do prompt para a pasta [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span><span class="sxs-lookup"><span data-stu-id="fab74-114">Change the prompt directory to the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="fab74-115">Esta pasta contém o arquivo CLR-ETW.man.</span><span class="sxs-lookup"><span data-stu-id="fab74-115">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="fab74-116">No prompt de comando, digite o seguinte comando para instalar o provedor de CLR:</span><span class="sxs-lookup"><span data-stu-id="fab74-116">At the command prompt, type the following command to install the CLR provider:</span></span>  
  
 `wevtutil im CLR-ETW.man`  
  
## <a name="capturing-clr-etw-events"></a><span data-ttu-id="fab74-117">Capturando eventos de CLR com o ETW</span><span class="sxs-lookup"><span data-stu-id="fab74-117">Capturing CLR ETW Events</span></span>  
 <span data-ttu-id="fab74-118">Use as ferramentas de linha de comando [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) e [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) para capturar eventos ETW e as ferramentas [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) e [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) para decodificar eventos de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="fab74-118">You can use the [Logman](http://go.microsoft.com/fwlink/?LinkId=150916) and [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) command-line tools to capture ETW events, and the [Tracerpt](http://go.microsoft.com/fwlink/?LinkId=150919) and [Xperf](http://msdn.microsoft.com/library/windows/hardware/hh162920.aspx) tools to decode the trace events.</span></span>  
  
 <span data-ttu-id="fab74-119">Para ativar o log, um usuário deve especificar três coisas:</span><span class="sxs-lookup"><span data-stu-id="fab74-119">To turn on logging, a user must specify three things:</span></span>  
  
-   <span data-ttu-id="fab74-120">O provedor com o qual a comunicação será feita.</span><span class="sxs-lookup"><span data-stu-id="fab74-120">The provider to communicate to.</span></span>  
  
-   <span data-ttu-id="fab74-121">Um número de 64 bits que representa um conjunto de palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="fab74-121">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="fab74-122">Cada palavra-chave representa um conjunto de eventos que o provedor pode ativar.</span><span class="sxs-lookup"><span data-stu-id="fab74-122">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="fab74-123">O número representa um conjunto combinado de palavras-chave para ativar.</span><span class="sxs-lookup"><span data-stu-id="fab74-123">The number represents a combined set of keywords to turn on.</span></span>  
  
-   <span data-ttu-id="fab74-124">Um número pequeno representando o nível (detalhamento) em que o registro será feito.</span><span class="sxs-lookup"><span data-stu-id="fab74-124">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="fab74-125">O nível 1 é o menos detalhado, enquanto que o nível 5 é o mais detalhado.</span><span class="sxs-lookup"><span data-stu-id="fab74-125">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="fab74-126">O nível 0 é um padrão cujo significado é específico do provedor.</span><span class="sxs-lookup"><span data-stu-id="fab74-126">Level 0 is a default whose meaning is provider-specific.</span></span>  
  
#### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="fab74-127">Para capturar eventos ETW de CLR usando o Logman</span><span class="sxs-lookup"><span data-stu-id="fab74-127">To capture CLR ETW events using Logman</span></span>  
  
1.  <span data-ttu-id="fab74-128">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="fab74-128">At the command prompt, type:</span></span>  
  
     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`  
  
     <span data-ttu-id="fab74-129">em que:</span><span class="sxs-lookup"><span data-stu-id="fab74-129">where:</span></span>  
  
    -   <span data-ttu-id="fab74-130">O parâmetro `-p` identifica o GUID do provedor.</span><span class="sxs-lookup"><span data-stu-id="fab74-130">The `-p` parameter identifies the provider GUID.</span></span>  
  
    -   <span data-ttu-id="fab74-131">`0x1CCBD` especifica as categorias de eventos que serão geradas.</span><span class="sxs-lookup"><span data-stu-id="fab74-131">`0x1CCBD` specifies the categories of events that will be raised.</span></span>  
  
    -   <span data-ttu-id="fab74-132">`0x5` define o nível do log (nesse caso, detalhado (5)).</span><span class="sxs-lookup"><span data-stu-id="fab74-132">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>  
  
    -   <span data-ttu-id="fab74-133">O parâmetro `-ets` instrui o Logman a enviar comandos para a seções de rastreamento de eventos.</span><span class="sxs-lookup"><span data-stu-id="fab74-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>  
  
    -   <span data-ttu-id="fab74-134">O parâmetro `-ct perf` especifica que a função `QueryPerformanceCounter` será usada para registrar o carimbo de data/hora para cada evento.</span><span class="sxs-lookup"><span data-stu-id="fab74-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>  
  
2.  <span data-ttu-id="fab74-135">Para parar de registrar os eventos, digite:</span><span class="sxs-lookup"><span data-stu-id="fab74-135">To stop logging the events, type:</span></span>  
  
     `logman stop clrevents -ets`  
  
     <span data-ttu-id="fab74-136">Este comando cria um arquivo binário de rastreamento chamado clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="fab74-136">This command creates a binary trace file named clrevents.etl.</span></span>  
  
#### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="fab74-137">Para capturar eventos CLR ETW usando o Xperf</span><span class="sxs-lookup"><span data-stu-id="fab74-137">To capture CLR ETW events using Xperf</span></span>  
  
1.  <span data-ttu-id="fab74-138">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="fab74-138">At the command prompt, type:</span></span>  
  
     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`  
  
     <span data-ttu-id="fab74-139">Onde o GUID é o GUID do provedor ETW de CLR, e `0x1CCBD:5` rastreia tudo no nível 5 (detalhado) e nos níveis inferiores.</span><span class="sxs-lookup"><span data-stu-id="fab74-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>  
  
2.  <span data-ttu-id="fab74-140">Para parar o rastreamento, digite:</span><span class="sxs-lookup"><span data-stu-id="fab74-140">To stop tracing, type:</span></span>  
  
     `Xperf -stop clr`  
  
     <span data-ttu-id="fab74-141">Este comando cria um arquivo de rastreamento chamado clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="fab74-141">This command creates a trace file named clrevents.etl.</span></span>  
  
## <a name="viewing-clr-etw-events"></a><span data-ttu-id="fab74-142">Exibindo eventos ETW de CLR</span><span class="sxs-lookup"><span data-stu-id="fab74-142">Viewing CLR ETW Events</span></span>  
 <span data-ttu-id="fab74-143">Use os comandos listados abaixo para exibir os eventos ETW de CLR.</span><span class="sxs-lookup"><span data-stu-id="fab74-143">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="fab74-144">Para obter uma descrição dos eventos, consulte [Eventos CLR ETW](../../../docs/framework/performance/clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="fab74-144">For a description of the events, see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).</span></span>  
  
#### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="fab74-145">Para exibir eventos ETW de CLR usando o Tracerpt</span><span class="sxs-lookup"><span data-stu-id="fab74-145">To view CLR ETW events using Tracerpt</span></span>  
  
-   <span data-ttu-id="fab74-146">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="fab74-146">At the command prompt, type:</span></span>  
  
     `tracerpt clrevents.etl`  
  
     <span data-ttu-id="fab74-147">Este comando cria dois arquivos: dumpfile.xml e summary.txt.</span><span class="sxs-lookup"><span data-stu-id="fab74-147">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="fab74-148">O arquivo dumpfile.xml lista todos os eventos, enquanto que summary.txt fornece um resumo dos eventos.</span><span class="sxs-lookup"><span data-stu-id="fab74-148">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>  
  
#### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="fab74-149">Para exibir eventos ETW de CLR usando Xperf</span><span class="sxs-lookup"><span data-stu-id="fab74-149">To view CLR ETW events using Xperf</span></span>  
  
-   <span data-ttu-id="fab74-150">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="fab74-150">At the command prompt, type:</span></span>  
  
     `xperf clrevents.etl`  
  
     <span data-ttu-id="fab74-151">Este comando abre o visualizador de arquivos Xperf ETL.</span><span class="sxs-lookup"><span data-stu-id="fab74-151">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="fab74-152">Nesse visualizador, os eventos CLR são mostrados na exibição **Eventos Genéricos**.</span><span class="sxs-lookup"><span data-stu-id="fab74-152">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="fab74-153">Para exibir uma grade de dados de eventos categorizados por tipo, selecione uma região de tempo nessa exibição e, em seguida, clique com o botão direito do mouse e selecione **Resumo**.</span><span class="sxs-lookup"><span data-stu-id="fab74-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>  
  
#### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="fab74-154">Para converter o arquivo .etl em um arquivo de valores separados por vírgula.</span><span class="sxs-lookup"><span data-stu-id="fab74-154">To convert the .etl file to a comma-separated value file</span></span>  
  
-   <span data-ttu-id="fab74-155">No prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="fab74-155">At the command prompt, type:</span></span>  
  
     `xperf -i clrevents.etl -f clrevents.csv`  
  
     <span data-ttu-id="fab74-156">Este comando faz com que XPerf despeje os eventos na forma de um arquivo de valores separados por vírgula (CSV) que você pode abrir.</span><span class="sxs-lookup"><span data-stu-id="fab74-156">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="fab74-157">Porque eventos diferentes possuem campos diferentes, esse arquivo CSV contém mais de uma linha de cabeçalho antes dos dados.</span><span class="sxs-lookup"><span data-stu-id="fab74-157">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="fab74-158">O primeiro campo de cada linha é o tipo de evento, que indica qual cabeçalho deve ser usado para determinar o restante dos campos.</span><span class="sxs-lookup"><span data-stu-id="fab74-158">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab74-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fab74-159">See Also</span></span>  
 [<span data-ttu-id="fab74-160">Ferramentas de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="fab74-160">Windows Performance Toolkit</span></span>](http://go.microsoft.com/fwlink/?LinkID=161141)  
 [<span data-ttu-id="fab74-161">Eventos ETW no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="fab74-161">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
