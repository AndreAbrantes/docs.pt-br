---
title: Método ICorProfilerInfo2::GetBoxClassLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 500cf74c320438fc1b78f0aac737b418716e1a11
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862822"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="c2015-102">Método ICorProfilerInfo2::GetBoxClassLayout</span><span class="sxs-lookup"><span data-stu-id="c2015-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="c2015-103">Obtém informações sobre onde o tipo de valor especificado está localizado quando ele está em caixa.</span><span class="sxs-lookup"><span data-stu-id="c2015-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2015-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2015-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2015-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2015-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="c2015-106">no A ID da classe que descreve o tipo de valor que está em caixa.</span><span class="sxs-lookup"><span data-stu-id="c2015-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="c2015-107">fora Um inteiro que é o deslocamento, relativo ao ponteiro da ID do objeto em caixa, do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="c2015-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2015-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2015-108">Remarks</span></span>  
 <span data-ttu-id="c2015-109">O valor de `pBufferOffset` é o local do tipo de valor dentro de uma caixa.</span><span class="sxs-lookup"><span data-stu-id="c2015-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="c2015-110">Depois que `pBufferOffset` é aplicado a um objeto em caixa, o layout de classe do tipo de valor pode ser usado para interpretar o valor do objeto.</span><span class="sxs-lookup"><span data-stu-id="c2015-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2015-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c2015-111">Requirements</span></span>  
 <span data-ttu-id="c2015-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2015-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2015-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c2015-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2015-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2015-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2015-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2015-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2015-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="c2015-116">See also</span></span>

- [<span data-ttu-id="c2015-117">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c2015-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c2015-118">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="c2015-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
