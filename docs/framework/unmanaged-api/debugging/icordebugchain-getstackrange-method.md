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
ms.openlocfilehash: 64e697323377d664b7b1e36bbf5931a44465cc51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178953"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="b140b-102">Método ICorDebugChain::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="b140b-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="b140b-103">Obtém o intervalo de endereços do segmento stack para esta cadeia.</span><span class="sxs-lookup"><span data-stu-id="b140b-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b140b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b140b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b140b-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b140b-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="b140b-106">[fora] Um ponteiro `CORDB_ADDRESS` para um valor que é o endereço inicial do segmento stack.</span><span class="sxs-lookup"><span data-stu-id="b140b-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="b140b-107">[fora] Um ponteiro `CORDB_ADDRESS` para um valor que é o endereço final do segmento stack.</span><span class="sxs-lookup"><span data-stu-id="b140b-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b140b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b140b-108">Remarks</span></span>  
 <span data-ttu-id="b140b-109">O intervalo numérico é significativo apenas para comparação de locais de quadro sumário.</span><span class="sxs-lookup"><span data-stu-id="b140b-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="b140b-110">Você não pode fazer nenhuma suposição sobre o que é realmente armazenado na pilha.</span><span class="sxs-lookup"><span data-stu-id="b140b-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b140b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b140b-111">Requirements</span></span>  
 <span data-ttu-id="b140b-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b140b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b140b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b140b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b140b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b140b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b140b-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b140b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
