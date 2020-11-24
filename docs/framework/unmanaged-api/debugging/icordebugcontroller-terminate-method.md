---
title: Método ICorDebugController::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: 460aeeca9d62ce91a11a24d774c8e681ed4f00ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679800"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="e90be-102">Método ICorDebugController::Terminate</span><span class="sxs-lookup"><span data-stu-id="e90be-102">ICorDebugController::Terminate Method</span></span>

<span data-ttu-id="e90be-103">Encerra o processo com o código de saída especificado.</span><span class="sxs-lookup"><span data-stu-id="e90be-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e90be-104">Esse método é um wrapper para a função do Win32 `TerminateProcess` .</span><span class="sxs-lookup"><span data-stu-id="e90be-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="e90be-105">Portanto, o `Terminate` usa o código de saída da mesma maneira que a função do Win32 o `TerminateProcess` utiliza.</span><span class="sxs-lookup"><span data-stu-id="e90be-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e90be-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e90be-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e90be-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e90be-107">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="e90be-108">no Um valor numérico que é o código de saída.</span><span class="sxs-lookup"><span data-stu-id="e90be-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="e90be-109">Os valores numéricos válidos são definidos em Winbase. h.</span><span class="sxs-lookup"><span data-stu-id="e90be-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e90be-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e90be-110">Remarks</span></span>  

 <span data-ttu-id="e90be-111">Se o processo for interrompido quando `Terminate` for chamado, o processo deverá continuar usando o método [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) para que o depurador receba a confirmação do encerramento por meio do retorno de chamada [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) ou [ICorDebugManagedCallback:: ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e90be-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e90be-112">Esse método não é implementado por um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e90be-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="e90be-113">Ou seja, ele não é implementado no <xref:System.AppDomain> nível.</span><span class="sxs-lookup"><span data-stu-id="e90be-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e90be-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e90be-114">Requirements</span></span>  

 <span data-ttu-id="e90be-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e90be-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e90be-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e90be-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e90be-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e90be-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e90be-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e90be-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90be-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="e90be-119">See also</span></span>
