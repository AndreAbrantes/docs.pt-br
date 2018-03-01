---
title: "Método ICorDebugCode::GetCode"
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
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f906fddf8073a00d2a3741613aae537b8604af67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="b6537-102">Método ICorDebugCode::GetCode</span><span class="sxs-lookup"><span data-stu-id="b6537-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="b6537-103">Obtém a todo o código para a função especificada, formatada para a desmontagem.</span><span class="sxs-lookup"><span data-stu-id="b6537-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="b6537-104">Esse método foi preterido no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="b6537-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b6537-105">Use [Icordebugcode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b6537-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6537-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6537-106">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6537-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b6537-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="b6537-108">[in] O deslocamento do início da função.</span><span class="sxs-lookup"><span data-stu-id="b6537-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="b6537-109">[in] O deslocamento do final da função.</span><span class="sxs-lookup"><span data-stu-id="b6537-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="b6537-110">[in] O tamanho do `buffer` matriz na qual o código será retornado.</span><span class="sxs-lookup"><span data-stu-id="b6537-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b6537-111">[out] A matriz na qual o código será retornado.</span><span class="sxs-lookup"><span data-stu-id="b6537-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="b6537-112">[out] O número de bytes retornados.</span><span class="sxs-lookup"><span data-stu-id="b6537-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6537-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6537-113">Remarks</span></span>  
 <span data-ttu-id="b6537-114">Se o código da função foi dividido em várias partes, eles são concatenados em ordem crescente de deslocamento nativo.</span><span class="sxs-lookup"><span data-stu-id="b6537-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="b6537-115">Limites de instrução não são verificados.</span><span class="sxs-lookup"><span data-stu-id="b6537-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6537-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6537-116">Requirements</span></span>  
 <span data-ttu-id="b6537-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6537-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6537-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6537-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6537-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6537-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6537-120">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="b6537-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6537-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6537-121">See Also</span></span>  
 [<span data-ttu-id="b6537-122">Método GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="b6537-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
