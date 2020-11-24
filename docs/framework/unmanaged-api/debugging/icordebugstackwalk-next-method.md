---
title: Método ICorDebugStackWalk::Next
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: 497dda473e6510cfa31405b2066c63b1a70dd5e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677317"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="7b546-102">Método ICorDebugStackWalk::Next</span><span class="sxs-lookup"><span data-stu-id="7b546-102">ICorDebugStackWalk::Next Method</span></span>

<span data-ttu-id="7b546-103">Move o objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o próximo quadro.</span><span class="sxs-lookup"><span data-stu-id="7b546-103">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b546-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b546-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7b546-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7b546-105">Return Value</span></span>  

 <span data-ttu-id="7b546-106">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="7b546-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7b546-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b546-107">HRESULT</span></span>|<span data-ttu-id="7b546-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b546-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b546-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b546-109">S_OK</span></span>|<span data-ttu-id="7b546-110">O tempo de execução rebobinado com êxito para o próximo quadro (consulte comentários).</span><span class="sxs-lookup"><span data-stu-id="7b546-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="7b546-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b546-111">E_FAIL</span></span>|<span data-ttu-id="7b546-112">O `ICorDebugStackWalk` objeto não pôde ser avançado.</span><span class="sxs-lookup"><span data-stu-id="7b546-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="7b546-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="7b546-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="7b546-114">O fim da pilha foi atingido como resultado desse desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="7b546-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="7b546-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="7b546-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="7b546-116">O ponteiro de quadro já está no final da pilha; Portanto, nenhum quadro adicional pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="7b546-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="7b546-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="7b546-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b546-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b546-118">Remarks</span></span>  

 <span data-ttu-id="7b546-119">O `Next` método avança o `ICorDebugStackWalk` objeto para o quadro de chamada somente se o tempo de execução puder desenrolar o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="7b546-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="7b546-120">Caso contrário, o objeto avança para o próximo quadro que o tempo de execução é capaz de desenrolar.</span><span class="sxs-lookup"><span data-stu-id="7b546-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b546-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b546-121">Requirements</span></span>  

 <span data-ttu-id="7b546-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b546-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b546-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b546-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b546-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b546-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b546-125">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b546-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b546-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b546-126">See also</span></span>

- [<span data-ttu-id="7b546-127">Interface ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="7b546-127">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="7b546-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7b546-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7b546-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="7b546-129">Debugging</span></span>](index.md)
