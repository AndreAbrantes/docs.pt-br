---
title: Método ICorProfilerInfo::GetEventMask
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
ms.openlocfilehash: 16bd8b09d5118171e669e9c428fb444384b5867d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722556"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="936fc-102">Método ICorProfilerInfo::GetEventMask</span><span class="sxs-lookup"><span data-stu-id="936fc-102">ICorProfilerInfo::GetEventMask Method</span></span>

<span data-ttu-id="936fc-103">Obtém as categorias de eventos atuais para as quais o criador de perfil deseja receber notificações de eventos para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="936fc-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="936fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="936fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="936fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="936fc-105">Parameters</span></span>  

 `pdwEvents`  
 <span data-ttu-id="936fc-106">[out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="936fc-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="936fc-107">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="936fc-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="936fc-108">Os bits são descritos na enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="936fc-108">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="936fc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="936fc-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="936fc-110">Você deve chamar o método [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) em vez desse método.</span><span class="sxs-lookup"><span data-stu-id="936fc-110">You should call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="936fc-111">Embora o `SetEventMask` método continue a ser suportado, o [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) fornece funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="936fc-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="936fc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="936fc-112">Requirements</span></span>  

 <span data-ttu-id="936fc-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="936fc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="936fc-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="936fc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="936fc-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="936fc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="936fc-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="936fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="936fc-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="936fc-117">See also</span></span>

- [<span data-ttu-id="936fc-118">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="936fc-118">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="936fc-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="936fc-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
