---
title: "Método ICorDebugDataTarget2::EnumerateThreadIDs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9030f7f8453de98f535cf8212e55c7daee94e8e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="691ce-102">Método ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="691ce-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="691ce-103">Retorna uma lista de IDs de thread ativo.</span><span class="sxs-lookup"><span data-stu-id="691ce-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="691ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="691ce-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="691ce-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="691ce-105">Parameters</span></span>  
 <span data-ttu-id="691ce-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="691ce-106">cThreadIDs</span></span>  
 <span data-ttu-id="691ce-107">[in] O número máximo de threads cujos IDs podem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="691ce-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="691ce-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="691ce-108">pcThreadIds</span></span>  
 <span data-ttu-id="691ce-109">[out] Um ponteiro para um `ULONG32` que indica o número real de IDs de thread gravadas na matriz `pThreadIds`.</span><span class="sxs-lookup"><span data-stu-id="691ce-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="691ce-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="691ce-110">pThreadIDs</span></span>  
 <span data-ttu-id="691ce-111">Uma matriz de identificadores de thread.</span><span class="sxs-lookup"><span data-stu-id="691ce-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="691ce-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="691ce-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="691ce-113">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="691ce-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="691ce-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="691ce-114">Requirements</span></span>  
 <span data-ttu-id="691ce-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md). **Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="691ce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="691ce-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="691ce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="691ce-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="691ce-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691ce-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="691ce-118">See Also</span></span>  
 [<span data-ttu-id="691ce-119">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="691ce-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="691ce-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="691ce-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
