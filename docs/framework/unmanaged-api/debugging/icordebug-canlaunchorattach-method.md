---
title: Método ICorDebug::CanLaunchOrAttach
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 354df02b27e87550ba602fe102352455c227441b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859678"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="e5a8c-102">Método ICorDebug::CanLaunchOrAttach</span><span class="sxs-lookup"><span data-stu-id="e5a8c-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="e5a8c-103">Retorna um HRESULT que indica se é possível iniciar um novo processo ou anexar ao processo existente especificado no contexto da configuração atual do computador e do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a8c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5a8c-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5a8c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5a8c-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="e5a8c-106">no A ID de um processo existente.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="e5a8c-107">no Passe `true` se você planeja iniciar com a depuração do Win32 habilitada ou para anexar com a depuração do Win32 habilitada; caso contrário, `false`passe.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5a8c-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e5a8c-108">Return Value</span></span>  
 <span data-ttu-id="e5a8c-109">S_OK se os serviços de depuração determinarem que a inicialização de um novo processo ou a anexação ao processo fornecido é possível, dadas as informações sobre o computador atual e a configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="e5a8c-110">Os possíveis valores HRESULT são:</span><span class="sxs-lookup"><span data-stu-id="e5a8c-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="e5a8c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5a8c-111">S_OK</span></span>  
  
- <span data-ttu-id="e5a8c-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="e5a8c-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="e5a8c-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="e5a8c-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="e5a8c-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="e5a8c-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5a8c-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5a8c-115">Remarks</span></span>  
 <span data-ttu-id="e5a8c-116">Esse método é puramente informativo.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-116">This method is purely informational.</span></span> <span data-ttu-id="e5a8c-117">A interface não o impedirá de iniciar ou anexar a um processo, independentemente do valor retornado por `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="e5a8c-118">Se você planeja iniciar com a depuração do Win32 habilitada ou anexada à depuração do `true` Win32 `win32DebuggingEnabled`habilitada, passe para.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="e5a8c-119">O HRESULT retornado por `CanLaunchOrAttach` pode ser diferente se você usar essa opção.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5a8c-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5a8c-120">Requirements</span></span>  
 <span data-ttu-id="e5a8c-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5a8c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5a8c-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5a8c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5a8c-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5a8c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5a8c-124">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5a8c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a8c-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="e5a8c-125">See also</span></span>

- [<span data-ttu-id="e5a8c-126">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="e5a8c-126">ICorDebug Interface</span></span>](icordebug-interface.md)
