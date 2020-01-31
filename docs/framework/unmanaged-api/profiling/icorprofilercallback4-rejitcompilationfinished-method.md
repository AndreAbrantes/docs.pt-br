---
title: Método ICorProfilerCallback4::ReJITCompilationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: e010a49dabd3b44602136e70b4c5524a68bdd9e2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865201"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="26ca6-102">Método ICorProfilerCallback4::ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="26ca6-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="26ca6-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) concluiu a recompilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="26ca6-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26ca6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26ca6-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26ca6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26ca6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="26ca6-106">no A ID da função que foi recompilada.</span><span class="sxs-lookup"><span data-stu-id="26ca6-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="26ca6-107">no A identidade da função de compilação JIT recompilada.</span><span class="sxs-lookup"><span data-stu-id="26ca6-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="26ca6-108">no Um valor que indica se a recompilação JIT foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="26ca6-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="26ca6-109">[in] `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; `false` para indicar que o bloqueio não afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="26ca6-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="26ca6-110">Um valor de `true` não danifica o tempo de execução, mas pode afetar os resultados da criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="26ca6-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26ca6-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="26ca6-111">Requirements</span></span>  
 <span data-ttu-id="26ca6-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26ca6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26ca6-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="26ca6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26ca6-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26ca6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26ca6-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26ca6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ca6-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="26ca6-116">See also</span></span>

- [<span data-ttu-id="26ca6-117">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="26ca6-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="26ca6-118">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="26ca6-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="26ca6-119">Método JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="26ca6-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="26ca6-120">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="26ca6-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
