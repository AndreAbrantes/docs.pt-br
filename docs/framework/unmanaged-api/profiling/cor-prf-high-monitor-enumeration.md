---
title: Enumeração COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 72324fd434f3f37f723988345514c8aaada07ca9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867146"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="7893a-102">Enumeração COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="7893a-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="7893a-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="7893a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="7893a-104">Fornece sinalizadores além daqueles encontrados na enumeração de [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) que o criador de perfil pode especificar para o método [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) quando ele está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="7893a-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7893a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7893a-105">Syntax</span></span>  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="7893a-106">Membros</span><span class="sxs-lookup"><span data-stu-id="7893a-106">Members</span></span>  
  
|<span data-ttu-id="7893a-107">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7893a-107">Member</span></span>|<span data-ttu-id="7893a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7893a-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="7893a-109">Nenhum sinalizador está definido.</span><span class="sxs-lookup"><span data-stu-id="7893a-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="7893a-110">Controla o retorno de chamada [ICorProfilerCallback6:: GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) para adicionar referências de assembly durante a movimentação de fechamento de referência do assembly CLR.</span><span class="sxs-lookup"><span data-stu-id="7893a-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="7893a-111">Controla o retorno de chamada [ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) para atualizações para o fluxo de símbolos associado a um módulo na memória.</span><span class="sxs-lookup"><span data-stu-id="7893a-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="7893a-112">Controla o retorno de chamada [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) para indicar quando um método dinâmico foi coletado pelo lixo e descarregado.</span><span class="sxs-lookup"><span data-stu-id="7893a-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="7893a-113">Somente .NET Core 3,0 e versões posteriores: desabilita a [compilação em camadas](../../../core/whats-new/dotnet-core-3-0.md) para os profileres.</span><span class="sxs-lookup"><span data-stu-id="7893a-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="7893a-114">Somente o .NET Core 3,0 e versões posteriores: fornece uma opção de criação de perfil de GC leve em comparação com [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7893a-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="7893a-115">Controla somente os retornos de chamada [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)e [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7893a-115">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="7893a-116">Ao contrário do sinalizador de `COR_PRF_MONITOR_GC`, `COR_PRF_HIGH_BASIC_GC` não desabilita a coleta de lixo simultânea.</span><span class="sxs-lookup"><span data-stu-id="7893a-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="7893a-117">Somente o .NET Core 3,0 e versões posteriores: habilita os retornos de chamada [MovedReferences](icorprofilercallback-movedreferences-method.md) e [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) apenas para os GCS de compactação.</span><span class="sxs-lookup"><span data-stu-id="7893a-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="7893a-118">Somente o .NET Core 3,0 e versões posteriores: semelhante a [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), mas fornece informações sobre alocações de objeto somente para o LOH (heap de objeto grande).</span><span class="sxs-lookup"><span data-stu-id="7893a-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="7893a-119">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que necessitam de imagens aprimoradas por perfil.</span><span class="sxs-lookup"><span data-stu-id="7893a-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="7893a-120">Ele corresponde ao sinalizador `COR_PRF_REQUIRE_PROFILE_IMAGE` na enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7893a-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="7893a-121">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="7893a-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="7893a-122">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos apenas durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="7893a-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="7893a-123">Tentar alterar qualquer um desses sinalizadores em outro lugar resulta em um valor de `HRESULT` que indica falha.</span><span class="sxs-lookup"><span data-stu-id="7893a-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7893a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="7893a-124">Remarks</span></span>

<span data-ttu-id="7893a-125">Os sinalizadores de `COR_PRF_HIGH_MONITOR` são usados com o parâmetro `pdwEventsHigh` dos métodos [ICorProfilerInfo5:: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) e [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7893a-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="7893a-126">Começando com o .NET Framework 4.6.1, o valor da `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` alterado de 0 para `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="7893a-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="7893a-127">Começando com o .NET Framework 4.7.2, seu valor mudou de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` para `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="7893a-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="7893a-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` se destina a ser um bitmask que representa todos os sinalizadores que só podem ser definidos durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="7893a-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="7893a-129">A tentativa de alterar qualquer um desses sinalizadores em outro lugar resulta em um `HRESULT`com falha.</span><span class="sxs-lookup"><span data-stu-id="7893a-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="7893a-130">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7893a-130">Requirements</span></span>

<span data-ttu-id="7893a-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7893a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="7893a-132">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7893a-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="7893a-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7893a-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="7893a-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7893a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7893a-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="7893a-135">See also</span></span>

- [<span data-ttu-id="7893a-136">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="7893a-136">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="7893a-137">Enumeração COR_PRF_MONITOR</span><span class="sxs-lookup"><span data-stu-id="7893a-137">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="7893a-138">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="7893a-138">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
