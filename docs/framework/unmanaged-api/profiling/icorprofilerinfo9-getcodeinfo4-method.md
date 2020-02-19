---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f65cebff912adeb7afc34434467cf7be72f9be32
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449758"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="d434a-102">Método ICorProfilerInfo9:: GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="d434a-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="d434a-103">Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código.</span><span class="sxs-lookup"><span data-stu-id="d434a-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="d434a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d434a-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="d434a-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d434a-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="d434a-106">\[em] um ponteiro para o início de uma função nativa.</span><span class="sxs-lookup"><span data-stu-id="d434a-106">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="d434a-107">\[em] o tamanho da matriz de `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="d434a-107">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="d434a-108">\[out] um ponteiro para o número total de estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d434a-108">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="d434a-109">\[out] um buffer fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="d434a-109">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="d434a-110">Depois que o método retorna, ele contém uma matriz de estruturas `COR_PRF_CODE_INFO`, cada uma delas descreve um bloco de código nativo.</span><span class="sxs-lookup"><span data-stu-id="d434a-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d434a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d434a-111">Remarks</span></span>

<span data-ttu-id="d434a-112">O método `GetCodeInfo4` é semelhante a [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), exceto pelo fato de que ele pode pesquisar informações de código para versões nativas diferentes de um método.</span><span class="sxs-lookup"><span data-stu-id="d434a-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="d434a-113">`GetCodeInfo4` pode disparar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d434a-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="d434a-114">As extensões são classificadas em ordem crescente de deslocamento de Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="d434a-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="d434a-115">Depois que `GetCodeInfo4` retorna, você deve verificar se o buffer de `codeInfos` era grande o suficiente para conter todas as estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="d434a-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="d434a-116">Para fazer isso, compare o valor de `cCodeInfos` com o valor do parâmetro `cchName`.</span><span class="sxs-lookup"><span data-stu-id="d434a-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="d434a-117">Se `cCodeInfos` dividido pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) for menor do que `pcCodeInfos`, aloque um buffer de `codeInfos` maior, atualize `cCodeInfos` com o tamanho novo, maior e chame `GetCodeInfo4` novamente.</span><span class="sxs-lookup"><span data-stu-id="d434a-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="d434a-118">Como alternativa, você pode primeiro chamar `GetCodeInfo4` com um buffer de `codeInfos` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="d434a-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d434a-119">Em seguida, você pode definir o tamanho do buffer de `codeInfos` para o valor retornado em `pcCodeInfos`, multiplicado pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) e chamar `GetCodeInfo4` novamente.</span><span class="sxs-lookup"><span data-stu-id="d434a-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="d434a-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d434a-120">Requirements</span></span>

<span data-ttu-id="d434a-121">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="d434a-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="d434a-122">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d434a-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d434a-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d434a-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d434a-124">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d434a-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d434a-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="d434a-125">See also</span></span>

- [<span data-ttu-id="d434a-126">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="d434a-126">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
