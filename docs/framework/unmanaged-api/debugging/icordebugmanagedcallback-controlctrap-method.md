---
title: Método ICorDebugManagedCallback::ControlCTrap
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 0c38269ea4d730d8f3f9ba5d2c5d8f0edf6d7d45
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731821"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="4d38c-102">Método ICorDebugManagedCallback::ControlCTrap</span><span class="sxs-lookup"><span data-stu-id="4d38c-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>

<span data-ttu-id="4d38c-103">Notifica o depurador de que um CTRL + C foi interceptado no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="4d38c-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d38c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d38c-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d38c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d38c-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="4d38c-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o CTRL + C é interceptado.</span><span class="sxs-lookup"><span data-stu-id="4d38c-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d38c-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="4d38c-107">Return Value</span></span>  
  
|<span data-ttu-id="4d38c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d38c-108">HRESULT</span></span>|<span data-ttu-id="4d38c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d38c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d38c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4d38c-110">S_OK</span></span>|<span data-ttu-id="4d38c-111">O depurador manipulará a interceptação CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="4d38c-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="4d38c-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4d38c-112">S_FALSE</span></span>|<span data-ttu-id="4d38c-113">O depurador não tratará a interceptação CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="4d38c-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d38c-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d38c-114">Remarks</span></span>  

 <span data-ttu-id="4d38c-115">Todos os domínios de aplicativo no processo são interrompidos para este retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="4d38c-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d38c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d38c-116">Requirements</span></span>  

 <span data-ttu-id="4d38c-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d38c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d38c-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d38c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d38c-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d38c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d38c-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d38c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d38c-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="4d38c-121">See also</span></span>

- [<span data-ttu-id="4d38c-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="4d38c-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
