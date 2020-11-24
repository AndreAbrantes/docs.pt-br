---
title: Método ICorProfilerInfo::ForceGC
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 75f2db5e5489f02dcae3db0c3e6af19c922e0745
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669186"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="4a7e1-102">Método ICorProfilerInfo::ForceGC</span><span class="sxs-lookup"><span data-stu-id="4a7e1-102">ICorProfilerInfo::ForceGC Method</span></span>

<span data-ttu-id="4a7e1-103">Força a coleta de lixo a ocorrer dentro do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4a7e1-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a7e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a7e1-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4a7e1-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a7e1-105">Remarks</span></span>  

 <span data-ttu-id="4a7e1-106">O `ForceGC` método deve ser chamado somente de um thread que nunca tenha executado código gerenciado e não tenha nenhum retorno de chamada do criador de perfil em sua pilha.</span><span class="sxs-lookup"><span data-stu-id="4a7e1-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="4a7e1-107">A implementação mais conveniente é criar um thread separado dentro do criador de perfil que chama `ForceGC` quando sinalizado.</span><span class="sxs-lookup"><span data-stu-id="4a7e1-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a7e1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a7e1-108">Requirements</span></span>  

 <span data-ttu-id="4a7e1-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a7e1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a7e1-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4a7e1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a7e1-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a7e1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a7e1-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a7e1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7e1-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="4a7e1-113">See also</span></span>

- [<span data-ttu-id="4a7e1-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="4a7e1-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
