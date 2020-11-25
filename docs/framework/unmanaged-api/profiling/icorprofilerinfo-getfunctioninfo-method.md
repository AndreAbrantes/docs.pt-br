---
title: Método ICorProfilerInfo::GetFunctionInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: 6aaa02d72dd10fe72d773246d55216143786dabb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722526"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="7fb3b-102">Método ICorProfilerInfo::GetFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="7fb3b-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>

<span data-ttu-id="7fb3b-103">Obtém a classe pai e o token de metadados para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fb3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fb3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fb3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fb3b-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="7fb3b-106">no A ID da função para a qual obter a classe pai e o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="7fb3b-107">fora Um ponteiro para a classe pai da função.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="7fb3b-108">fora Um ponteiro para o módulo no qual a classe pai da função é definida.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="7fb3b-109">fora Um ponteiro para o token de metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fb3b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7fb3b-110">Remarks</span></span>  

 <span data-ttu-id="7fb3b-111">O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de metadados para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="7fb3b-112">O token de metadados que é retornado para o local referenciado por `pToken` pode ser usado para acessar os metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="7fb3b-113">`ClassID`Talvez não seja possível obter o de uma função em uma classe genérica sem mais informações contextuais sobre o uso da função.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="7fb3b-114">Nesse caso, `pClassId` será 0.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="7fb3b-115">O código do criador de perfil deve usar [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) com um valor COR_PRF_FRAME_INFO para fornecer mais contexto.</span><span class="sxs-lookup"><span data-stu-id="7fb3b-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fb3b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fb3b-116">Requirements</span></span>  

 <span data-ttu-id="7fb3b-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fb3b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fb3b-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7fb3b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7fb3b-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fb3b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fb3b-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fb3b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb3b-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="7fb3b-121">See also</span></span>

- [<span data-ttu-id="7fb3b-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7fb3b-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
