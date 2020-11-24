---
title: Método ICorProfilerCallback::ObjectAllocated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: fda234a6a280aeea1f497ad195d6d41efb6aa951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674312"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="9e07d-102">Método ICorProfilerCallback::ObjectAllocated</span><span class="sxs-lookup"><span data-stu-id="9e07d-102">ICorProfilerCallback::ObjectAllocated Method</span></span>

<span data-ttu-id="9e07d-103">Notifica o criador de perfil de que a memória dentro do heap foi alocada para um objeto.</span><span class="sxs-lookup"><span data-stu-id="9e07d-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e07d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e07d-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e07d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e07d-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="9e07d-106">no A ID do objeto para o qual a memória foi alocada.</span><span class="sxs-lookup"><span data-stu-id="9e07d-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="9e07d-107">no A ID da classe da qual o objeto é uma instância.</span><span class="sxs-lookup"><span data-stu-id="9e07d-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e07d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e07d-108">Remarks</span></span>  

 <span data-ttu-id="9e07d-109">O `ObjectedAllocated` método não é chamado para alocações a partir da pilha ou da memória não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="9e07d-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="9e07d-110">O `classId` parâmetro pode se referir a uma classe no código gerenciado que ainda não foi carregado.</span><span class="sxs-lookup"><span data-stu-id="9e07d-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="9e07d-111">O criador de perfil receberá um retorno de chamada de carga de classe para essa classe imediatamente após o `ObjectAllocated` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="9e07d-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e07d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e07d-112">Requirements</span></span>  

 <span data-ttu-id="9e07d-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e07d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e07d-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9e07d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e07d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e07d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e07d-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e07d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e07d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e07d-117">See also</span></span>

- [<span data-ttu-id="9e07d-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9e07d-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9e07d-119">Método ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="9e07d-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="9e07d-120">Método ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="9e07d-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
