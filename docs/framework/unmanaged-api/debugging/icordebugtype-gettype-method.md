---
title: Método ICorDebugType::GetType
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: f0f45d5f0b2ea8cefa6bd36e909ae43d80c968ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700880"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="4dd53-102">Método ICorDebugType::GetType</span><span class="sxs-lookup"><span data-stu-id="4dd53-102">ICorDebugType::GetType Method</span></span>

<span data-ttu-id="4dd53-103">Obtém um valor de CorElementType que descreve o tipo nativo do Common Language Runtime (CLR) <xref:System.Type> representado por esse ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="4dd53-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4dd53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dd53-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4dd53-105">Parameters</span></span>  

 `ty`  
 <span data-ttu-id="4dd53-106">fora Um ponteiro para um valor da `CorElementType` enumeração que indica o CLR <xref:System.Type> que isso `ICorDebugType` representa.</span><span class="sxs-lookup"><span data-stu-id="4dd53-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dd53-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4dd53-107">Remarks</span></span>  

 <span data-ttu-id="4dd53-108">Se o valor de `ty` for ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, o método [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) poderá ser chamado para obter o tipo não instanciado para um tipo genérico; caso contrário, não chame `ICorDebugType::GetClass` .</span><span class="sxs-lookup"><span data-stu-id="4dd53-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dd53-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4dd53-109">Requirements</span></span>  

 <span data-ttu-id="4dd53-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dd53-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dd53-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dd53-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dd53-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dd53-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dd53-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dd53-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
