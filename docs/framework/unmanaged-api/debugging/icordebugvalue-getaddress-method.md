---
title: Método ICorDebugValue::GetAddress
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 47c0c4dfa78e85bcc83f0bb2a333955c8e8666fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728362"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="c6779-102">Método ICorDebugValue::GetAddress</span><span class="sxs-lookup"><span data-stu-id="c6779-102">ICorDebugValue::GetAddress Method</span></span>

<span data-ttu-id="c6779-103">Obtém o endereço desse objeto "ICorDebugValue", que está no processo de ser depurado.</span><span class="sxs-lookup"><span data-stu-id="c6779-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6779-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6779-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6779-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6779-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="c6779-106">fora Ponteiro para um `CORDB_ADDRESS` objeto que especifica o endereço desse objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="c6779-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6779-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6779-107">Remarks</span></span>  

 <span data-ttu-id="c6779-108">Se o valor não estiver disponível, será retornado 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="c6779-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="c6779-109">Isso pode acontecer se o valor for pelo menos parcialmente em registros ou armazenado em um identificador de coletor de lixo ( `GCHandle` ).</span><span class="sxs-lookup"><span data-stu-id="c6779-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6779-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6779-110">Requirements</span></span>  

 <span data-ttu-id="c6779-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6779-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6779-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6779-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6779-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6779-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6779-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6779-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6779-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="c6779-115">See also</span></span>
