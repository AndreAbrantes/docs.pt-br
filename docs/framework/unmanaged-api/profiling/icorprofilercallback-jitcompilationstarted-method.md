---
title: Método ICorProfilerCallback::JITCompilationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: e05cb944ea4f3a9ca718dc22c6cd726b6a516ea9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866228"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="2302c-102">Método ICorProfilerCallback::JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="2302c-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="2302c-103">Notifica o criador de perfil de que o compilador JIT (just-in-time) começou a compilar uma função.</span><span class="sxs-lookup"><span data-stu-id="2302c-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2302c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2302c-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2302c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2302c-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2302c-106">no A ID da função para a qual a compilação está sendo iniciada.</span><span class="sxs-lookup"><span data-stu-id="2302c-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="2302c-107">no Um valor que indica ao criador de perfil se o bloqueio afetará a operação do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2302c-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="2302c-108">O valor será `true` se o bloqueio puder fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="2302c-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="2302c-109">Embora um valor de `true` não danifique o tempo de execução, ele pode distorcer os resultados de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="2302c-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2302c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2302c-110">Remarks</span></span>  
 <span data-ttu-id="2302c-111">É possível receber mais de um par de chamadas `JITCompilationStarted` e [ICorProfilerCallback:: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) para cada função devido à maneira como o tempo de execução manipula construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="2302c-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="2302c-112">Por exemplo, o tempo de execução inicia o método A de compilação JIT a, mas o construtor de classe para a classe B precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="2302c-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="2302c-113">Portanto, o tempo de execução JIT compila o construtor para a classe B e o executa.</span><span class="sxs-lookup"><span data-stu-id="2302c-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="2302c-114">Enquanto o Construtor está em execução, ele faz uma chamada para o método A, o que faz com que o método A seja compilado em JIT novamente.</span><span class="sxs-lookup"><span data-stu-id="2302c-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="2302c-115">Nesse cenário, a primeira compilação JIT do método A é interrompida.</span><span class="sxs-lookup"><span data-stu-id="2302c-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="2302c-116">No entanto, ambas as tentativas de compilação JIT do método A são relatadas com eventos de compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="2302c-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="2302c-117">Se o criador de perfil substituir o código MSIL (Microsoft Intermediate Language) para o método A chamando o método [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) , ele deverá fazer isso para ambos os eventos `JITCompilationStarted`, mas poderá usar o mesmo bloco MSIL para ambos.</span><span class="sxs-lookup"><span data-stu-id="2302c-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="2302c-118">Os profileres devem dar suporte à sequência de retornos de chamada JIT nos casos em que dois threads estão realizando retornos de chamada simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2302c-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="2302c-119">Por exemplo, thread A chama `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="2302c-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="2302c-120">No entanto, antes do thread A chamar `JITCompilationFinished`, thread B chama [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID da função do retorno de chamada `JITCompilationStarted` do thread A.</span><span class="sxs-lookup"><span data-stu-id="2302c-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="2302c-121">Pode parecer que a ID da função ainda não deve ser válida porque uma chamada para `JITCompilationFinished` ainda não tinha sido recebida pelo criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="2302c-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="2302c-122">No entanto, em um caso como este, a ID da função é válida.</span><span class="sxs-lookup"><span data-stu-id="2302c-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2302c-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2302c-123">Requirements</span></span>  
 <span data-ttu-id="2302c-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2302c-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2302c-125">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2302c-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2302c-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2302c-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2302c-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2302c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2302c-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="2302c-128">See also</span></span>

- [<span data-ttu-id="2302c-129">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="2302c-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2302c-130">Método JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="2302c-130">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
