---
title: Método ICorDebugStackWalk::GetContext
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 927f2077b4bb71177c24816774d06643ebdaa922
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711956"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="90f5d-102">Método ICorDebugStackWalk::GetContext</span><span class="sxs-lookup"><span data-stu-id="90f5d-102">ICorDebugStackWalk::GetContext Method</span></span>

<span data-ttu-id="90f5d-103">Retorna o contexto para o quadro atual no objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="90f5d-103">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90f5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90f5d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90f5d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90f5d-105">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="90f5d-106">no Sinalizadores que indicam o conteúdo solicitado do buffer de contexto (definido em WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="90f5d-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="90f5d-107">no O tamanho alocado do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="90f5d-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="90f5d-108">fora O tamanho real do contexto.</span><span class="sxs-lookup"><span data-stu-id="90f5d-108">[out] The actual size of the context.</span></span> <span data-ttu-id="90f5d-109">Esse valor deve ser menor ou igual ao tamanho do buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="90f5d-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="90f5d-110">fora O buffer de contexto.</span><span class="sxs-lookup"><span data-stu-id="90f5d-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90f5d-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="90f5d-111">Return Value</span></span>  

 <span data-ttu-id="90f5d-112">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="90f5d-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90f5d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90f5d-113">HRESULT</span></span>|<span data-ttu-id="90f5d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="90f5d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90f5d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="90f5d-115">S_OK</span></span>|<span data-ttu-id="90f5d-116">O contexto do quadro atual foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="90f5d-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="90f5d-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="90f5d-117">E_FAIL</span></span>|<span data-ttu-id="90f5d-118">Não foi possível retornar o contexto.</span><span class="sxs-lookup"><span data-stu-id="90f5d-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="90f5d-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="90f5d-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="90f5d-120">O buffer de contexto é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="90f5d-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="90f5d-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="90f5d-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="90f5d-122">O ponteiro de quadro já está no final da pilha; Portanto, nenhum quadro adicional pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="90f5d-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="90f5d-123">Exceções</span><span class="sxs-lookup"><span data-stu-id="90f5d-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90f5d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="90f5d-124">Remarks</span></span>  

 <span data-ttu-id="90f5d-125">Como o desenrolamento restaura apenas um subconjunto dos registros, como registros não-voláteis, o contexto pode não corresponder exatamente ao estado de registro no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="90f5d-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90f5d-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90f5d-126">Requirements</span></span>  

 <span data-ttu-id="90f5d-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90f5d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90f5d-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90f5d-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90f5d-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90f5d-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90f5d-130">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90f5d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f5d-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="90f5d-131">See also</span></span>

- [<span data-ttu-id="90f5d-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="90f5d-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="90f5d-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="90f5d-133">Debugging</span></span>](index.md)
