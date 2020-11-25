---
title: Método ICorDebugILFrame2::RemapFunction
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
ms.openlocfilehash: 5eb6299526d69624056961cfb7f0387ff8f873cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725021"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="0d480-102">Método ICorDebugILFrame2::RemapFunction</span><span class="sxs-lookup"><span data-stu-id="0d480-102">ICorDebugILFrame2::RemapFunction Method</span></span>

<span data-ttu-id="0d480-103">Remapeia uma função editada especificando o novo deslocamento da MSIL (Microsoft Intermediate Language)</span><span class="sxs-lookup"><span data-stu-id="0d480-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d480-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d480-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d480-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d480-105">Parameters</span></span>  

 `newILOffset`  
 <span data-ttu-id="0d480-106">no O novo deslocamento MSIL do quadro de pilha no qual o ponteiro de instrução deve ser colocado.</span><span class="sxs-lookup"><span data-stu-id="0d480-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="0d480-107">Esse valor deve ser um ponto de sequência.</span><span class="sxs-lookup"><span data-stu-id="0d480-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="0d480-108">É responsabilidade do chamador garantir a validade desse valor.</span><span class="sxs-lookup"><span data-stu-id="0d480-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="0d480-109">Por exemplo, o deslocamento de MSIL não será válido se estiver fora dos limites da função.</span><span class="sxs-lookup"><span data-stu-id="0d480-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d480-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d480-110">Remarks</span></span>  

 <span data-ttu-id="0d480-111">Quando a função de um quadro é editada, o depurador pode chamar o `RemapFunction` método para alternar a versão mais recente da função do quadro para que possa ser executado.</span><span class="sxs-lookup"><span data-stu-id="0d480-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="0d480-112">A execução do código será iniciada no deslocamento de MSIL fornecido.</span><span class="sxs-lookup"><span data-stu-id="0d480-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d480-113">Chamar `RemapFunction` , como chamar [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md), invalidará imediatamente todas as interfaces de depuração relacionadas à geração de um rastreamento de pilha para o thread.</span><span class="sxs-lookup"><span data-stu-id="0d480-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="0d480-114">Essas interfaces incluem [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame e ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="0d480-114">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="0d480-115">O `RemapFunction` método pode ser chamado somente no contexto do quadro atual e apenas em um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="0d480-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="0d480-116">Após o recebimento de um retorno de chamada [ICorDebugManagedCallback2:: FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) que ainda não foi continuado.</span><span class="sxs-lookup"><span data-stu-id="0d480-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="0d480-117">Enquanto a execução do código é interrompida devido a um evento [ICorDebugManagedCallback:: EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) para esse quadro.</span><span class="sxs-lookup"><span data-stu-id="0d480-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d480-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d480-118">Requirements</span></span>  

 <span data-ttu-id="0d480-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d480-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d480-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d480-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d480-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d480-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d480-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d480-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
