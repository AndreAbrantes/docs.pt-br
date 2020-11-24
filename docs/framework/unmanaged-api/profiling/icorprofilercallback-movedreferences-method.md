---
title: Método ICorProfilerCallback::MovedReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
ms.openlocfilehash: 4da09be6816174a1d4a131086d5e98b881c27b9c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680252"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="8167c-102">Método ICorProfilerCallback::MovedReferences</span><span class="sxs-lookup"><span data-stu-id="8167c-102">ICorProfilerCallback::MovedReferences Method</span></span>

<span data-ttu-id="8167c-103">Chamado para relatar o novo layout de objetos no heap como resultado de uma coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="8167c-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8167c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8167c-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8167c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8167c-105">Parameters</span></span>  

 `cMovedObjectIDRanges`  
 <span data-ttu-id="8167c-106">no O número de blocos de objetos contíguos que foram movidos como resultado da coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="8167c-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="8167c-107">Ou seja, o valor de `cMovedObjectIDRanges` é o tamanho total das `oldObjectIDRangeStart` `newObjectIDRangeStart` matrizes, e `cObjectIDRangeLength` .</span><span class="sxs-lookup"><span data-stu-id="8167c-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="8167c-108">Os próximos três argumentos de `MovedReferences` são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="8167c-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="8167c-109">Em outras palavras,,, `oldObjectIDRangeStart[i]` `newObjectIDRangeStart[i]` e `cObjectIDRangeLength[i]` todos se preocupam com um único bloco de objetos contíguos.</span><span class="sxs-lookup"><span data-stu-id="8167c-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="8167c-110">no Uma matriz de `ObjectID` valores, cada um dos quais é o endereço inicial (coleta antes de lixo) de um bloco de objetos dinâmicos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="8167c-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="8167c-111">no Uma matriz de `ObjectID` valores, cada um dos quais é o novo endereço inicial (coleta de lixo) de um bloco de objetos dinâmicos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="8167c-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="8167c-112">no Uma matriz de inteiros, cada qual é o tamanho de um bloco de objetos contíguos na memória.</span><span class="sxs-lookup"><span data-stu-id="8167c-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="8167c-113">Um tamanho é especificado para cada bloco que é referenciado nas `oldObjectIDRangeStart` `newObjectIDRangeStart` matrizes e.</span><span class="sxs-lookup"><span data-stu-id="8167c-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8167c-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="8167c-114">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8167c-115">Esse método relata tamanhos `MAX_ULONG` para objetos que são maiores que 4 GB em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8167c-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="8167c-116">Para obter o tamanho dos objetos com mais de 4 GB, use o método [ICorProfilerCallback4:: MovedReferences2](icorprofilercallback4-movedreferences2-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="8167c-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="8167c-117">Um coletor de lixo de compactação recupera a memória ocupada por objetos inativos e compacta o espaço livre.</span><span class="sxs-lookup"><span data-stu-id="8167c-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="8167c-118">Como resultado, os objetos dinâmicos podem ser movidos dentro do heap, e `ObjectID` os valores distribuídos pelas notificações anteriores podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="8167c-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="8167c-119">Suponha que um `ObjectID` valor existente ( `oldObjectID` ) está dentro do seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="8167c-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="8167c-120">Nesse caso, o deslocamento do início do intervalo até o início do objeto é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8167c-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="8167c-121">Para qualquer valor `i` que esteja no seguinte intervalo:</span><span class="sxs-lookup"><span data-stu-id="8167c-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="8167c-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="8167c-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="8167c-123">Você pode calcular o novo da `ObjectID` seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8167c-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="8167c-124">`newObjectID` = `newObjectIDRangeStart[i]` + ( `oldObjectID` – `oldObjectIDRangeStart[i]` )</span><span class="sxs-lookup"><span data-stu-id="8167c-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="8167c-125">Nenhum dos `ObjectID` valores passados por `MovedReferences` são válidos durante o próprio retorno de chamada, pois a coleta de lixo pode estar no meio da movimentação de objetos de locais antigos para novos locais.</span><span class="sxs-lookup"><span data-stu-id="8167c-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="8167c-126">Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `MovedReferences`.</span><span class="sxs-lookup"><span data-stu-id="8167c-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="8167c-127">Um retorno de chamada [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) indica que todos os objetos foram movidos para seus novos locais e a inspeção pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="8167c-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8167c-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8167c-128">Requirements</span></span>  

 <span data-ttu-id="8167c-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8167c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8167c-130">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8167c-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8167c-131">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8167c-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8167c-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8167c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8167c-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="8167c-133">See also</span></span>

- [<span data-ttu-id="8167c-134">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8167c-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8167c-135">Método MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="8167c-135">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="8167c-136">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="8167c-136">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8167c-137">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8167c-137">Profiling</span></span>](index.md)
