---
title: "Método ICorDebugArrayValue::GetElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetElement
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5fc9671365a866c04671bca965ed43d83533f07f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="a0f46-102">Método ICorDebugArrayValue::GetElement</span><span class="sxs-lookup"><span data-stu-id="a0f46-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="a0f46-103">Obtém o valor do elemento da matriz determinado.</span><span class="sxs-lookup"><span data-stu-id="a0f46-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0f46-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0f46-104">Syntax</span></span>  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0f46-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0f46-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="a0f46-106">[in] O número de dimensões deste `ICorDebugArrayValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="a0f46-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="a0f46-107">Esse valor também é o tamanho do `indices` porque seu tamanho é igual ao número de dimensões do `ICorDebugArrayValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="a0f46-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="a0f46-108">[in] Uma matriz de valores de índice, cada uma delas Especifica uma posição dentro de uma dimensão do `ICorDebugArrayValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="a0f46-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="a0f46-109">Esse valor não deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="a0f46-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a0f46-110">[out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="a0f46-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0f46-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0f46-111">Requirements</span></span>  
 <span data-ttu-id="a0f46-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0f46-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0f46-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0f46-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0f46-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0f46-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0f46-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0f46-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
