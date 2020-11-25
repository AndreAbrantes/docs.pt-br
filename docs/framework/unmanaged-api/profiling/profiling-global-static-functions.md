---
title: Criando perfil de funções estáticas globais
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 1b0ad42e6b34e99212e112f6a594b0a36b6715e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723071"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="52d83-102">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="52d83-102">Profiling Global Static Functions</span></span>

<span data-ttu-id="52d83-103">Esta seção descreve as funções de API não gerenciadas que a API de criação de perfil usa.</span><span class="sxs-lookup"><span data-stu-id="52d83-103">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52d83-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="52d83-104">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="52d83-105">Funções de criação de perfil .NET Framework versão 1</span><span class="sxs-lookup"><span data-stu-id="52d83-105">.NET Framework version 1 Profiling Functions</span></span>  

 [<span data-ttu-id="52d83-106">Função FunctionEnter</span><span class="sxs-lookup"><span data-stu-id="52d83-106">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="52d83-107">Notifica o criador de perfil que o controle está sendo passado para uma função.</span><span class="sxs-lookup"><span data-stu-id="52d83-107">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="52d83-108">Preterido no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="52d83-108">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="52d83-109">Função FunctionLeave</span><span class="sxs-lookup"><span data-stu-id="52d83-109">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="52d83-110">Notifica o criador de perfil de que uma função está prestes a retornar ao chamador.</span><span class="sxs-lookup"><span data-stu-id="52d83-110">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="52d83-111">Preterido no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="52d83-111">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="52d83-112">Função FunctionTailcall</span><span class="sxs-lookup"><span data-stu-id="52d83-112">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="52d83-113">Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função.</span><span class="sxs-lookup"><span data-stu-id="52d83-113">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="52d83-114">Preterido no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="52d83-114">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="52d83-115">Funções de criação de perfil .NET Framework versão 2</span><span class="sxs-lookup"><span data-stu-id="52d83-115">.NET Framework version 2 Profiling Functions</span></span>  

 [<span data-ttu-id="52d83-116">Função FunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="52d83-116">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="52d83-117">Notifica o criador de perfil de que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usada nos retornos de chamada [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)e [FunctionTailcall2](functiontailcall2-function.md) para essa função.</span><span class="sxs-lookup"><span data-stu-id="52d83-117">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="52d83-118">Também permite que o criador de perfil indique se deseja receber retornos de chamada para essa função</span><span class="sxs-lookup"><span data-stu-id="52d83-118">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="52d83-119">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="52d83-119">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="52d83-120">Notifica o criador de perfil que o controle está sendo passado para uma função e fornece informações sobre o quadro de pilha e os argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="52d83-120">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="52d83-121">Preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="52d83-121">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="52d83-122">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="52d83-122">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="52d83-123">Notifica o criador de perfil de que uma função está prestes a retornar ao chamador e fornece informações sobre o quadro de pilha e o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="52d83-123">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="52d83-124">Preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="52d83-124">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="52d83-125">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="52d83-125">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="52d83-126">Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função e fornece informações sobre o registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="52d83-126">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="52d83-127">Preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="52d83-127">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="52d83-128">Função StackSnapshotCallback</span><span class="sxs-lookup"><span data-stu-id="52d83-128">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="52d83-129">Fornece ao criador de perfil informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante uma movimentação de pilha, que é iniciada pelo método [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="52d83-129">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="52d83-130">Funções de criação de perfil .NET Framework versão 4</span><span class="sxs-lookup"><span data-stu-id="52d83-130">.NET Framework version 4 Profiling Functions</span></span>  

 [<span data-ttu-id="52d83-131">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="52d83-131">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="52d83-132">Notifica o criador de perfil de que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usada nos retornos de chamada [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)e [FunctionTailcall3](functiontailcall3-function.md)ou[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) para essa função.</span><span class="sxs-lookup"><span data-stu-id="52d83-132">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="52d83-133">Também permite que o criador de perfil indique se deseja receber retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="52d83-133">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="52d83-134">`FunctionIDMapper2` estende a função [FunctionIDMapper](functionidmapper-function.md) com um `clientData` parâmetro, que os profileres podem usar para fazer a ambiguidade entre os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="52d83-134">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="52d83-135">Função FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="52d83-135">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="52d83-136">Notifica o criador de perfil que o controle está sendo passado para uma função.</span><span class="sxs-lookup"><span data-stu-id="52d83-136">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="52d83-137">Função FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="52d83-137">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="52d83-138">Notifica o criador de perfil que o controle está sendo passado para uma função e fornece um identificador que pode ser passado para [ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) para recuperar o quadro de pilha e os argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="52d83-138">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="52d83-139">Função FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="52d83-139">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="52d83-140">Notifica o criador de perfil que o controle está sendo retornado de uma função.</span><span class="sxs-lookup"><span data-stu-id="52d83-140">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="52d83-141">Função FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="52d83-141">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="52d83-142">Notifica o criador de perfil que o controle está sendo retornado de uma função e fornece um identificador que pode ser passado para [ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) para recuperar o quadro de pilha e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="52d83-142">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="52d83-143">Função FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="52d83-143">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="52d83-144">Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função.</span><span class="sxs-lookup"><span data-stu-id="52d83-144">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="52d83-145">Função FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="52d83-145">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="52d83-146">Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função e fornece um identificador que pode ser passado para [ICorProfilerInfo3:: GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) para recuperar o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="52d83-146">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52d83-147">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="52d83-147">Related Sections</span></span>  

 [<span data-ttu-id="52d83-148">Visão geral da criação de perfil</span><span class="sxs-lookup"><span data-stu-id="52d83-148">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="52d83-149">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="52d83-149">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="52d83-150">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="52d83-150">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="52d83-151">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="52d83-151">Profiling Structures</span></span>](profiling-structures.md)
