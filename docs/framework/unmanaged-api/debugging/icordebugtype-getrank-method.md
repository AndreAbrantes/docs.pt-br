---
title: Método ICorDebugType::GetRank
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f112e0d064041a877963939b78029da08bbbed1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="d36fa-102">Método ICorDebugType::GetRank</span><span class="sxs-lookup"><span data-stu-id="d36fa-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="d36fa-103">Obtém o número de dimensões em um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="d36fa-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d36fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d36fa-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d36fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d36fa-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="d36fa-106">[out] Um ponteiro para o número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="d36fa-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d36fa-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d36fa-107">Requirements</span></span>  
 <span data-ttu-id="d36fa-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d36fa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d36fa-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d36fa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d36fa-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d36fa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d36fa-111">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d36fa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
