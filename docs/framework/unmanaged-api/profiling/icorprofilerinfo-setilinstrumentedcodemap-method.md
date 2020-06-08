---
title: Método ICorProfilerInfo::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: cac8e9570dab55af6b6e1fcf6f53b6a697727972
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502906"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="5af0d-102">Método ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="5af0d-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="5af0d-103">Define um mapa de código para a função especificada usando as entradas de mapa da MSIL (Microsoft Intermediate Language) especificadas.</span><span class="sxs-lookup"><span data-stu-id="5af0d-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="5af0d-104">No .NET Framework versão 2,0, chamar `SetILInstrumentedCodeMap` em um `FunctionID` que representa uma função genérica em um domínio de aplicativo específico afetará todas as instâncias dessa função no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5af0d-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="5af0d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5af0d-105">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="5af0d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5af0d-106">Parameters</span></span>

`functionId`\
<span data-ttu-id="5af0d-107">no A ID da função para a qual definir o mapa de código.</span><span class="sxs-lookup"><span data-stu-id="5af0d-107">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="5af0d-108">no Um valor booliano que indica se a chamada para o `SetILInstrumentedCodeMap` método é a primeira para um específico `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="5af0d-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="5af0d-109">Defina `fStartJit` como `true` na primeira chamada para `SetILInstrumentedCodeMap` para um determinado `FunctionID` e para `false` depois.</span><span class="sxs-lookup"><span data-stu-id="5af0d-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="5af0d-110">no O número de elementos na `cILMapEntries` matriz.</span><span class="sxs-lookup"><span data-stu-id="5af0d-110">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="5af0d-111">no Uma matriz de estruturas COR_IL_MAP, cada uma delas especifica um deslocamento MSIL.</span><span class="sxs-lookup"><span data-stu-id="5af0d-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="5af0d-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5af0d-112">Remarks</span></span>

<span data-ttu-id="5af0d-113">Um criador de perfil geralmente insere instruções no código-fonte de um método para instrumentar esse método (por exemplo, para notificar quando uma determinada linha de origem for atingida).</span><span class="sxs-lookup"><span data-stu-id="5af0d-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="5af0d-114">`SetILInstrumentedCodeMap`permite que um criador de perfil Mapeie as instruções originais do MSIL para seus novos locais.</span><span class="sxs-lookup"><span data-stu-id="5af0d-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="5af0d-115">Um criador de perfil pode usar o método [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) para obter o deslocamento de MSIL original para um determinado deslocamento nativo.</span><span class="sxs-lookup"><span data-stu-id="5af0d-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="5af0d-116">O depurador assumirá que cada deslocamento antigo se refere a um deslocamento MSIL dentro do código MSIL original e não modificado, e que cada deslocamento novo se refere ao deslocamento MSIL dentro do novo código instrumentado.</span><span class="sxs-lookup"><span data-stu-id="5af0d-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="5af0d-117">O mapa deve ser classificado em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="5af0d-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="5af0d-118">Para que a depuração funcione corretamente, siga estas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="5af0d-118">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="5af0d-119">Não reordene o código MSIL instrumentado.</span><span class="sxs-lookup"><span data-stu-id="5af0d-119">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="5af0d-120">Não remova o código MSIL original.</span><span class="sxs-lookup"><span data-stu-id="5af0d-120">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="5af0d-121">Inclua entradas para todos os pontos de sequência do arquivo de banco de dados do programa (PDB) no mapa.</span><span class="sxs-lookup"><span data-stu-id="5af0d-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="5af0d-122">O mapa não interpola as entradas ausentes.</span><span class="sxs-lookup"><span data-stu-id="5af0d-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="5af0d-123">Portanto, considerando o seguinte mapa:</span><span class="sxs-lookup"><span data-stu-id="5af0d-123">So, given the following map:</span></span>

  <span data-ttu-id="5af0d-124">(0 antigo, 0 novo)</span><span class="sxs-lookup"><span data-stu-id="5af0d-124">(0 old, 0 new)</span></span>

  <span data-ttu-id="5af0d-125">(5 antigos, 10 novos)</span><span class="sxs-lookup"><span data-stu-id="5af0d-125">(5 old, 10 new)</span></span>

  <span data-ttu-id="5af0d-126">(9 antigos, 20 novos)</span><span class="sxs-lookup"><span data-stu-id="5af0d-126">(9 old, 20 new)</span></span>

  - <span data-ttu-id="5af0d-127">Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para o novo deslocamento 0.</span><span class="sxs-lookup"><span data-stu-id="5af0d-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="5af0d-128">Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento 10.</span><span class="sxs-lookup"><span data-stu-id="5af0d-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="5af0d-129">Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.</span><span class="sxs-lookup"><span data-stu-id="5af0d-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="5af0d-130">Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o deslocamento antigo 0.</span><span class="sxs-lookup"><span data-stu-id="5af0d-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="5af0d-131">Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.</span><span class="sxs-lookup"><span data-stu-id="5af0d-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="5af0d-132">Um novo deslocamento de 20 ou mais será mapeado para o deslocamento antigo 9.</span><span class="sxs-lookup"><span data-stu-id="5af0d-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="5af0d-133">No .NET Framework 3,5 e versões anteriores, você aloca a `rgILMapEntries` matriz chamando o método [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) .</span><span class="sxs-lookup"><span data-stu-id="5af0d-133">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="5af0d-134">Como o tempo de execução se apropria dessa memória, o criador de perfil não deve tentar liberá-la.</span><span class="sxs-lookup"><span data-stu-id="5af0d-134">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="5af0d-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5af0d-135">Requirements</span></span>

<span data-ttu-id="5af0d-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5af0d-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5af0d-137">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5af0d-137">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5af0d-138">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5af0d-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5af0d-139">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5af0d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5af0d-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="5af0d-140">See also</span></span>

- [<span data-ttu-id="5af0d-141">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5af0d-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
