---
title: Função CorBindToRuntime
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 426e95281b648217642ca06f04dfbd9ec991221e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733770"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="f7bc5-102">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="f7bc5-102">CorBindToRuntime Function</span></span>

<span data-ttu-id="f7bc5-103">Permite que hosts não gerenciados carreguem o Common Language Runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="f7bc5-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bc5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7bc5-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7bc5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7bc5-106">Parameters</span></span>  

 `pwszVersion`  
 <span data-ttu-id="f7bc5-107">no Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="f7bc5-108">Um número de versão no .NET Framework consiste em quatro partes separadas por pontos: *Major. Minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="f7bc5-109">A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número de versão (por exemplo, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="f7bc5-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="f7bc5-110">Algumas versões do CLR são instaladas com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="f7bc5-111">Por padrão, o Shim de inicialização `pwszVersion` é avaliado em relação a instruções de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="f7bc5-112">Um host pode forçar o Shim a ignorar a avaliação da política e carregar a versão exata especificada no `pwszVersion` passando um valor de  `STARTUP_LOADER_SAFEMODE` para o `flags` parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="f7bc5-113">Se o chamador especificar NULL para `pwszVersion` , a versão mais recente do tempo de execução será carregada.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="f7bc5-114">A passagem de NULL fornece ao host nenhum controle sobre qual versão do tempo de execução está carregada.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="f7bc5-115">Embora essa abordagem possa ser apropriada em alguns cenários, é altamente recomendável que o host forneça uma versão específica para carregar.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="f7bc5-116">no Uma cadeia de caracteres que especifica se o servidor ou a compilação da estação de trabalho do CLR deve ser carregada.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="f7bc5-117">Os valores válidos são `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="f7bc5-118">A compilação do servidor é otimizada para aproveitar vários processadores para coletas de lixo e a compilação da estação de trabalho é otimizada para aplicativos cliente em execução em um computador com um único processador.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="f7bc5-119">Se `pwszBuildFlavor` é definido como NULL, a compilação da estação de trabalho é carregada.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="f7bc5-120">Durante a execução em um computador com um único processador, a compilação da estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` estiver definida como `svr` .</span><span class="sxs-lookup"><span data-stu-id="f7bc5-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="f7bc5-121">No entanto, se `pwszBuildFlavor` for definido como `svr` e a coleta de lixo simultânea for especificada (consulte a descrição do `flags` parâmetro), a compilação do servidor será carregada.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="f7bc5-122">no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f7bc5-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="f7bc5-123">Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="f7bc5-124">no O `IID` da interface solicitada de `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="f7bc5-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="f7bc5-125">Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f7bc5-126">fora O ponteiro de interface retornado para `riid` .</span><span class="sxs-lookup"><span data-stu-id="f7bc5-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7bc5-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7bc5-127">Remarks</span></span>  

 <span data-ttu-id="f7bc5-128">Se `pwszVersion` o especificar uma versão de tempo de execução que não existe, `CorBindToRuntimeEx` o retornará um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="f7bc5-129">Contexto de execução e fluxo de identidade do Windows</span><span class="sxs-lookup"><span data-stu-id="f7bc5-129">Execution Context and Flow of Windows Identity</span></span>  

 <span data-ttu-id="f7bc5-130">Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> objeto não flui em pontos assíncronos, como novos threads, pools de threads ou retornos de chamada de temporizador.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="f7bc5-131">Na versão 2,0 do CLR, um <xref:System.Threading.ExecutionContext> objeto encapsula algumas informações sobre o thread em execução no momento e o flui em qualquer ponto assíncrono, mas não entre os limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="f7bc5-132">Da mesma forma, o <xref:System.Security.Principal.WindowsIdentity> objeto também flui em qualquer ponto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="f7bc5-133">Portanto, a representação atual no thread, se houver, flui também.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="f7bc5-134">Você pode alterar o fluxo de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="f7bc5-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="f7bc5-135">Modificando as <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo em uma base por thread (consulte os <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> métodos, e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="f7bc5-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="f7bc5-136">Alterando o modo padrão do processo para o modo de compatibilidade da versão 1, em que o <xref:System.Security.Principal.WindowsIdentity> objeto não flui em nenhum ponto assíncrono, independentemente das <xref:System.Threading.ExecutionContext> configurações no thread atual.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="f7bc5-137">A maneira como você altera o modo padrão depende se você usa um executável gerenciado ou uma interface de hospedagem não gerenciada para carregar o CLR:</span><span class="sxs-lookup"><span data-stu-id="f7bc5-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="f7bc5-138">Para executáveis gerenciados, você deve definir o `enabled` atributo do [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elemento como `true` .</span><span class="sxs-lookup"><span data-stu-id="f7bc5-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="f7bc5-139">Para interfaces de hospedagem não gerenciadas, defina o `STARTUP_LEGACY_IMPERSONATION` sinalizador no `flags` parâmetro ao chamar a `CorBindToRuntimeEx` função.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="f7bc5-140">O modo de compatibilidade da versão 1 se aplica a todo o processo e a todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7bc5-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7bc5-141">Remarks</span></span>  

 <span data-ttu-id="f7bc5-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) e `CorBindToRuntime` executam a mesma operação, mas a `CorBindToRuntimeEx` função permite que você defina sinalizadores para especificar o comportamento do CLR.</span><span class="sxs-lookup"><span data-stu-id="f7bc5-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7bc5-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7bc5-143">Requirements</span></span>  

 <span data-ttu-id="f7bc5-144">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7bc5-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7bc5-145">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f7bc5-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7bc5-146">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7bc5-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7bc5-147">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7bc5-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bc5-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="f7bc5-148">See also</span></span>

- [<span data-ttu-id="f7bc5-149">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="f7bc5-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="f7bc5-150">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="f7bc5-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="f7bc5-151">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="f7bc5-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="f7bc5-152">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f7bc5-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="f7bc5-153">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f7bc5-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="f7bc5-154">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="f7bc5-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
