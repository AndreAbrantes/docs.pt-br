---
title: Método ICorDebugChain::GetStackRange
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 841e3ca608d20a4b8618508e69195de0b1da1341
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724384"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="f4b05-102">Método ICorDebugChain::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="f4b05-102">ICorDebugChain::GetStackRange Method</span></span>

<span data-ttu-id="f4b05-103">Obtém o intervalo de endereços do segmento da pilha para esta cadeia.</span><span class="sxs-lookup"><span data-stu-id="f4b05-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4b05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4b05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4b05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4b05-105">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="f4b05-106">fora Um ponteiro para um `CORDB_ADDRESS` valor que é o endereço inicial do segmento da pilha.</span><span class="sxs-lookup"><span data-stu-id="f4b05-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="f4b05-107">fora Um ponteiro para um `CORDB_ADDRESS` valor que é o endereço final do segmento da pilha.</span><span class="sxs-lookup"><span data-stu-id="f4b05-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4b05-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4b05-108">Remarks</span></span>  

 <span data-ttu-id="f4b05-109">O intervalo numérico é significativo apenas para comparação de locais de quadros de pilha.</span><span class="sxs-lookup"><span data-stu-id="f4b05-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="f4b05-110">Você não pode fazer suposições sobre o que realmente está armazenado na pilha.</span><span class="sxs-lookup"><span data-stu-id="f4b05-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4b05-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4b05-111">Requirements</span></span>  

 <span data-ttu-id="f4b05-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4b05-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4b05-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4b05-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4b05-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4b05-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4b05-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4b05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
