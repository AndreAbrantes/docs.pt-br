---
title: Método ICorDebugArrayValue::GetBaseIndicies
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: ea5c5a728afb9ac90f8599c833caab11fd0c65fe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731456"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="5a250-102">Método ICorDebugArrayValue::GetBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="5a250-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>

<span data-ttu-id="5a250-103">Obtém o índice base de cada dimensão na matriz.</span><span class="sxs-lookup"><span data-stu-id="5a250-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a250-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a250-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a250-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a250-105">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="5a250-106">no O número de dimensões deste `ICorDebugArrayValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="5a250-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="5a250-107">Esse valor também é o tamanho da `indicies` matriz porque seu tamanho é igual ao número de dimensões do `ICorDebugArrayValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="5a250-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="5a250-108">fora Uma matriz de inteiros, cada um dos quais é o índice base (ou seja, o índice inicial) de uma dimensão desse `ICorDebugArrayValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="5a250-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a250-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a250-109">Requirements</span></span>  

 <span data-ttu-id="5a250-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a250-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a250-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a250-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a250-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a250-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a250-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a250-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
