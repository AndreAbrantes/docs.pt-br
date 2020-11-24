---
title: Método ICorProfilerInfo3::EnumModules
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 698f6abc872a7e072ae47520386aa9c7ddfb44fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681464"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="6ddf1-102">Método ICorProfilerInfo3::EnumModules</span><span class="sxs-lookup"><span data-stu-id="6ddf1-102">ICorProfilerInfo3::EnumModules Method</span></span>

<span data-ttu-id="6ddf1-103">Retorna um enumerador que fornece métodos para iterar em sequência por meio de uma coleção de módulos gerenciados que são carregados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ddf1-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ddf1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ddf1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ddf1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ddf1-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="6ddf1-106">fora Um ponteiro para uma interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6ddf1-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ddf1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ddf1-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ddf1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ddf1-108">Requirements</span></span>  

 <span data-ttu-id="6ddf1-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ddf1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ddf1-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6ddf1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6ddf1-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ddf1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ddf1-112">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ddf1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ddf1-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="6ddf1-113">See also</span></span>

- [<span data-ttu-id="6ddf1-114">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="6ddf1-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="6ddf1-115">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="6ddf1-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6ddf1-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="6ddf1-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6ddf1-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6ddf1-117">Profiling</span></span>](index.md)
