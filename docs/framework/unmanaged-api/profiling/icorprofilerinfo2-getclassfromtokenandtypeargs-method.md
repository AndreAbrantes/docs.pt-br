---
title: Método ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: e0663ff122397ba639a0a219e513be2f3f0cbbef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862757"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="0f4c8-102">Método ICorProfilerInfo2::GetClassFromTokenAndTypeArgs</span><span class="sxs-lookup"><span data-stu-id="0f4c8-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="0f4c8-103">Obtém a `ClassID` de um tipo usando o token de metadados especificado e os valores de `ClassID` de qualquer argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f4c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f4c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f4c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f4c8-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="0f4c8-106">no A ID do módulo no qual o tipo reside.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="0f4c8-107">no Um `mdTypeDef` token de metadados que faz referência ao tipo.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="0f4c8-108">no O número de parâmetros de tipo para o tipo fornecido.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="0f4c8-109">Esse valor deve ser zero para tipos não genéricos.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="0f4c8-110">no Uma matriz de valores de `ClassID`, cada um dos quais é um argumento do tipo.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="0f4c8-111">O valor de `typeArgs` pode ser nulo se `cTypeArgs` for definido como zero.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="0f4c8-112">fora Um ponteiro para a `ClassID` do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f4c8-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f4c8-113">Remarks</span></span>  
 <span data-ttu-id="0f4c8-114">Chamar o método `GetClassFromTokenAndTypeArgs` com um `mdTypeRef` em vez de um token de metadados `mdTypeDef` pode ter resultados imprevisíveis; os chamadores devem resolver o `mdTypeRef` a um `mdTypeDef` ao passá-lo.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="0f4c8-115">Se o tipo ainda não estiver carregado, chamar `GetClassFromTokenAndTypeArgs` irá disparar o carregamento, que é uma operação perigosa em muitos contextos.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="0f4c8-116">Por exemplo, chamar esse método durante o carregamento de módulos ou outros tipos pode levar a um loop infinito, pois o tempo de execução tenta carregar as coisas de forma circular.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="0f4c8-117">Em geral, o uso de `GetClassFromTokenAndTypeArgs` não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="0f4c8-118">Se os profileres estiverem interessados em eventos para um tipo específico, eles deverão armazenar o `ModuleID` e `mdTypeDef` desse tipo e usar [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) para verificar se um determinado `ClassID` é do tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f4c8-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0f4c8-119">Requirements</span></span>  
 <span data-ttu-id="0f4c8-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f4c8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f4c8-121">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0f4c8-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f4c8-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f4c8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f4c8-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f4c8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f4c8-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="0f4c8-124">See also</span></span>

- [<span data-ttu-id="0f4c8-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="0f4c8-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0f4c8-126">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="0f4c8-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
