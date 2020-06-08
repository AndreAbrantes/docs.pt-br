---
title: ICorProfilerCallback6::Método GetAssemblyReferences
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: 5deacbff740ebb1dcc8cb8d1fb7e4eb0d4bdcc30
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499214"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="e708d-102">ICorProfilerCallback6::Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="e708d-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>
<span data-ttu-id="e708d-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="e708d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e708d-104">Notifica o criador de perfis de que um assembly está em um estágio inicial de carregamento, quando o Common Language Runtime realiza um exame de fechamento da referência do assembly.</span><span class="sxs-lookup"><span data-stu-id="e708d-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e708d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e708d-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e708d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e708d-106">Parameters</span></span>  
 `wszAssemblyPath`  
 <span data-ttu-id="e708d-107">[in] O caminho e o nome do assembly cujos metadados serão modificados.</span><span class="sxs-lookup"><span data-stu-id="e708d-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="e708d-108">no Um ponteiro para o endereço de uma interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) que especifica as referências de assembly a serem adicionadas.</span><span class="sxs-lookup"><span data-stu-id="e708d-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e708d-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="e708d-109">Return Value</span></span>  
 <span data-ttu-id="e708d-110">Os valores retornados desse retorno de chamada são ignorados.</span><span class="sxs-lookup"><span data-stu-id="e708d-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e708d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e708d-111">Remarks</span></span>  
 <span data-ttu-id="e708d-112">Esse retorno de chamada é controlado pela definição do sinalizador de máscara de evento [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) ao chamar o método [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e708d-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="e708d-113">Se o criador de perfil se registrar para o método de retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , o tempo de execução passará o caminho e o nome do assembly a ser carregado, juntamente com um ponteiro para um objeto de interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) para esse método.</span><span class="sxs-lookup"><span data-stu-id="e708d-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="e708d-114">O criador de perfil pode então chamar o método [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) com um `COR_PRF_ASSEMBLY_REFERENCE_INFO` objeto para cada assembly de destino que planeja fazer referência a partir do assembly especificado no `GetAssemblyReferences` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="e708d-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="e708d-115">Use o retorno de chamada `GetAssemblyReferences` apenas se for necessário ao criador de perfis modificar os metadados de um assembly para adicionar referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="e708d-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="e708d-116">(Mas observe que a modificação real dos metadados de um assembly é feita no método de retorno de chamada [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).) O criador de perfil deve implementar o `GetAssemblyReferences` método de retorno de chamada para informar ao Common Language Runtime (CLR) que as referências de assembly serão adicionadas quando o módulo for carregado.</span><span class="sxs-lookup"><span data-stu-id="e708d-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="e708d-117">Isso ajuda a garantir que decisões de compartilhamento de assembly tomadas pelo CLR durante esse estágio inicial permanecem válidas apesar de o criador de perfis planejar modificar as referências de metadados do assembly mais tarde.</span><span class="sxs-lookup"><span data-stu-id="e708d-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="e708d-118">Isso pode evitar algumas instâncias nas quais as modificações de metadados do criador de perfis causam um erro de `SECURITY_E_INCOMPATIBLE_SHARE`.</span><span class="sxs-lookup"><span data-stu-id="e708d-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="e708d-119">O criador de perfil usa o objeto [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) fornecido por esse método para adicionar referências de assembly ao suplemento de referência de assembly CLR.</span><span class="sxs-lookup"><span data-stu-id="e708d-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="e708d-120">O objeto [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) deve ser usado somente de dentro deste retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="e708d-120">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="e708d-121">Chamadas para o método [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) desse retorno de chamada não resultam em metadados modificados, mas apenas em uma movimentação de fechamento de referência de assembly modificada.</span><span class="sxs-lookup"><span data-stu-id="e708d-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="e708d-122">O criador de perfil ainda terá que usar um objeto [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) para adicionar explicitamente referências de assembly de dentro do retorno de chamada [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) para o assembly de referência, mesmo que ele implemente o `GetAssemblyReferences` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="e708d-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="e708d-123">O criador de perfil deve estar preparado para receber chamadas duplicadas para esse retorno de chamada para o mesmo assembly e deve responder de forma idêntica para cada uma dessas chamadas duplicadas (fazendo o mesmo conjunto de chamadas [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="e708d-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e708d-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e708d-124">Requirements</span></span>  
 <span data-ttu-id="e708d-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e708d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e708d-126">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e708d-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e708d-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e708d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e708d-128">**.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e708d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e708d-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="e708d-129">See also</span></span>

- [<span data-ttu-id="e708d-130">Interface ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="e708d-130">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)
- [<span data-ttu-id="e708d-131">Método ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="e708d-131">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="e708d-132">Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="e708d-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="e708d-133">Interface ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="e708d-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
