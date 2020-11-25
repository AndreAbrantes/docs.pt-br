---
title: Método ICorProfilerCallback::ObjectsAllocatedByClass
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 70d43d7526376c40d0f8358ebd65e4a00a41b969
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701660"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="7bc68-102">Método ICorProfilerCallback::ObjectsAllocatedByClass</span><span class="sxs-lookup"><span data-stu-id="7bc68-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>

<span data-ttu-id="7bc68-103">Notifica o criador de perfil sobre o número de instâncias de cada classe especificada que foram criadas desde a coleta de lixo mais recente.</span><span class="sxs-lookup"><span data-stu-id="7bc68-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bc68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bc68-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bc68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bc68-105">Parameters</span></span>  

 `cClassCount`  
 <span data-ttu-id="7bc68-106">no O tamanho das `classIds` `cObjects` matrizes e.</span><span class="sxs-lookup"><span data-stu-id="7bc68-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="7bc68-107">no Uma matriz de IDs de classe, em que cada ID especifica uma classe com uma ou mais instâncias.</span><span class="sxs-lookup"><span data-stu-id="7bc68-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="7bc68-108">no Uma matriz de inteiros, em que cada inteiro especifica o número de instâncias para a classe correspondente na `classIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="7bc68-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bc68-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bc68-109">Remarks</span></span>  

 <span data-ttu-id="7bc68-110">As `classIds` `cObjects` matrizes e são matrizes paralelas.</span><span class="sxs-lookup"><span data-stu-id="7bc68-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="7bc68-111">Por exemplo, `classIds[i]` e `cObjects[i]` referenciar a mesma classe.</span><span class="sxs-lookup"><span data-stu-id="7bc68-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="7bc68-112">Se nenhuma instância de uma classe tiver sido criada desde a coleta de lixo anterior, a classe será omitida.</span><span class="sxs-lookup"><span data-stu-id="7bc68-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="7bc68-113">O `ObjectsAllocatedByClass` retorno de chamada não relatará objetos alocados na heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="7bc68-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="7bc68-114">Os números relatados por `ObjectsAllocatedByClass` são apenas estimativas.</span><span class="sxs-lookup"><span data-stu-id="7bc68-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="7bc68-115">Para contagens exatas, use [ICorProfilerCallback:: ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="7bc68-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="7bc68-116">A `classIds` matriz pode conter uma ou mais entradas nulas se a `cObjects` matriz correspondente tiver tipos que estão descarregando.</span><span class="sxs-lookup"><span data-stu-id="7bc68-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bc68-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bc68-117">Requirements</span></span>  

 <span data-ttu-id="7bc68-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bc68-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bc68-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7bc68-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7bc68-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bc68-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bc68-121">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bc68-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bc68-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7bc68-122">See also</span></span>

- [<span data-ttu-id="7bc68-123">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7bc68-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
