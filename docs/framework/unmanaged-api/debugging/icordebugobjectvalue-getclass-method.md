---
title: "Método ICorDebugObjectValue::GetClass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dee9f110647230e54df527959651dc5b2fb73b3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="aca03-102">Método ICorDebugObjectValue::GetClass</span><span class="sxs-lookup"><span data-stu-id="aca03-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="aca03-103">Obtém a classe de valor desse objeto.</span><span class="sxs-lookup"><span data-stu-id="aca03-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca03-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aca03-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aca03-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aca03-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="aca03-106">[out] Um ponteiro para o endereço de um objeto de "ICorDebugClass" que representa a classe do valor do objeto representado pelo objeto "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="aca03-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aca03-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="aca03-107">Remarks</span></span>  
 <span data-ttu-id="aca03-108">O `GetClass` e [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) métodos retornam informações sobre o tipo de um valor; elas são substituídas pelas com reconhecimento de genéricos [Icordebugvalue2](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="aca03-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca03-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aca03-109">Requirements</span></span>  
 <span data-ttu-id="aca03-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aca03-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca03-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aca03-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aca03-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aca03-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aca03-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca03-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca03-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aca03-114">See Also</span></span>  
    
 
