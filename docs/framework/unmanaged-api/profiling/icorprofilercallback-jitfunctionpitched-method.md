---
title: Método ICorProfilerCallback::JITFunctionPitched
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 51fec26837b3c7f0a0328a7b64ff4a02148283da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725502"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="4fd6a-102">Método ICorProfilerCallback::JITFunctionPitched</span><span class="sxs-lookup"><span data-stu-id="4fd6a-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>

<span data-ttu-id="4fd6a-103">Notifica o criador de perfil de que uma função que foi compilada JIT (just-in-time) foi removida da memória.</span><span class="sxs-lookup"><span data-stu-id="4fd6a-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fd6a-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fd6a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4fd6a-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="4fd6a-106">no A ID da função que foi removida.</span><span class="sxs-lookup"><span data-stu-id="4fd6a-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fd6a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fd6a-107">Remarks</span></span>  

 <span data-ttu-id="4fd6a-108">Se a função removida for chamada, o criador de perfil receberá novos eventos de compilação JIT quando a função for recompilada.</span><span class="sxs-lookup"><span data-stu-id="4fd6a-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="4fd6a-109">Atualmente, o compilador JIT do Common Language Runtime (CLR) não remove funções da memória, portanto, esse retorno de chamada não é usado no momento e não será recebido pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="4fd6a-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="4fd6a-110">O valor de `functionId` não é válido até que a função seja recompilada.</span><span class="sxs-lookup"><span data-stu-id="4fd6a-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="4fd6a-111">Quando a função for recompilada, o mesmo `functionId` valor será usado.</span><span class="sxs-lookup"><span data-stu-id="4fd6a-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fd6a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4fd6a-112">Requirements</span></span>  

 <span data-ttu-id="4fd6a-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fd6a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fd6a-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4fd6a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fd6a-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fd6a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fd6a-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fd6a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd6a-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="4fd6a-117">See also</span></span>

- [<span data-ttu-id="4fd6a-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4fd6a-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
