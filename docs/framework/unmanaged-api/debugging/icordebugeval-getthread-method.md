---
title: "Método ICorDebugEval::GetThread"
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
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a2ed99c2a939d2b39f6b236165b79634f2fc2c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="f6591-102">Método ICorDebugEval::GetThread</span><span class="sxs-lookup"><span data-stu-id="f6591-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="f6591-103">Obtém o thread em que essa avaliação está em execução ou será executado.</span><span class="sxs-lookup"><span data-stu-id="f6591-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6591-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6591-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6591-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6591-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="f6591-106">[out] Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread.</span><span class="sxs-lookup"><span data-stu-id="f6591-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6591-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6591-107">Requirements</span></span>  
 <span data-ttu-id="f6591-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6591-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6591-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6591-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6591-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6591-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6591-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6591-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
