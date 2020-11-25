---
title: Interface ICorProfilerInfo6
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: b3aed97e19694675fd5e0c1070dbbf6d9321eedd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733835"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="590d6-102">Interface ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="590d6-102">ICorProfilerInfo6 Interface</span></span>

<span data-ttu-id="590d6-103">[Com suporte no .NET Framework 4,6 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="590d6-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="590d6-104">Uma subclasse de [ICorProfilerInfo5](icorprofilerinfo5-interface.md) que fornece um enumerador para todos os métodos que são definidos em um determinado módulo NGen e embutidos em um determinado método.</span><span class="sxs-lookup"><span data-stu-id="590d6-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="590d6-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="590d6-105">Methods</span></span>  
  
|<span data-ttu-id="590d6-106">Método</span><span class="sxs-lookup"><span data-stu-id="590d6-106">Method</span></span>|<span data-ttu-id="590d6-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="590d6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="590d6-108">Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="590d6-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="590d6-109">Retorna um enumerador para todos os métodos que pertencem a um determinado módulo NGen e que são embutidos no corpo de um determinado método.</span><span class="sxs-lookup"><span data-stu-id="590d6-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="590d6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="590d6-110">Requirements</span></span>  

 <span data-ttu-id="590d6-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="590d6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="590d6-112">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="590d6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="590d6-113">**.NET Framework versões:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="590d6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590d6-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="590d6-114">See also</span></span>

- [<span data-ttu-id="590d6-115">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="590d6-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
