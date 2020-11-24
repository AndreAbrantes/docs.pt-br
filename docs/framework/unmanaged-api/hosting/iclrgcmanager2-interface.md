---
title: Interface ICLRGCManager2
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: d2873b5e1f8229e8a16dfaacf1c9737ac47405bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672793"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="558ef-102">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="558ef-102">ICLRGCManager2 Interface</span></span>

<span data-ttu-id="558ef-103">Fornece métodos que permitem que um host interaja com o sistema de coleta de lixo do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="558ef-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="558ef-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="558ef-104">Methods</span></span>  
  
|<span data-ttu-id="558ef-105">Método</span><span class="sxs-lookup"><span data-stu-id="558ef-105">Method</span></span>|<span data-ttu-id="558ef-106">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="558ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="558ef-107">Método SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="558ef-107">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="558ef-108">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="558ef-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="558ef-109">Habilita a geração 0 e os tamanhos de segmento maiores que `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="558ef-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="558ef-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="558ef-110">Remarks</span></span>  

 <span data-ttu-id="558ef-111">Essa interface herda da [interface ICLRGCManager](iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="558ef-111">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="558ef-112">O Common Language Runtime (CLR) implementa seu mecanismo de coleta de lixo com o <xref:System.GC> tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="558ef-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="558ef-113">Para obter mais informações sobre o sistema de coleta de lixo, consulte [coleta de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="558ef-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="558ef-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="558ef-114">Requirements</span></span>  

 <span data-ttu-id="558ef-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="558ef-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="558ef-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="558ef-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="558ef-117">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="558ef-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="558ef-118">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="558ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="558ef-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="558ef-119">See also</span></span>

- [<span data-ttu-id="558ef-120">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="558ef-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="558ef-121">Estrutura COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="558ef-121">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="558ef-122">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="558ef-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="558ef-123">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="558ef-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="558ef-124">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="558ef-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="558ef-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="558ef-125">Hosting</span></span>](index.md)
