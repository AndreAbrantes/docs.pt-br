---
title: "Método ICorDebugCode::GetAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38524f806b5e1669dbeb58d4fdf3a586d19c7bd7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="d8ae7-102">Método ICorDebugCode::GetAddress</span><span class="sxs-lookup"><span data-stu-id="d8ae7-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="d8ae7-103">Obtém o endereço virtual relativo (RVA) do segmento de código que representa essa interface "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="d8ae7-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ae7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8ae7-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8ae7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8ae7-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="d8ae7-106">[out] Um ponteiro para o RVA do segmento de código.</span><span class="sxs-lookup"><span data-stu-id="d8ae7-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ae7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8ae7-107">Requirements</span></span>  
 <span data-ttu-id="d8ae7-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ae7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ae7-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8ae7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ae7-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ae7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ae7-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ae7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ae7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8ae7-112">See Also</span></span>  
 
