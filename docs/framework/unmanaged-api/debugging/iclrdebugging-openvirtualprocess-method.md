---
title: Método ICLRDebugging::OpenVirtualProcess
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: 585b3d605d0df9169c12ca10198846ec0a7fe6d4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793605"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="3837b-102">Método ICLRDebugging::OpenVirtualProcess</span><span class="sxs-lookup"><span data-stu-id="3837b-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="3837b-103">Obtém a interface ICorDebugProcess que corresponde a um módulo Common Language Runtime (CLR) carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="3837b-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3837b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3837b-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3837b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3837b-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="3837b-106">no O endereço base de um módulo no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="3837b-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="3837b-107">COR_E_NOT_CLR será retornado se o módulo especificado não for um módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="3837b-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="3837b-108">no Uma abstração de destino de dados que permite que o depurador gerenciado Inspecione o estado do processo.</span><span class="sxs-lookup"><span data-stu-id="3837b-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="3837b-109">O depurador deve implementar a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3837b-109">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="3837b-110">Você deve implementar a interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) para dar suporte a cenários em que o CLR que está sendo depurado não está instalado localmente no computador.</span><span class="sxs-lookup"><span data-stu-id="3837b-110">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="3837b-111">no Uma interface de retorno de chamada do provedor de biblioteca que permite que bibliotecas de depuração específicas da versão sejam localizadas e carregadas sob demanda.</span><span class="sxs-lookup"><span data-stu-id="3837b-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="3837b-112">Esse parâmetro será necessário somente se `ppProcess` ou `pFlags` não estiver `null`.</span><span class="sxs-lookup"><span data-stu-id="3837b-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="3837b-113">no A versão mais recente do CLR que este depurador pode depurar.</span><span class="sxs-lookup"><span data-stu-id="3837b-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="3837b-114">Você deve especificar as versões principal, secundária e de compilação da última versão do CLR à qual este depurador dá suporte e definir o número de revisão como 65535 para acomodar futuras versões de serviço do CLR in-loco.</span><span class="sxs-lookup"><span data-stu-id="3837b-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="3837b-115">no A ID da interface ICorDebugProcess a ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="3837b-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="3837b-116">Atualmente, os únicos valores aceitos são IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 e IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="3837b-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="3837b-117">fora Um ponteiro para a interface COM que é identificado por `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="3837b-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="3837b-118">[entrada, saída] A versão do CLR.</span><span class="sxs-lookup"><span data-stu-id="3837b-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="3837b-119">Na entrada, esse valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="3837b-119">On input, this value can be `null`.</span></span> <span data-ttu-id="3837b-120">Ele também pode apontar para uma estrutura de [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) ; nesse caso, o campo de `wStructVersion` da estrutura deve ser inicializado como 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="3837b-120">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="3837b-121">Na saída, a estrutura de `CLR_DEBUGGING_VERSION` retornada será preenchida com as informações de versão do CLR.</span><span class="sxs-lookup"><span data-stu-id="3837b-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="3837b-122">fora Sinalizadores informativos sobre o tempo de execução especificado.</span><span class="sxs-lookup"><span data-stu-id="3837b-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="3837b-123">Consulte o tópico [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) para obter uma descrição dos sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="3837b-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3837b-124">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3837b-124">Return Value</span></span>  
 <span data-ttu-id="3837b-125">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="3837b-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3837b-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3837b-126">HRESULT</span></span>|<span data-ttu-id="3837b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="3837b-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3837b-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="3837b-128">S_OK</span></span>|<span data-ttu-id="3837b-129">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="3837b-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="3837b-130">{1&gt;E_POINTER&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3837b-130">E_POINTER</span></span>|<span data-ttu-id="3837b-131">`pDataTarget` é `null`.</span><span class="sxs-lookup"><span data-stu-id="3837b-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="3837b-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="3837b-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="3837b-133">O retorno de chamada [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) retorna um erro ou não fornece um identificador válido.</span><span class="sxs-lookup"><span data-stu-id="3837b-133">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="3837b-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="3837b-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="3837b-135">`pDataTarget` não implementa as interfaces de destino de dados necessárias para esta versão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3837b-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="3837b-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="3837b-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="3837b-137">O módulo indicado não é um módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="3837b-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="3837b-138">Esse HRESULT também é retornado quando um módulo CLR não pode ser detectado porque a memória foi corrompida, o módulo não está disponível ou a versão do CLR é posterior à versão de Shim.</span><span class="sxs-lookup"><span data-stu-id="3837b-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="3837b-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="3837b-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="3837b-140">Esta versão de tempo de execução não dá suporte a este modelo de depuração.</span><span class="sxs-lookup"><span data-stu-id="3837b-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="3837b-141">Atualmente, o modelo de depuração não tem suporte das versões do CLR antes do .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3837b-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="3837b-142">O parâmetro de saída `pwszVersion` ainda é definido como o valor correto após esse erro.</span><span class="sxs-lookup"><span data-stu-id="3837b-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="3837b-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="3837b-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="3837b-144">A versão do CLR é maior que a versão que este depurador declara para dar suporte.</span><span class="sxs-lookup"><span data-stu-id="3837b-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="3837b-145">O parâmetro de saída `pwszVersion` ainda é definido como o valor correto após esse erro.</span><span class="sxs-lookup"><span data-stu-id="3837b-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="3837b-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="3837b-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="3837b-147">A interface `riidProcess` não está disponível.</span><span class="sxs-lookup"><span data-stu-id="3837b-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="3837b-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="3837b-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="3837b-149">A estrutura de `CLR_DEBUGGING_VERSION` não tem um valor reconhecido para `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="3837b-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="3837b-150">O único valor aceito neste momento é 0.</span><span class="sxs-lookup"><span data-stu-id="3837b-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="3837b-151">Exceções</span><span class="sxs-lookup"><span data-stu-id="3837b-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3837b-152">Comentários</span><span class="sxs-lookup"><span data-stu-id="3837b-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3837b-153">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="3837b-153">Requirements</span></span>  
 <span data-ttu-id="3837b-154">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3837b-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3837b-155">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3837b-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3837b-156">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3837b-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3837b-157">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3837b-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3837b-158">Veja também</span><span class="sxs-lookup"><span data-stu-id="3837b-158">See also</span></span>

- [<span data-ttu-id="3837b-159">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3837b-159">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3837b-160">Depuração</span><span class="sxs-lookup"><span data-stu-id="3837b-160">Debugging</span></span>](index.md)
