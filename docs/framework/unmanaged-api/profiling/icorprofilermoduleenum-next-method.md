---
title: Método ICorProfilerModuleEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 94c2c159cf386e00dfc0d1df97536d7ade53407e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732938"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="712b5-102">Método ICorProfilerModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="712b5-102">ICorProfilerModuleEnum::Next Method</span></span>

<span data-ttu-id="712b5-103">Obtém o número especificado de módulos contíguos de uma coleção sequencial de módulos, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="712b5-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="712b5-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="712b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="712b5-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="712b5-106">no O número de módulos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="712b5-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="712b5-107">fora Uma matriz de `ModuleID` valores, cada um representando um módulo recuperado.</span><span class="sxs-lookup"><span data-stu-id="712b5-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="712b5-108">fora Um ponteiro para o número de elementos realmente retornados na `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="712b5-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="712b5-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="712b5-109">Return Value</span></span>  

 <span data-ttu-id="712b5-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="712b5-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="712b5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="712b5-111">HRESULT</span></span>|<span data-ttu-id="712b5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="712b5-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="712b5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="712b5-113">S_OK</span></span>|<span data-ttu-id="712b5-114">`celt` elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="712b5-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="712b5-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="712b5-115">S_FALSE</span></span>|<span data-ttu-id="712b5-116">Menos de `celt` elementos foram retornados, o que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="712b5-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="712b5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="712b5-117">Requirements</span></span>  

 <span data-ttu-id="712b5-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="712b5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712b5-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="712b5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="712b5-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="712b5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="712b5-121">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="712b5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712b5-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="712b5-122">See also</span></span>

- [<span data-ttu-id="712b5-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="712b5-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="712b5-124">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="712b5-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
