---
title: Método ICorProfilerCallback::ClassUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 114d5d58d0d9098944299aefd0cb99a70c5da09d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700256"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="422f9-102">Método ICorProfilerCallback::ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="422f9-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>

<span data-ttu-id="422f9-103">Notifica o criador de perfil de que uma classe concluiu o descarregamento.</span><span class="sxs-lookup"><span data-stu-id="422f9-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="422f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="422f9-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="422f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="422f9-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="422f9-106">\[in] identifica a classe que foi descarregada.</span><span class="sxs-lookup"><span data-stu-id="422f9-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="422f9-107">\[in] um HRESULT que indica se a classe foi descarregada com êxito.</span><span class="sxs-lookup"><span data-stu-id="422f9-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="422f9-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="422f9-108">Remarks</span></span>  

 <span data-ttu-id="422f9-109">Algumas partes do descarregamento da classe podem continuar após o `ClassUnloadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="422f9-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="422f9-110">Um HRESULT de falha em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="422f9-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="422f9-111">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do descarregamento da classe foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="422f9-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="422f9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="422f9-112">Requirements</span></span>  

 <span data-ttu-id="422f9-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="422f9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="422f9-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="422f9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="422f9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="422f9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="422f9-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="422f9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="422f9-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="422f9-117">See also</span></span>

- [<span data-ttu-id="422f9-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="422f9-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="422f9-119">Método ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="422f9-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
