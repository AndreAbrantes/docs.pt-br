---
title: Interface ICorDebugStepper
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: 622fdfa37c93e406950e73941775828ae4b112fa
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379429"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="b336e-102">Interface ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="b336e-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="b336e-103">Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.</span><span class="sxs-lookup"><span data-stu-id="b336e-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b336e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b336e-104">Methods</span></span>  
  
|<span data-ttu-id="b336e-105">Método</span><span class="sxs-lookup"><span data-stu-id="b336e-105">Method</span></span>|<span data-ttu-id="b336e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b336e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b336e-107">Método Deactivate</span><span class="sxs-lookup"><span data-stu-id="b336e-107">Deactivate Method</span></span>](icordebugstepper-deactivate-method.md)|<span data-ttu-id="b336e-108">Faz com que isso `ICorDebugStepper` cancele o comando da última etapa recebido.</span><span class="sxs-lookup"><span data-stu-id="b336e-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="b336e-109">Método IsActive</span><span class="sxs-lookup"><span data-stu-id="b336e-109">IsActive Method</span></span>](icordebugstepper-isactive-method.md)|<span data-ttu-id="b336e-110">Obtém um valor que indica se este `ICorDebugStepper` está executando uma etapa no momento.</span><span class="sxs-lookup"><span data-stu-id="b336e-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="b336e-111">Método SetInterceptMask</span><span class="sxs-lookup"><span data-stu-id="b336e-111">SetInterceptMask Method</span></span>](icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="b336e-112">Define um valor CorDebugIntercept que especifica os tipos de código que são percorridos.</span><span class="sxs-lookup"><span data-stu-id="b336e-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="b336e-113">Método SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="b336e-113">SetRangeIL Method</span></span>](icordebugstepper-setrangeil-method.md)|<span data-ttu-id="b336e-114">Define um valor que indica se as chamadas para [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) passam valores de argumentos relativos ao código nativo ou ao código MSIL (Microsoft Intermediate Language) do método que está sendo percorrido.</span><span class="sxs-lookup"><span data-stu-id="b336e-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="b336e-115">Método SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="b336e-115">SetUnmappedStopMask Method</span></span>](icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="b336e-116">Define um valor CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual a execução será interrompida.</span><span class="sxs-lookup"><span data-stu-id="b336e-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="b336e-117">Método Step</span><span class="sxs-lookup"><span data-stu-id="b336e-117">Step Method</span></span>](icordebugstepper-step-method.md)|<span data-ttu-id="b336e-118">Faz isso `ICorDebugStepper` para uma única etapa por meio de seu thread que o contém e, opcionalmente, para continuar percorrendo por meio de funções que são chamadas dentro do thread.</span><span class="sxs-lookup"><span data-stu-id="b336e-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="b336e-119">Método StepOut</span><span class="sxs-lookup"><span data-stu-id="b336e-119">StepOut Method</span></span>](icordebugstepper-stepout-method.md)|<span data-ttu-id="b336e-120">Faz isso `ICorDebugStepper` para uma única etapa por meio de seu thread que o contém e para concluir quando o quadro atual retorna o controle para o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="b336e-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="b336e-121">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="b336e-121">StepRange Method</span></span>](icordebugstepper-steprange-method.md)|<span data-ttu-id="b336e-122">Faz isso `ICorDebugStepper` para uma única etapa por meio de seu thread que o contém e retorna quando ele atinge o código após o último dos intervalos especificados.</span><span class="sxs-lookup"><span data-stu-id="b336e-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b336e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="b336e-123">Remarks</span></span>  
 <span data-ttu-id="b336e-124">A `ICorDebugStepper` interface atende às seguintes finalidades:</span><span class="sxs-lookup"><span data-stu-id="b336e-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="b336e-125">Ele atua como um identificador entre um comando Step que é emitido e a conclusão desse comando.</span><span class="sxs-lookup"><span data-stu-id="b336e-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="b336e-126">Ele fornece uma interface central para encapsular toda a depuração que pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="b336e-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="b336e-127">Ele fornece uma maneira de cancelar prematuramente uma operação de depuração.</span><span class="sxs-lookup"><span data-stu-id="b336e-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="b336e-128">Pode haver mais de um stepper por thread.</span><span class="sxs-lookup"><span data-stu-id="b336e-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="b336e-129">Por exemplo, um ponto de interrupção pode ser atingido durante a depuração em uma função, e o usuário pode desejar iniciar uma nova operação de depuração dentro dessa função.</span><span class="sxs-lookup"><span data-stu-id="b336e-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="b336e-130">Cabe ao depurador determinar como lidar com essa situação.</span><span class="sxs-lookup"><span data-stu-id="b336e-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="b336e-131">O depurador pode querer cancelar a operação de depuração original ou aninhar as duas operações.</span><span class="sxs-lookup"><span data-stu-id="b336e-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="b336e-132">A `ICorDebugStepper` interface dá suporte a ambas as opções.</span><span class="sxs-lookup"><span data-stu-id="b336e-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="b336e-133">Um stepper poderá migrar entre threads se o Common Language Runtime (CLR) fizer uma chamada de marshaling em vários threads.</span><span class="sxs-lookup"><span data-stu-id="b336e-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b336e-134">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="b336e-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b336e-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b336e-135">Requirements</span></span>  
 <span data-ttu-id="b336e-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b336e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b336e-137">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b336e-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b336e-138">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b336e-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b336e-139">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b336e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b336e-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="b336e-140">See also</span></span>

- [<span data-ttu-id="b336e-141">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b336e-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
