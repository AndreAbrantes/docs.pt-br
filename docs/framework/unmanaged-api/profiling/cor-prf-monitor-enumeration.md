---
title: Enumeração COR_PRF_MONITOR
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 1ff167121a5bb752c70edd2c5901133503326bea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500800"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="53408-102">Enumeração COR_PRF_MONITOR</span><span class="sxs-lookup"><span data-stu-id="53408-102">COR_PRF_MONITOR Enumeration</span></span>
<span data-ttu-id="53408-103">Contém valores usados para especificar comportamentos, recursos ou eventos que o criador de perfis deseja assinar.</span><span class="sxs-lookup"><span data-stu-id="53408-103">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53408-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53408-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="53408-105">Membros</span><span class="sxs-lookup"><span data-stu-id="53408-105">Members</span></span>  
 <span data-ttu-id="53408-106">As seções a seguir listam `COR_PRF_MONITOR` membros de enumeração por categoria.</span><span class="sxs-lookup"><span data-stu-id="53408-106">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="53408-107">As categorias são:</span><span class="sxs-lookup"><span data-stu-id="53408-107">The categories are:</span></span>  
  
- [<span data-ttu-id="53408-108">Nenhum sinalizador definido</span><span class="sxs-lookup"><span data-stu-id="53408-108">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="53408-109">Sinalizadores de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="53408-109">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="53408-110">Sinalizadores de habilitação de recurso</span><span class="sxs-lookup"><span data-stu-id="53408-110">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="53408-111">Sinalizadores de configuração</span><span class="sxs-lookup"><span data-stu-id="53408-111">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="53408-112">Sinalizadores compostos</span><span class="sxs-lookup"><span data-stu-id="53408-112">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a><span data-ttu-id="53408-113">Nenhum sinalizador definido</span><span class="sxs-lookup"><span data-stu-id="53408-113">No flags set</span></span>  
  
|<span data-ttu-id="53408-114">Membro</span><span class="sxs-lookup"><span data-stu-id="53408-114">Member</span></span>|<span data-ttu-id="53408-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="53408-115">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="53408-116">Nenhum sinalizador está definido.</span><span class="sxs-lookup"><span data-stu-id="53408-116">No flags are set.</span></span>|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a><span data-ttu-id="53408-117">Sinalizadores de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="53408-117">Callback flags</span></span>  
  
|<span data-ttu-id="53408-118">Membro</span><span class="sxs-lookup"><span data-stu-id="53408-118">Member</span></span>|<span data-ttu-id="53408-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="53408-119">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="53408-120">Habilita todos os eventos de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="53408-120">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="53408-121">Controla os `AppDomainCreation*` `AppDomainShutdown*` retornos de chamada e na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-121">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="53408-122">Controla os `AssemblyLoad*` `AssemblyUnload*` retornos de chamada e na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-122">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="53408-123">Controla os `JITCachedFunctionSearch*` retornos de chamada na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-123">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="53408-124">O comportamento deste sinalizador é alterado no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="53408-124">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="53408-125">Controla os `COMClassicVTable*` retornos de chamada na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-125">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="53408-126">Controla os `ClassLoad*` `ClassUnload*` retornos de chamada e na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-126">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="53408-127">Controla os `ExceptionCLRCatcher*` retornos de chamada na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-127">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="53408-128">Controla os retornos de chamada [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) e [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="53408-128">Controls the [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="53408-129">Controla as `FunctionEnter*` `FunctionLeave*` `FunctionTailCall*` [funções estáticas globais](profiling-global-static-functions.md), e de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="53408-129">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="53408-130">Controla o retorno de chamada [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) e os `ExceptionSearch*` `ExceptionOSHandler*` retornos de chamada,, `ExceptionUnwind*` e `ExceptionCatcher*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-130">Controls the [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="53408-131">Controla o retorno de chamada [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-131">Controls the [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="53408-132">Controla os retornos de chamada [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)e [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) nas `ICorProfilerCallback*` interfaces.</span><span class="sxs-lookup"><span data-stu-id="53408-132">Controls the [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="53408-133">Quando `COR_PRF_MONITOR_GC` é alocado, a coleta de lixo simultânea é desativada.</span><span class="sxs-lookup"><span data-stu-id="53408-133">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="53408-134">Controla os `JITCompilation*` retornos de chamada, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md)e [JITInlining](icorprofilercallback-jitinlining-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-134">Controls the `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="53408-135">Controla os `ModuleLoad*` `ModuleUnload*` retornos de chamada, e [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-135">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="53408-136">Controla o retorno de chamada de [ObjectAllocated](icorprofilercallback-objectallocated-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-136">Controls the [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="53408-137">Controla os `Remoting*` retornos de chamada na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-137">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="53408-138">Controla se os retornos de chamada `Remoting*` vão monitorar ou não os eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="53408-138">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="53408-139">Controla se um cookie é passado para os retornos de chamada `Remoting*`.</span><span class="sxs-lookup"><span data-stu-id="53408-139">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="53408-140">Controla os `RuntimeSuspend*` `RuntimeResume*` retornos de chamada,, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)e [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-140">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="53408-141">Controla os retornos de chamada [ThreadCreated](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)e [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) nas interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) e [ICorProfilerCallback2](icorprofilercallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-141">Controls the [ThreadCreated](icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a><span data-ttu-id="53408-142">Sinalizadores de habilitação de recurso</span><span class="sxs-lookup"><span data-stu-id="53408-142">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="53408-143">Membro</span><span class="sxs-lookup"><span data-stu-id="53408-143">Member</span></span>|<span data-ttu-id="53408-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="53408-144">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="53408-145">Habilita a recuperação de um exato `ClassID` para uma função genérica chamando o método [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) com um `COR_PRF_FRAME_INFO` valor retornado pelo retorno de chamada [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-145">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="53408-146">Habilita o rastreamento de argumentos usando o retorno de chamada [FunctionEnter2](functionenter2-function.md) ou o retorno de chamada [FunctionEnter3WithInfo](functionenter3withinfo-function.md) e o método [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-146">Enables argument tracing using the [FunctionEnter2](functionenter2-function.md) callback or the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="53408-147">Habilita o rastreamento de valores de retorno usando o retorno de chamada [FunctionLeave2](functionleave2-function.md) ou o [FunctionLeave3WithInfo](functionleave3withinfo-function.md) retorno de chamada e o método [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-147">Enables tracing of return values by using the [FunctionLeave2](functionleave2-function.md) callback or the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="53408-148">Preterido.</span><span class="sxs-lookup"><span data-stu-id="53408-148">Deprecated.</span></span><br /><br /> <span data-ttu-id="53408-149">Não tem suporte no processo de depuração.</span><span class="sxs-lookup"><span data-stu-id="53408-149">In process debugging is not supported.</span></span> <span data-ttu-id="53408-150">Este sinalizador não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="53408-150">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="53408-151">Preterido.</span><span class="sxs-lookup"><span data-stu-id="53408-151">Deprecated.</span></span><br /><br /> <span data-ttu-id="53408-152">Permite que o criador de perfil obtenha mapas de IL para nativo usando [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span><span class="sxs-lookup"><span data-stu-id="53408-152">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="53408-153">A partir do .NET Framework 2.0, o runtime sempre acompanha os mapas IL para nativo, portanto, esse sinalizador é sempre considerado como definido.</span><span class="sxs-lookup"><span data-stu-id="53408-153">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="53408-154">Informa o runtime que o criador de perfil pode desejar para notificações de alocação do objeto.</span><span class="sxs-lookup"><span data-stu-id="53408-154">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="53408-155">Este sinalizador deve ser definido durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="53408-155">This flag must be set during initialization.</span></span> <span data-ttu-id="53408-156">Ele permite que o criador de perfil Use posteriormente o `COR_PRF_MONITOR_OBJECT_ALLOCATED` sinalizador para receber retornos de chamada de [ObjectAllocated](icorprofilercallback-objectallocated-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-156">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="53408-157">Habilita chamadas para os métodos [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) e [RequestRevert](icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-157">Enables calls to the [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="53408-158">O criador de perfil deve definir este sinalizador na inicialização.</span><span class="sxs-lookup"><span data-stu-id="53408-158">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="53408-159">Se o criador de perfil especificar este sinalizador, também deverá especificar `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span><span class="sxs-lookup"><span data-stu-id="53408-159">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="53408-160">Habilita chamadas para o método [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53408-160">Enables calls to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a><span data-ttu-id="53408-161">Sinalizadores de configuração</span><span class="sxs-lookup"><span data-stu-id="53408-161">Configuration flags</span></span>  
  
|<span data-ttu-id="53408-162">Membro</span><span class="sxs-lookup"><span data-stu-id="53408-162">Member</span></span>|<span data-ttu-id="53408-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="53408-163">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="53408-164">Impede o carregamento de todas as imagens nativas (incluindo imagens aprimoradas do criador de perfil).</span><span class="sxs-lookup"><span data-stu-id="53408-164">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="53408-165">Se este sinalizador e o sinalizador `COR_PRF_USE_PROFILE_IMAGES` estiverem especificados, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` será usado.</span><span class="sxs-lookup"><span data-stu-id="53408-165">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="53408-166">Desabilita todas as conexões embutidas.</span><span class="sxs-lookup"><span data-stu-id="53408-166">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="53408-167">Desabilita todas as otimizações de código.</span><span class="sxs-lookup"><span data-stu-id="53408-167">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="53408-168">Desabilita verificações de transparência de segurança que normalmente são feitas durante a compilação JIT (Just-in-Time) e o carregamento de classe para os conjuntos de confiança total.</span><span class="sxs-lookup"><span data-stu-id="53408-168">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="53408-169">Isso pode facilitar a execução de instrumentação.</span><span class="sxs-lookup"><span data-stu-id="53408-169">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="53408-170">Faz com que a imagem nativa procure imagens aprimoradas para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="53408-170">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="53408-171">Se nenhuma imagem aprimorada para o criador de perfil for encontrada para determinada montagem, o Common Language Runtime (CRL) retornará ao JIT para esse assembly.</span><span class="sxs-lookup"><span data-stu-id="53408-171">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="53408-172">Se este sinalizador e o sinalizador `COR_PRF_DISABLE_ALL_NGEN_IMAGES` estiverem especificados, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` será usado.</span><span class="sxs-lookup"><span data-stu-id="53408-172">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a><span data-ttu-id="53408-173">Sinalizadores compostos</span><span class="sxs-lookup"><span data-stu-id="53408-173">Composite flags</span></span>  
  
|<span data-ttu-id="53408-174">Membro</span><span class="sxs-lookup"><span data-stu-id="53408-174">Member</span></span>|<span data-ttu-id="53408-175">Descrição</span><span class="sxs-lookup"><span data-stu-id="53408-175">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="53408-176">Representa todos os valores de sinalizador `COR_PRF_MONITOR`.</span><span class="sxs-lookup"><span data-stu-id="53408-176">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="53408-177">Representa todos os sinalizadores `COR_PRF_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="53408-177">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="53408-178">A seção de sintaxe indica os sinalizadores individuais que estão presentes nesta bitmask.</span><span class="sxs-lookup"><span data-stu-id="53408-178">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="53408-179">Habilita todos os eventos de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="53408-179">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="53408-180">Representa todos os sinalizadores `COR_PRF_MONITOR` que podem ser definidos apenas durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="53408-180">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="53408-181">A tentativa de alterar qualquer um desses sinalizadores após a inicialização retorna um valor `HRESULT` que indica falha.</span><span class="sxs-lookup"><span data-stu-id="53408-181">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="53408-182">Representa todos os sinalizadores `COR_PRF_MONITOR` que necessitam de imagens aprimoradas por perfil.</span><span class="sxs-lookup"><span data-stu-id="53408-182">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53408-183">Comentários</span><span class="sxs-lookup"><span data-stu-id="53408-183">Remarks</span></span>  
 <span data-ttu-id="53408-184">Um `COR_PRF_MONITOR` valor é usado com os métodos [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) e [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir as notificações de eventos que o Common Language Runtime faz para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="53408-184">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53408-185">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53408-185">Requirements</span></span>  
 <span data-ttu-id="53408-186">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53408-186">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53408-187">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="53408-187">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53408-188">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53408-188">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53408-189">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53408-189">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53408-190">Confira também</span><span class="sxs-lookup"><span data-stu-id="53408-190">See also</span></span>

- [<span data-ttu-id="53408-191">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="53408-191">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="53408-192">Método GetEventMask</span><span class="sxs-lookup"><span data-stu-id="53408-192">GetEventMask Method</span></span>](icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="53408-193">Método SetEventMask</span><span class="sxs-lookup"><span data-stu-id="53408-193">SetEventMask Method</span></span>](icorprofilerinfo-seteventmask-method.md)
