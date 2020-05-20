---
title: Interfaces de hospedagem CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: e6913e18a4ff6e616f357a4ef43fb8b892264943
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616834"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="45ae9-102">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="45ae9-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="45ae9-103">Esta seção descreve as interfaces que os hosts não gerenciados podem usar para integrar o Common Language Runtime (CLR) em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="45ae9-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="45ae9-104">As informações referem-se à .NET Framework versão 2,0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="45ae9-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="45ae9-105">Essas interfaces permitem que o host controle muitos outros aspectos do tempo de execução do que era possível nas versões 1,0 e 1,1 e fornece uma integração muito mais rígida entre o CLR e o modelo de execução do host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="45ae9-106">No .NET Framework versão 1,0 e 1,1, o modelo de hospedagem habilitou um host não gerenciado para carregar o CLR em um processo, para definir determinadas configurações e para receber notificações de eventos.</span><span class="sxs-lookup"><span data-stu-id="45ae9-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="45ae9-107">No entanto, em geral, o host e o CLR eram executados de forma independente nesse processo.</span><span class="sxs-lookup"><span data-stu-id="45ae9-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="45ae9-108">No .NET Framework versão 2,0 e versões posteriores, novas camadas de abstração permitem que o host forneça muitos dos recursos fornecidos atualmente pelos tipos no assembly do Win32 e estenda o conjunto de recursos que o host pode configurar.</span><span class="sxs-lookup"><span data-stu-id="45ae9-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45ae9-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="45ae9-109">In This Section</span></span>  
 [<span data-ttu-id="45ae9-110">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="45ae9-110">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="45ae9-111">Fornece um método que executa um retorno de chamada para um evento registrado.</span><span class="sxs-lookup"><span data-stu-id="45ae9-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="45ae9-112">Interface IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="45ae9-112">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="45ae9-113">Fornece métodos para fazer retornos de chamada em um apartamento.</span><span class="sxs-lookup"><span data-stu-id="45ae9-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="45ae9-114">Interface IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="45ae9-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="45ae9-115">Fornece métodos para definir a configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="45ae9-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="45ae9-116">Interface ICatalogServices</span><span class="sxs-lookup"><span data-stu-id="45ae9-116">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="45ae9-117">Fornece métodos para catalogar serviços.</span><span class="sxs-lookup"><span data-stu-id="45ae9-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="45ae9-118">(Essa interface dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.)</span><span class="sxs-lookup"><span data-stu-id="45ae9-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="45ae9-119">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="45ae9-120">Fornece métodos que dão suporte à comunicação entre o host e o CLR sobre assemblies.</span><span class="sxs-lookup"><span data-stu-id="45ae9-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="45ae9-121">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="45ae9-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="45ae9-122">Gerencia uma lista de assemblies que são carregados pelo CLR e não pelo host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="45ae9-123">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="45ae9-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="45ae9-124">Fornece métodos para o host obter acesso e configurar vários aspectos do, o CLR.</span><span class="sxs-lookup"><span data-stu-id="45ae9-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="45ae9-125">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="45ae9-126">Fornece métodos que permitem que um host associe um conjunto de tarefas a um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="45ae9-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="45ae9-127">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-127">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="45ae9-128">Fornece métodos que permitem ao host configurar despejos de heap personalizados para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="45ae9-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="45ae9-129">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-129">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="45ae9-130">Fornece métodos que permitem que um host interaja com o sistema de coleta de lixo do CLR.</span><span class="sxs-lookup"><span data-stu-id="45ae9-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="45ae9-131">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-131">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="45ae9-132">Fornece métodos para o host avaliar e comunicar alterações nas informações de política para assemblies.</span><span class="sxs-lookup"><span data-stu-id="45ae9-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="45ae9-133">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-133">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="45ae9-134">Permite que o host bloqueie classes gerenciadas, métodos, propriedades e campos específicos da execução em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="45ae9-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="45ae9-135">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="45ae9-136">Implementa um método de retorno de chamada que permite ao host notificar o CLR do status de solicitações de e/s especificadas.</span><span class="sxs-lookup"><span data-stu-id="45ae9-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="45ae9-137">Interface ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="45ae9-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="45ae9-138">Permite que o host relate condições de pressão de memória usando uma abordagem semelhante à da `CreateMemoryResourceNotification` função do Win32.</span><span class="sxs-lookup"><span data-stu-id="45ae9-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="45ae9-139">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-139">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="45ae9-140">Fornece métodos que permitem ao host registrar e cancelar o registro de retornos de chamada para eventos CLR.</span><span class="sxs-lookup"><span data-stu-id="45ae9-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="45ae9-141">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="45ae9-142">Fornece métodos que permitem que o host especifique ações de política a serem executadas em caso de falhas e tempos limite.</span><span class="sxs-lookup"><span data-stu-id="45ae9-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="45ae9-143">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="45ae9-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="45ae9-144">Fornece métodos que permitem ao host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que são internas ao CLR, sem a necessidade de criar ou compreender essa identidade.</span><span class="sxs-lookup"><span data-stu-id="45ae9-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="45ae9-145">Interface ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="45ae9-145">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="45ae9-146">Fornece métodos que permitem ao host manipular o conjunto de assemblies referenciados por um arquivo ou fluxo usando dados de identidade de assembly que são internos ao CLR, sem a necessidade de criar ou compreender essas identidades.</span><span class="sxs-lookup"><span data-stu-id="45ae9-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="45ae9-147">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="45ae9-147">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="45ae9-148">Fornece recursos semelhantes a [ICorRuntimeHost](icorruntimehost-interface.md), com um método adicional para definir a interface de controle de host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-148">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="45ae9-149">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-149">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="45ae9-150">Fornece métodos para o host obter informações sobre as tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.</span><span class="sxs-lookup"><span data-stu-id="45ae9-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="45ae9-151">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="45ae9-151">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="45ae9-152">Fornece métodos que permitem ao host fazer solicitações do CLR ou fornecer notificação ao CLR sobre a tarefa associada.</span><span class="sxs-lookup"><span data-stu-id="45ae9-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="45ae9-153">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="45ae9-154">Fornece métodos que permitem que o host solicite explicitamente que o CLR crie uma nova tarefa, obtenha a tarefa em execução no momento e defina o idioma geográfico e a cultura da tarefa.</span><span class="sxs-lookup"><span data-stu-id="45ae9-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="45ae9-155">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="45ae9-155">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="45ae9-156">Fornece métodos para validar imagens executáveis portáteis (PE) e relatar erros de validação.</span><span class="sxs-lookup"><span data-stu-id="45ae9-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="45ae9-157">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="45ae9-157">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="45ae9-158">Fornece métodos para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="45ae9-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="45ae9-159">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="45ae9-159">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="45ae9-160">Fornece métodos para acessar o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="45ae9-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="45ae9-161">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="45ae9-161">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="45ae9-162">Fornece métodos para obter informações sobre o estado dos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="45ae9-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="45ae9-163">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="45ae9-163">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="45ae9-164">Fornece métodos para notificar o host sobre o bloqueio e o desbloqueio de threads pelos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="45ae9-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="45ae9-165">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="45ae9-165">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="45ae9-166">Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="45ae9-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="45ae9-167">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="45ae9-167">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="45ae9-168">Fornece o método [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) que permite que um host defina o tamanho do segmento de coleta de lixo e o tamanho máximo da geração de zero do sistema de coleta de lixo com valores maiores que `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="45ae9-168">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="45ae9-169">Interface IGCHostControl</span><span class="sxs-lookup"><span data-stu-id="45ae9-169">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="45ae9-170">Fornece um método que permite que o coletor de lixo solicite o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="45ae9-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="45ae9-171">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="45ae9-171">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="45ae9-172">Fornece métodos para participar do agendamento de threads que, de outra forma, seriam bloqueados para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="45ae9-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="45ae9-173">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-173">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="45ae9-174">Fornece métodos que permitem que um host especifique conjuntos de assemblies que devem ser carregados pelo CLR ou pelo host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="45ae9-175">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="45ae9-175">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="45ae9-176">Fornece métodos que permitem que um host carregue assemblies e módulos independentemente do CLR.</span><span class="sxs-lookup"><span data-stu-id="45ae9-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="45ae9-177">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="45ae9-177">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="45ae9-178">Fornece uma representação de um evento de redefinição automática implementado pelo host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="45ae9-179">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="45ae9-179">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="45ae9-180">Fornece métodos para configurar o carregamento de assemblies e para determinar a quais interfaces de hospedagem o host dá suporte.</span><span class="sxs-lookup"><span data-stu-id="45ae9-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="45ae9-181">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="45ae9-181">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="45ae9-182">Serve como a representação do host de uma seção crítica para Threading.</span><span class="sxs-lookup"><span data-stu-id="45ae9-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="45ae9-183">Interface IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-183">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="45ae9-184">Fornece métodos que notificam o host de eventos no mecanismo de coleta de lixo implementado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="45ae9-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="45ae9-185">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-185">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="45ae9-186">Fornece métodos que permitem que o CLR interaja com portas de conclusão de e/s fornecidas pelo host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="45ae9-187">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="45ae9-187">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="45ae9-188">Fornece métodos para que o CLR solicite alocações refinadas do heap por meio do host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="45ae9-189">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="45ae9-189">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="45ae9-190">Fornece a implementação do host de uma representação de um evento de redefinição manual.</span><span class="sxs-lookup"><span data-stu-id="45ae9-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="45ae9-191">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-191">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="45ae9-192">Fornece métodos para que o CLR faça solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual Win32 padrão.</span><span class="sxs-lookup"><span data-stu-id="45ae9-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="45ae9-193">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-193">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="45ae9-194">Fornece métodos que notificam o host das ações que o CLR executa em caso de anulações, tempos limite ou falhas.</span><span class="sxs-lookup"><span data-stu-id="45ae9-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="45ae9-195">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="45ae9-195">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="45ae9-196">Permite que o CLR mantenha informações de contexto de segurança implementadas pelo host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="45ae9-197">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-197">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="45ae9-198">Fornece métodos que habilitam o acesso e o controle sobre o contexto de segurança do thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="45ae9-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="45ae9-199">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="45ae9-199">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="45ae9-200">Fornece uma representação de um semáforo implementado pelo host.</span><span class="sxs-lookup"><span data-stu-id="45ae9-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="45ae9-201">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-201">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="45ae9-202">Fornece métodos para que o CLR crie primitivos de sincronização chamando o host, em vez de usar as funções de sincronização do Win32.</span><span class="sxs-lookup"><span data-stu-id="45ae9-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="45ae9-203">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="45ae9-203">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="45ae9-204">Fornece métodos que permitem que o CLR se comunique com o host para gerenciar tarefas.</span><span class="sxs-lookup"><span data-stu-id="45ae9-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="45ae9-205">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-205">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="45ae9-206">Fornece métodos que permitem que o CLR trabalhe com tarefas por meio do host em vez de usar as funções de fibra ou de Threading do sistema operacional padrão.</span><span class="sxs-lookup"><span data-stu-id="45ae9-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="45ae9-207">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="45ae9-207">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="45ae9-208">Fornece métodos para que o CLR configure o pool de threads e enfileirar itens de trabalho para o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="45ae9-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="45ae9-209">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="45ae9-209">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="45ae9-210">Fornece métodos para controlar um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="45ae9-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="45ae9-211">"IObjectHandle"</span><span class="sxs-lookup"><span data-stu-id="45ae9-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="45ae9-212">Fornece um método para desencapsular objetos Marshal-by-Value do indireção.</span><span class="sxs-lookup"><span data-stu-id="45ae9-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="45ae9-213">Interface ITypeName</span><span class="sxs-lookup"><span data-stu-id="45ae9-213">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="45ae9-214">Fornece métodos para obter informações de nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="45ae9-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="45ae9-215">(Essa interface dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.)</span><span class="sxs-lookup"><span data-stu-id="45ae9-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="45ae9-216">Interface ITypeNameBuilder</span><span class="sxs-lookup"><span data-stu-id="45ae9-216">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="45ae9-217">Fornece métodos para criar um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="45ae9-217">Provides methods for building a type name.</span></span> <span data-ttu-id="45ae9-218">(Essa interface dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.)</span><span class="sxs-lookup"><span data-stu-id="45ae9-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="45ae9-219">Interface ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="45ae9-219">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="45ae9-220">Fornece métodos para decompor um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="45ae9-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="45ae9-221">(Essa interface dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.)</span><span class="sxs-lookup"><span data-stu-id="45ae9-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="45ae9-222">IValidator</span><span class="sxs-lookup"><span data-stu-id="45ae9-222">"IValidator"</span></span>  
 <span data-ttu-id="45ae9-223">Fornece métodos para validar imagens executáveis portáteis (PE) e relatar erros de validação.</span><span class="sxs-lookup"><span data-stu-id="45ae9-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="45ae9-224">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="45ae9-224">Related Sections</span></span>  
 [<span data-ttu-id="45ae9-225">Interfaces e coclasse de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="45ae9-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="45ae9-226">Contém tópicos que descrevem as interfaces de hospedagem fornecidas no .NET Framework versão 1,0 e 1,1.</span><span class="sxs-lookup"><span data-stu-id="45ae9-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="45ae9-227">Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="45ae9-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="45ae9-228">Contém tópicos que descrevem as interfaces de hospedagem fornecidas no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="45ae9-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
