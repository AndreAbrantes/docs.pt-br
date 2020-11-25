---
title: Método ICorProfilerInfo4::InitializeCurrentThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 51f16523c00cc3dd95b786f1586ccfd75ce8d5f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733822"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="cd443-102">Método ICorProfilerInfo4::InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="cd443-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>

<span data-ttu-id="cd443-103">Inicializa o thread atual antes das chamadas de API do criador de perfil subsequentes no mesmo thread, para que o deadlock possa ser evitado.</span><span class="sxs-lookup"><span data-stu-id="cd443-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd443-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd443-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cd443-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd443-105">Remarks</span></span>  

 <span data-ttu-id="cd443-106">Recomendamos que você chame `InitializeCurrentThread` em qualquer thread que chamará uma API do profiler enquanto houver threads suspensos.</span><span class="sxs-lookup"><span data-stu-id="cd443-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="cd443-107">Esse método é normalmente usado por infilers de amostragem que criam seu próprio thread para chamar o método [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) para executar movimentações de pilha enquanto o thread-alvo é suspenso.</span><span class="sxs-lookup"><span data-stu-id="cd443-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="cd443-108">Chamando `InitializeCurrentThread` uma vez quando o criador de perfil cria primeiro o thread de amostragem, os profileres podem garantir a inicialização lenta por thread que o CLR executaria, de outra forma, durante a primeira chamada para `DoStackSnapshot` pode ocorrer com segurança quando nenhum outro thread for suspenso.</span><span class="sxs-lookup"><span data-stu-id="cd443-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd443-109">`InitializeCurrentThread` faz a inicialização com antecedência para concluir as tarefas que usam bloqueios e pode travar.</span><span class="sxs-lookup"><span data-stu-id="cd443-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="cd443-110">Chame `InitializeCurrentThread` somente quando não houver threads suspensos.</span><span class="sxs-lookup"><span data-stu-id="cd443-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd443-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd443-111">Requirements</span></span>  

 <span data-ttu-id="cd443-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd443-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd443-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cd443-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd443-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd443-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd443-115">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd443-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd443-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd443-116">See also</span></span>

- [<span data-ttu-id="cd443-117">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="cd443-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="cd443-118">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="cd443-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cd443-119">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="cd443-119">Profiling</span></span>](index.md)
