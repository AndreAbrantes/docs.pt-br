---
title: Método ICorDebugRegisterSet::GetRegistersAvailable
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
ms.openlocfilehash: d28c130e55cbebf29348752780c03b03c1b8f358
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716987"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="c55e9-102">Método ICorDebugRegisterSet::GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="c55e9-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>

<span data-ttu-id="c55e9-103">Obtém uma máscara de bits que indica quais registros neste [ICorDebugRegisterSet](icordebugregisterset-interface.md) estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="c55e9-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c55e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c55e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c55e9-105">Parameters</span></span>  

 `pAvailable`  
 <span data-ttu-id="c55e9-106">fora Uma máscara de bits que indica quais registros estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="c55e9-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c55e9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c55e9-107">Remarks</span></span>  

 <span data-ttu-id="c55e9-108">Um registro pode não estar disponível se seu valor não puder ser determinado para a situação especificada.</span><span class="sxs-lookup"><span data-stu-id="c55e9-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="c55e9-109">A máscara retornada contém um bit para cada registro (1 << o índice de registro).</span><span class="sxs-lookup"><span data-stu-id="c55e9-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="c55e9-110">O valor de bit será 1 se o registro estiver disponível ou 0 se não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="c55e9-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c55e9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c55e9-111">Requirements</span></span>  

 <span data-ttu-id="c55e9-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c55e9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c55e9-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c55e9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c55e9-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c55e9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c55e9-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c55e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55e9-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="c55e9-116">See also</span></span>

- [<span data-ttu-id="c55e9-117">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="c55e9-117">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="c55e9-118">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="c55e9-118">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
