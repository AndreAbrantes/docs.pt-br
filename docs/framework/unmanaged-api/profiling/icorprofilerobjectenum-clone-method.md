---
title: Método ICorProfilerObjectEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: a2a54c32c0713b4b69d8f2a0272687cbe9420610
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494755"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="d7371-102">Método ICorProfilerObjectEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="d7371-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="d7371-103">Obtém um ponteiro de interface para uma cópia desta interface [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d7371-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7371-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7371-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7371-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7371-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d7371-106">fora Um ponteiro para o ponteiro de interface que, por sua vez, aponta para a cópia dessa `ICorProfilerObjectEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="d7371-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="d7371-107">A cópia mantém seu próprio estado de enumeração separadamente deste.</span><span class="sxs-lookup"><span data-stu-id="d7371-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="d7371-108">No entanto, a posição inicial do cursor da cópia será a mesma posição do cursor atual do enumerador.</span><span class="sxs-lookup"><span data-stu-id="d7371-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7371-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7371-109">Requirements</span></span>  
 <span data-ttu-id="d7371-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7371-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7371-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d7371-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7371-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7371-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7371-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7371-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7371-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7371-114">See also</span></span>

- [<span data-ttu-id="d7371-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="d7371-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
