---
title: Método ICorDebugManagedCallback::DebuggerError
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: eb95bf779e54742cd2cc4b688c24a49e6d85a40d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731898"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="b1da8-102">Método ICorDebugManagedCallback::DebuggerError</span><span class="sxs-lookup"><span data-stu-id="b1da8-102">ICorDebugManagedCallback::DebuggerError Method</span></span>

<span data-ttu-id="b1da8-103">Notifica o depurador de que ocorreu um erro ao tentar lidar com um evento do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b1da8-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1da8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1da8-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1da8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1da8-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="b1da8-106">no Um ponteiro para um objeto "ICorDebugProcess" que representa o processo no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="b1da8-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="b1da8-107">no O valor HRESULT que foi retornado do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b1da8-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="b1da8-108">no Um inteiro que especifica o erro CLR.</span><span class="sxs-lookup"><span data-stu-id="b1da8-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1da8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1da8-109">Remarks</span></span>  

 <span data-ttu-id="b1da8-110">O processo pode ser colocado em modo de passagem, dependendo da natureza do erro.</span><span class="sxs-lookup"><span data-stu-id="b1da8-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="b1da8-111">O `DebugError` retorno de chamada indica que os serviços de depuração foram desabilitados devido a um erro, portanto, os depuradores devem tornar a mensagem de erro disponível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b1da8-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="b1da8-112">[ICorDebugProcess:: GetID](icordebugprocess-getid-method.md) será seguro chamar, mas todos os outros métodos, incluindo [ICorDebug:: Terminate](icordebug-terminate-method.md), não devem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="b1da8-112">[ICorDebugProcess::GetID](icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="b1da8-113">O depurador deve usar recursos do sistema operacional para encerrar processos.</span><span class="sxs-lookup"><span data-stu-id="b1da8-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1da8-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1da8-114">Requirements</span></span>  

 <span data-ttu-id="b1da8-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1da8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1da8-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1da8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1da8-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1da8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1da8-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1da8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1da8-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="b1da8-119">See also</span></span>

- [<span data-ttu-id="b1da8-120">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b1da8-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
