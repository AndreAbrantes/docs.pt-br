---
title: Método ICorDebugHandleValue::GetHandleType
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
ms.openlocfilehash: 6eb76ddd6ee8b2a00aac3af9ebf815338d29f194
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212159"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="d8582-102">Método ICorDebugHandleValue::GetHandleType</span><span class="sxs-lookup"><span data-stu-id="d8582-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="d8582-103">Obtém um valor que indica o tipo de identificador referenciado por este objeto ICorDebugHandleValue.</span><span class="sxs-lookup"><span data-stu-id="d8582-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8582-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8582-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8582-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8582-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="d8582-106">fora Um ponteiro para um valor da Enumeração CorDebugHandleType que indica o tipo desse identificador.</span><span class="sxs-lookup"><span data-stu-id="d8582-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8582-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8582-107">Requirements</span></span>  
 <span data-ttu-id="d8582-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8582-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8582-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8582-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8582-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8582-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8582-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8582-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
