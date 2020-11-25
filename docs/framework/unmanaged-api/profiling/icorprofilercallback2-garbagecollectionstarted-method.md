---
title: Método ICorProfilerCallback2::GarbageCollectionStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
ms.openlocfilehash: 63a8d212a61bd73f44995f0e057eeff96f9a5554
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731937"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="b9c3a-102">Método ICorProfilerCallback2::GarbageCollectionStarted</span><span class="sxs-lookup"><span data-stu-id="b9c3a-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>

<span data-ttu-id="b9c3a-103">Notifica o criador de perfil de código que a coleta de lixo foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="b9c3a-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9c3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9c3a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9c3a-105">Parameters</span></span>  

 `cGenerations`  
 <span data-ttu-id="b9c3a-106">no O número total de entradas na `generationCollected` matriz.</span><span class="sxs-lookup"><span data-stu-id="b9c3a-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="b9c3a-107">no Uma matriz de valores Boolianos, que `true` se a geração que corresponde ao índice de matriz está sendo coletada por essa coleta de lixo; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="b9c3a-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="b9c3a-108">A matriz é indexada por um valor da enumeração [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , que indica a geração.</span><span class="sxs-lookup"><span data-stu-id="b9c3a-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="b9c3a-109">no Um valor da enumeração [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) que indica o motivo pelo qual a coleta de lixo foi induzida.</span><span class="sxs-lookup"><span data-stu-id="b9c3a-109">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9c3a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9c3a-110">Remarks</span></span>  

 <span data-ttu-id="b9c3a-111">Todos os retornos de chamada que pertencem a essa coleta de lixo ocorrerão entre o `GarbageCollectionStarted` retorno de chamada e o retorno de chamada [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) correspondente.</span><span class="sxs-lookup"><span data-stu-id="b9c3a-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="b9c3a-112">Esses retornos de chamada não precisam ocorrer no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="b9c3a-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="b9c3a-113">É seguro que o criador de perfil Inspecione objetos em seus locais originais durante o `GarbageCollectionStarted` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b9c3a-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="b9c3a-114">O coletor de lixo começará a mover objetos após o retorno de `GarbageCollectionStarted` .</span><span class="sxs-lookup"><span data-stu-id="b9c3a-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="b9c3a-115">Depois que o criador de perfil for retornado desse retorno de chamada, o criador de perfil deverá considerar que todas as IDs de objeto sejam inválidas até receber um `ICorProfilerCallback2::GarbageCollectionFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b9c3a-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9c3a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9c3a-116">Requirements</span></span>  

 <span data-ttu-id="b9c3a-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9c3a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9c3a-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b9c3a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9c3a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9c3a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9c3a-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9c3a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c3a-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="b9c3a-121">See also</span></span>

- [<span data-ttu-id="b9c3a-122">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b9c3a-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b9c3a-123">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="b9c3a-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
