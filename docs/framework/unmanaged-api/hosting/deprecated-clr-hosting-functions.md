---
title: Funções de hospedagem CLR reprovadas
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 9e19502672973f292991b72c7ea9b4fdc17f5707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673118"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="16968-102">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="16968-102">Deprecated CLR Hosting Functions</span></span>

<span data-ttu-id="16968-103">Esta seção descreve as funções estáticas globais não gerenciadas que as versões anteriores da API de hospedagem usavam.</span><span class="sxs-lookup"><span data-stu-id="16968-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="16968-104">Com exceção das funções de infraestrutura ( `_Cor*` funções), que são usadas somente pelo .NET Framework, essas funções foram preteridas no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="16968-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="16968-105">Funções de ativação</span><span class="sxs-lookup"><span data-stu-id="16968-105">Activation functions</span></span>  

 [<span data-ttu-id="16968-106">Função ClrCreateManagedInstance</span><span class="sxs-lookup"><span data-stu-id="16968-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="16968-107">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-107">Deprecated.</span></span> <span data-ttu-id="16968-108">Cria uma instância do tipo gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="16968-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="16968-109">Função CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="16968-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="16968-110">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="16968-110">Obsolete.</span></span> <span data-ttu-id="16968-111">Para inicializar o Common Language Runtime (CLR), use [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="16968-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="16968-112">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="16968-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="16968-113">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-113">Deprecated.</span></span> <span data-ttu-id="16968-114">Garante que o mecanismo de execução do CLR seja carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="16968-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="16968-115">Em vez disso, use o método [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="16968-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="16968-116">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="16968-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="16968-117">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-117">Deprecated.</span></span> <span data-ttu-id="16968-118">Carrega o Common Language Runtime (CLR) em um processo usando as informações de versão armazenadas em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="16968-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="16968-119">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="16968-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="16968-120">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-120">Deprecated.</span></span> <span data-ttu-id="16968-121">Permite que hosts não gerenciados carreguem o CLR em um processo.</span><span class="sxs-lookup"><span data-stu-id="16968-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="16968-122">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="16968-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="16968-123">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-123">Deprecated.</span></span> <span data-ttu-id="16968-124">Carrega o CLR em um processo usando informações de versão lidas de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="16968-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="16968-125">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="16968-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="16968-126">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-126">Deprecated.</span></span> <span data-ttu-id="16968-127">Permite que hosts não gerenciados carreguem o CLR em um processo e permite que você defina sinalizadores para especificar o comportamento do CLR.</span><span class="sxs-lookup"><span data-stu-id="16968-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="16968-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="16968-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="16968-129">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-129">Deprecated.</span></span> <span data-ttu-id="16968-130">Permite que os hosts carreguem uma versão especificada do CLR em um processo.</span><span class="sxs-lookup"><span data-stu-id="16968-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="16968-131">Função GetCORRequiredVersion</span><span class="sxs-lookup"><span data-stu-id="16968-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="16968-132">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-132">Deprecated.</span></span> <span data-ttu-id="16968-133">Obtém o número de versão do CLR necessário.</span><span class="sxs-lookup"><span data-stu-id="16968-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="16968-134">Função GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="16968-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="16968-135">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-135">Deprecated.</span></span> <span data-ttu-id="16968-136">Retorna o diretório de instalação do CLR que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="16968-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="16968-137">Função GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="16968-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="16968-138">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-138">Deprecated.</span></span> <span data-ttu-id="16968-139">Obtém o endereço da função especificada que é exportada da última versão instalada do CLR.</span><span class="sxs-lookup"><span data-stu-id="16968-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="16968-140">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="16968-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="16968-141">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-141">Deprecated.</span></span> <span data-ttu-id="16968-142">Obtém informações de versão e diretório sobre o CLR solicitado por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16968-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="16968-143">Funções de versão do CLR</span><span class="sxs-lookup"><span data-stu-id="16968-143">CLR version functions</span></span>  

 <span data-ttu-id="16968-144">As funções nesta seção retornam uma versão do CLR; Eles não ativam o CLR.</span><span class="sxs-lookup"><span data-stu-id="16968-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="16968-145">Função GetCORVersion</span><span class="sxs-lookup"><span data-stu-id="16968-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="16968-146">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-146">Deprecated.</span></span> <span data-ttu-id="16968-147">Retorna o número de versão do CLR que está sendo executado no processo atual.</span><span class="sxs-lookup"><span data-stu-id="16968-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="16968-148">Função GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="16968-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="16968-149">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-149">Deprecated.</span></span> <span data-ttu-id="16968-150">Obtém as informações de versão do CLR do arquivo especificado, usando o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="16968-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="16968-151">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="16968-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="16968-152">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-152">Deprecated.</span></span> <span data-ttu-id="16968-153">Obtém o número de versão do CLR solicitado pelo aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="16968-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="16968-154">Se essa versão não estiver instalada, o obterá a versão mais recente instalada antes da versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="16968-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="16968-155">Função GetRequestedRuntimeVersionForCLSID</span><span class="sxs-lookup"><span data-stu-id="16968-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="16968-156">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-156">Deprecated.</span></span> <span data-ttu-id="16968-157">Obtém as informações de versão do CLR apropriadas para a classe com o CLSID especificado.</span><span class="sxs-lookup"><span data-stu-id="16968-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="16968-158">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="16968-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="16968-159">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-159">Deprecated.</span></span> <span data-ttu-id="16968-160">Obtém o número de versão do CLR associado ao identificador de processo especificado.</span><span class="sxs-lookup"><span data-stu-id="16968-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="16968-161">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="16968-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="16968-162">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-162">Deprecated.</span></span> <span data-ttu-id="16968-163">Permite que o host determine qual versão do CLR será usada dentro do processo antes de inicializar explicitamente o CLR.</span><span class="sxs-lookup"><span data-stu-id="16968-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="16968-164">Funções de hospedagem</span><span class="sxs-lookup"><span data-stu-id="16968-164">Hosting functions</span></span>  

 [<span data-ttu-id="16968-165">Função CallFunctionShim</span><span class="sxs-lookup"><span data-stu-id="16968-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="16968-166">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-166">Deprecated.</span></span> <span data-ttu-id="16968-167">Faz uma chamada para a função que tem o nome e os parâmetros especificados na biblioteca especificada.</span><span class="sxs-lookup"><span data-stu-id="16968-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="16968-168">Função CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="16968-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="16968-169">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-169">Deprecated.</span></span> <span data-ttu-id="16968-170">Descarrega um assembly COM do processo.</span><span class="sxs-lookup"><span data-stu-id="16968-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="16968-171">Função CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="16968-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="16968-172">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-172">Deprecated.</span></span> <span data-ttu-id="16968-173">Desliga o processo atual não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="16968-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="16968-174">Função CorLaunchApplication</span><span class="sxs-lookup"><span data-stu-id="16968-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="16968-175">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-175">Deprecated.</span></span> <span data-ttu-id="16968-176">Inicia o aplicativo no caminho de rede especificado, usando os manifestos especificados e outros dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16968-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="16968-177">Função CorMarkThreadInThreadPool</span><span class="sxs-lookup"><span data-stu-id="16968-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="16968-178">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-178">Deprecated.</span></span> <span data-ttu-id="16968-179">Marca o thread do pool de threads em execução no momento para a execução do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="16968-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="16968-180">A partir do .NET Framework versão 2,0, essa função não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="16968-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="16968-181">Ela não é necessária e pode ser removida do seu código.</span><span class="sxs-lookup"><span data-stu-id="16968-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="16968-182">Função CoUninitializeCor</span><span class="sxs-lookup"><span data-stu-id="16968-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="16968-183">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="16968-183">Obsolete.</span></span> <span data-ttu-id="16968-184">O CLR não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="16968-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="16968-185">Função CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="16968-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="16968-186">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="16968-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="16968-187">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="16968-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="16968-188">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-188">Deprecated.</span></span> <span data-ttu-id="16968-189">Cria um objeto [ICorDebug](../debugging/icordebug-interface.md) com base nas informações de versão especificadas.</span><span class="sxs-lookup"><span data-stu-id="16968-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="16968-190">Função CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="16968-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="16968-191">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-191">Deprecated.</span></span> <span data-ttu-id="16968-192">Cria um objeto [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="16968-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="16968-193">Função DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="16968-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="16968-194">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-194">Deprecated.</span></span> <span data-ttu-id="16968-195">Destrói um objeto [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="16968-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="16968-196">Ponteiro de função FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="16968-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="16968-197">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-197">Deprecated.</span></span> <span data-ttu-id="16968-198">Aponta para uma função que o CLR chama para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="16968-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="16968-199">Ponteiro de função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="16968-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="16968-200">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-200">Deprecated.</span></span> <span data-ttu-id="16968-201">Aponta para uma função que o CLR chama para notificar o host de que a inicialização foi iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="16968-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="16968-202">Função GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="16968-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="16968-203">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-203">Deprecated.</span></span> <span data-ttu-id="16968-204">Obtém um ponteiro para uma interface que permite que o CLR gerencie identidades.</span><span class="sxs-lookup"><span data-stu-id="16968-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="16968-205">Função LoadLibraryShim</span><span class="sxs-lookup"><span data-stu-id="16968-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="16968-206">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-206">Deprecated.</span></span> <span data-ttu-id="16968-207">Carrega uma versão especificada de uma .NET Framework DLL.</span><span class="sxs-lookup"><span data-stu-id="16968-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="16968-208">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="16968-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="16968-209">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-209">Deprecated.</span></span> <span data-ttu-id="16968-210">Traduz um valor HRESULT em uma mensagem de erro usando a cultura padrão do thread atual.</span><span class="sxs-lookup"><span data-stu-id="16968-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="16968-211">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="16968-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="16968-212">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-212">Deprecated.</span></span> <span data-ttu-id="16968-213">Traduz um valor HRESULT para uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="16968-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="16968-214">Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="16968-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="16968-215">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-215">Deprecated.</span></span> <span data-ttu-id="16968-216">Aponta para uma função que notifica o host quando uma e/s sobreposta (ou seja, assíncrona) para um dispositivo for concluída.</span><span class="sxs-lookup"><span data-stu-id="16968-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="16968-217">Ponteiro de função LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="16968-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="16968-218">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-218">Deprecated.</span></span> <span data-ttu-id="16968-219">Aponta para uma função que notifica o host que um thread começou a ser executado.</span><span class="sxs-lookup"><span data-stu-id="16968-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="16968-220">Função RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="16968-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="16968-221">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-221">Deprecated.</span></span> <span data-ttu-id="16968-222">Executa o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="16968-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="16968-223">Ponteiro de função WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="16968-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="16968-224">Preterido.</span><span class="sxs-lookup"><span data-stu-id="16968-224">Deprecated.</span></span> <span data-ttu-id="16968-225">Aponta para uma função que notifica o host de que um identificador de espera foi sinalizado ou atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="16968-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="16968-226">Funções de infraestrutura</span><span class="sxs-lookup"><span data-stu-id="16968-226">Infrastructure functions</span></span>  

 <span data-ttu-id="16968-227">As funções nesta seção são para uso apenas pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16968-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="16968-228">Função _CorDllMain</span><span class="sxs-lookup"><span data-stu-id="16968-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="16968-229">Inicializa o CLR, localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly de DLL e começa a execução.</span><span class="sxs-lookup"><span data-stu-id="16968-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="16968-230">Função _CorExeMain</span><span class="sxs-lookup"><span data-stu-id="16968-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="16968-231">Inicializa o CLR, localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly executável e começa a execução.</span><span class="sxs-lookup"><span data-stu-id="16968-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="16968-232">Função _CorExeMain2</span><span class="sxs-lookup"><span data-stu-id="16968-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="16968-233">Executa o ponto de entrada no código mapeado de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="16968-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="16968-234">Essa função é chamada pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="16968-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="16968-235">Função _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="16968-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="16968-236">Notifica o carregador quando as imagens do módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="16968-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="16968-237">Função _CorValidateImage</span><span class="sxs-lookup"><span data-stu-id="16968-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="16968-238">Valida as imagens de módulo gerenciado e notifica o carregador do sistema operacional depois que elas tiverem sido carregadas.</span><span class="sxs-lookup"><span data-stu-id="16968-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16968-239">Confira também</span><span class="sxs-lookup"><span data-stu-id="16968-239">See also</span></span>

- [<span data-ttu-id="16968-240">.NET Framework 4 hospedando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="16968-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
