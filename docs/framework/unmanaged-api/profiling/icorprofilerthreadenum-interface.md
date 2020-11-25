---
title: Interface ICorProfilerThreadEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: 147694431d2c378b856577ef5a60e8a8b4e9a7a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721212"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="46df4-102">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="46df4-102">ICorProfilerThreadEnum Interface</span></span>

<span data-ttu-id="46df4-103">Fornece métodos para iterar em sequência por meio de uma coleção de threads no Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="46df4-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46df4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="46df4-104">Methods</span></span>  
  
|<span data-ttu-id="46df4-105">Método</span><span class="sxs-lookup"><span data-stu-id="46df4-105">Method</span></span>|<span data-ttu-id="46df4-106">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="46df4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46df4-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="46df4-107">Clone Method</span></span>](icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="46df4-108">Obtém um ponteiro de interface para uma cópia desta `ICorProfilerThreadEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="46df4-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="46df4-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="46df4-109">GetCount Method</span></span>](icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="46df4-110">Obtém o número de threads que são usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="46df4-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="46df4-111">Método Next</span><span class="sxs-lookup"><span data-stu-id="46df4-111">Next Method</span></span>](icorprofilerthreadenum-next-method.md)|<span data-ttu-id="46df4-112">Obtém o número especificado de threads contíguos de uma coleção sequencial de threads, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="46df4-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="46df4-113">Método Reset</span><span class="sxs-lookup"><span data-stu-id="46df4-113">Reset Method</span></span>](icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="46df4-114">Move o cursor do enumerador para a posição inicial da sequência.</span><span class="sxs-lookup"><span data-stu-id="46df4-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="46df4-115">Método Skip</span><span class="sxs-lookup"><span data-stu-id="46df4-115">Skip Method</span></span>](icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="46df4-116">Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.</span><span class="sxs-lookup"><span data-stu-id="46df4-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46df4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="46df4-117">Remarks</span></span>  

 <span data-ttu-id="46df4-118">A `ICorProfilerThreadEnum` interface é um enumerador.</span><span class="sxs-lookup"><span data-stu-id="46df4-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="46df4-119">Ele permite que o destinatário de uma matriz Extraia elementos do remetente a uma taxa apropriada para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="46df4-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="46df4-120">Em outras palavras, o receptor é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando, assim, os problemas associados à passagem de matrizes grandes como parâmetros de método.</span><span class="sxs-lookup"><span data-stu-id="46df4-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46df4-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46df4-121">Requirements</span></span>  

 <span data-ttu-id="46df4-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46df4-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46df4-123">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="46df4-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46df4-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46df4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46df4-125">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46df4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46df4-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="46df4-126">See also</span></span>

- [<span data-ttu-id="46df4-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="46df4-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="46df4-128">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="46df4-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
