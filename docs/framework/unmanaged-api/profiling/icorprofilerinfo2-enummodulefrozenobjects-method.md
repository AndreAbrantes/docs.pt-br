---
title: Método ICorProfilerInfo2::EnumModuleFrozenObjects
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: 1fe44f8f84c079e920c8c82fb9d52d1980d3b852
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497199"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="f5eb8-102">Método ICorProfilerInfo2::EnumModuleFrozenObjects</span><span class="sxs-lookup"><span data-stu-id="f5eb8-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="f5eb8-103">Obtém um enumerador que permite a iteração sobre os objetos congelados no módulo especificado. Este método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f5eb8-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5eb8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5eb8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5eb8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5eb8-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="f5eb8-106">no A ID do módulo que contém os objetos congelados a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="f5eb8-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="f5eb8-107">fora Um ponteiro para o endereço de uma interface [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) , que enumera os objetos congelados.</span><span class="sxs-lookup"><span data-stu-id="f5eb8-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5eb8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5eb8-108">Requirements</span></span>  
 <span data-ttu-id="f5eb8-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5eb8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5eb8-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f5eb8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5eb8-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5eb8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5eb8-112">**.NET Framework versões:** 3,5, 3,0 sp1, 3,0, 2,0 SP1, 2,0</span><span class="sxs-lookup"><span data-stu-id="f5eb8-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5eb8-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5eb8-113">See also</span></span>

- [<span data-ttu-id="f5eb8-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f5eb8-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f5eb8-115">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="f5eb8-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
