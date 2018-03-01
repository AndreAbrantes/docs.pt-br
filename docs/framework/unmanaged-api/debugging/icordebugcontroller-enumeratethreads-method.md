---
title: "Método ICorDebugController::EnumerateThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61d96aa6c8ae4a50c3afbcd84033244208e2444d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="3522a-102">Método ICorDebugController::EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="3522a-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="3522a-103">Obtém um enumerador para os threads gerenciados ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="3522a-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3522a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3522a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3522a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3522a-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="3522a-106">[out] Um ponteiro para o endereço de um objeto de "ICorDebugThreadEnum" que representa um enumerador para todos os threads gerenciados que estão ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="3522a-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3522a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3522a-107">Remarks</span></span>  
 <span data-ttu-id="3522a-108">Um thread é considerado ativo após o [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) retorno de chamada foi enviado e antes do [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) retorno de chamada foi distribuído .</span><span class="sxs-lookup"><span data-stu-id="3522a-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="3522a-109">Um thread gerenciado não pode ter necessariamente quadros gerenciados na pilha.</span><span class="sxs-lookup"><span data-stu-id="3522a-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="3522a-110">Threads podem ser enumerados mesmo antes de [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3522a-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="3522a-111">A enumeração naturalmente estará vazia.</span><span class="sxs-lookup"><span data-stu-id="3522a-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3522a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3522a-112">Requirements</span></span>  
 <span data-ttu-id="3522a-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3522a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3522a-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3522a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3522a-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3522a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3522a-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3522a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3522a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3522a-117">See Also</span></span>  
 
