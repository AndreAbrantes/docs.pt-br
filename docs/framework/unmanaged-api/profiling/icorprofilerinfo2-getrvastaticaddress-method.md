---
title: Método ICorProfilerInfo2::GetRVAStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: ea4f6f129cf2919124b1bef1fd837f2b1e13760e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727049"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="b1a90-102">Método ICorProfilerInfo2::GetRVAStaticAddress</span><span class="sxs-lookup"><span data-stu-id="b1a90-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>

<span data-ttu-id="b1a90-103">Obtém o endereço do campo estático de endereço virtual relativo (RVA) especificado.</span><span class="sxs-lookup"><span data-stu-id="b1a90-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a90-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1a90-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a90-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1a90-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="b1a90-106">no A ID da classe que contém o campo RVA-static solicitado.</span><span class="sxs-lookup"><span data-stu-id="b1a90-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="b1a90-107">no Token de metadados para o campo RVA-static solicitado.</span><span class="sxs-lookup"><span data-stu-id="b1a90-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="b1a90-108">fora Um ponteiro para o endereço do campo RVA-estático.</span><span class="sxs-lookup"><span data-stu-id="b1a90-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1a90-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1a90-109">Remarks</span></span>  

 <span data-ttu-id="b1a90-110">O `GetRVAStaticAddress` método pode retornar um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="b1a90-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="b1a90-111">Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.</span><span class="sxs-lookup"><span data-stu-id="b1a90-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="b1a90-112">Os endereços de objetos que podem estar no heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b1a90-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="b1a90-113">Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, os profileres não devem presumir que eles são válidos.</span><span class="sxs-lookup"><span data-stu-id="b1a90-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="b1a90-114">Antes que o construtor de classe de uma classe seja concluído, o `GetRVAStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos já possam ser inicializados e possam estar enraizadando objetos de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b1a90-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a90-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1a90-115">Requirements</span></span>  

 <span data-ttu-id="b1a90-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a90-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a90-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b1a90-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1a90-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1a90-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1a90-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a90-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a90-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="b1a90-120">See also</span></span>

- [<span data-ttu-id="b1a90-121">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b1a90-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b1a90-122">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="b1a90-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
