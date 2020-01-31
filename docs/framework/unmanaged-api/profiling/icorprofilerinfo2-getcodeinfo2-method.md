---
title: Método ICorProfilerInfo2::GetCodeInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 9295ea8b22f72529f55cbe13f6a79a0aa34d2fa0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868757"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="93845-102">Método ICorProfilerInfo2::GetCodeInfo2</span><span class="sxs-lookup"><span data-stu-id="93845-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="93845-103">Obtém as extensões do código nativo associado ao `FunctionID`especificado.</span><span class="sxs-lookup"><span data-stu-id="93845-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93845-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93845-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93845-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93845-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="93845-106">no A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="93845-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="93845-107">no O tamanho da matriz de `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="93845-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="93845-108">fora Um ponteiro para o número total de estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponíveis.</span><span class="sxs-lookup"><span data-stu-id="93845-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="93845-109">fora Um buffer fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="93845-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="93845-110">Depois que o método retorna, ele contém uma matriz de estruturas `COR_PRF_CODE_INFO`, cada uma delas descreve um bloco de código nativo.</span><span class="sxs-lookup"><span data-stu-id="93845-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93845-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="93845-111">Remarks</span></span>  
 <span data-ttu-id="93845-112">As extensões são classificadas em ordem de aumento do deslocamento da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="93845-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="93845-113">Depois que `GetCodeInfo2` retorna, você deve verificar se o buffer de `codeInfos` era grande o suficiente para conter todas as estruturas de `COR_PRF_CODE_INFO`.</span><span class="sxs-lookup"><span data-stu-id="93845-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="93845-114">Para fazer isso, compare o valor de `cCodeInfos` com o valor do parâmetro `cchName`.</span><span class="sxs-lookup"><span data-stu-id="93845-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="93845-115">Se `cCodeInfos` dividido pelo tamanho de uma estrutura de `COR_PRF_CODE_INFO` for menor do que `pcCodeInfos`, aloque um buffer de `codeInfos` maior, atualize `cCodeInfos` com o tamanho novo, maior e chame `GetCodeInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="93845-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="93845-116">Como alternativa, você pode primeiro chamar `GetCodeInfo2` com um buffer de `codeInfos` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="93845-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="93845-117">Em seguida, você pode definir o tamanho do buffer de `codeInfos` para o valor retornado em `pcCodeInfos`, multiplicado pelo tamanho de uma estrutura de `COR_PRF_CODE_INFO` e chamar `GetCodeInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="93845-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93845-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="93845-118">Requirements</span></span>  
 <span data-ttu-id="93845-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93845-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93845-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="93845-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93845-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93845-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93845-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93845-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93845-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="93845-123">See also</span></span>

- [<span data-ttu-id="93845-124">Método GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="93845-124">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="93845-125">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="93845-125">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="93845-126">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="93845-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="93845-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="93845-127">Profiling</span></span>](index.md)
