---
title: Método ICorDebugManagedCallback2::FunctionRemapComplete
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
ms.openlocfilehash: 7eb7fb55a5077d2914eb85a67ca62163a1aa8cc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704585"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="1450f-102">Método ICorDebugManagedCallback2::FunctionRemapComplete</span><span class="sxs-lookup"><span data-stu-id="1450f-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>

<span data-ttu-id="1450f-103">Notifica o depurador de que a execução de código mudou para uma nova versão de uma função editada.</span><span class="sxs-lookup"><span data-stu-id="1450f-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1450f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1450f-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1450f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1450f-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="1450f-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém a função editada.</span><span class="sxs-lookup"><span data-stu-id="1450f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1450f-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual o ponto de interrupção do remapeamento foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="1450f-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="1450f-108">no Um ponteiro para um objeto ICorDebugFunction que representa a versão da função em execução no momento no thread.</span><span class="sxs-lookup"><span data-stu-id="1450f-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1450f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="1450f-109">Remarks</span></span>  

 <span data-ttu-id="1450f-110">Esse retorno de chamada dá ao depurador uma oportunidade de recriar todos os apresentadores que existiam anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1450f-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1450f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1450f-111">Requirements</span></span>  

 <span data-ttu-id="1450f-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1450f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1450f-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1450f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1450f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1450f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1450f-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1450f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1450f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="1450f-116">See also</span></span>

- [<span data-ttu-id="1450f-117">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="1450f-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="1450f-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="1450f-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
