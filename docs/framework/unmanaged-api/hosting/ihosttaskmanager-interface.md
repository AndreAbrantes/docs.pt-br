---
title: Interface IHostTaskManager
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: deb14d291bfd511e8f3534f3c5e32787c259c5e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673105"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="108ff-102">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="108ff-102">IHostTaskManager Interface</span></span>

<span data-ttu-id="108ff-103">Fornece métodos que permitem que o Common Language Runtime (CLR) trabalhe com tarefas por meio do host em vez de usar as funções de fibra ou de Threading do sistema operacional padrão.</span><span class="sxs-lookup"><span data-stu-id="108ff-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="108ff-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="108ff-104">Methods</span></span>  
  
|<span data-ttu-id="108ff-105">Método</span><span class="sxs-lookup"><span data-stu-id="108ff-105">Method</span></span>|<span data-ttu-id="108ff-106">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="108ff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="108ff-107">Método BeginDelayAbort</span><span class="sxs-lookup"><span data-stu-id="108ff-107">BeginDelayAbort Method</span></span>](ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="108ff-108">Notifica o host de que o código gerenciado está entrando em um período no qual a tarefa atual não deve ser anulada.</span><span class="sxs-lookup"><span data-stu-id="108ff-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="108ff-109">Método BeginThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="108ff-109">BeginThreadAffinity Method</span></span>](ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="108ff-110">Notifica o host de que o código gerenciado está entrando em um período no qual a tarefa atual não deve ser movida para outro thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="108ff-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="108ff-111">Método CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="108ff-111">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="108ff-112">Permite que o host especifique se o Common Language Runtime pode embutir a chamada especificada para uma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="108ff-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="108ff-113">Método CreateTask</span><span class="sxs-lookup"><span data-stu-id="108ff-113">CreateTask Method</span></span>](ihosttaskmanager-createtask-method.md)|<span data-ttu-id="108ff-114">Solicita que o host crie uma nova tarefa.</span><span class="sxs-lookup"><span data-stu-id="108ff-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="108ff-115">Método EndDelayAbort</span><span class="sxs-lookup"><span data-stu-id="108ff-115">EndDelayAbort Method</span></span>](ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="108ff-116">Notifica o host de que o código gerenciado está saindo do período no qual a tarefa atual não deve ser anulada, seguindo uma chamada anterior para `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="108ff-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="108ff-117">Método EndThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="108ff-117">EndThreadAffinity Method</span></span>](ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="108ff-118">Notifica o host de que o código gerenciado está saindo do período no qual a tarefa atual não deve ser movida para outro thread do sistema operacional, seguindo uma chamada anterior para `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="108ff-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="108ff-119">Método EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="108ff-119">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="108ff-120">Notifica o host de que uma chamada para um método não gerenciado, como um método de invocação de plataforma, está retornando o controle de execução para o CLR.</span><span class="sxs-lookup"><span data-stu-id="108ff-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="108ff-121">Método GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="108ff-121">GetCurrentTask Method</span></span>](ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="108ff-122">Obtém um ponteiro de interface para a tarefa que está atualmente em execução no thread do sistema operacional do qual essa chamada é feita.</span><span class="sxs-lookup"><span data-stu-id="108ff-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="108ff-123">Método GetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="108ff-123">GetStackGuarantee Method</span></span>](ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="108ff-124">Obtém a quantidade de espaço de pilha que tem garantia de disponibilidade após a conclusão de uma operação de pilha, mas antes do fechamento de um processo.</span><span class="sxs-lookup"><span data-stu-id="108ff-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="108ff-125">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="108ff-125">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="108ff-126">Notifica o host que o código gerenciado está prestes a fazer uma chamada para uma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="108ff-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="108ff-127">Método ReverseEnterRuntime</span><span class="sxs-lookup"><span data-stu-id="108ff-127">ReverseEnterRuntime Method</span></span>](ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="108ff-128">Notifica o host de que uma chamada está sendo feita no Common Language Runtime (CLR) de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="108ff-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="108ff-129">Método ReverseLeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="108ff-129">ReverseLeaveRuntime Method</span></span>](ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="108ff-130">Notifica o host que o controle está deixando o CLR e inserindo uma função não gerenciada que, por sua vez, foi chamada a partir do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="108ff-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="108ff-131">Método SetCLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="108ff-131">SetCLRTaskManager Method</span></span>](ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="108ff-132">Fornece ao host um ponteiro de interface para uma instância [ICLRTaskManager](iclrtaskmanager-interface.md) implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="108ff-132">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="108ff-133">Método SetLocale</span><span class="sxs-lookup"><span data-stu-id="108ff-133">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="108ff-134">Notifica o host de que o CLR alterou a localidade na tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="108ff-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="108ff-135">Método SetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="108ff-135">SetStackGuarantee Method</span></span>](ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="108ff-136">Reservado apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="108ff-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="108ff-137">Método SetUILocale</span><span class="sxs-lookup"><span data-stu-id="108ff-137">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="108ff-138">Notifica o host de que a localidade da interface do usuário foi alterada na tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="108ff-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="108ff-139">Método Sleep</span><span class="sxs-lookup"><span data-stu-id="108ff-139">Sleep Method</span></span>](ihosttaskmanager-sleep-method.md)|<span data-ttu-id="108ff-140">Notifica o host que a tarefa atual vai suspender.</span><span class="sxs-lookup"><span data-stu-id="108ff-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="108ff-141">Método SwitchToTask</span><span class="sxs-lookup"><span data-stu-id="108ff-141">SwitchToTask Method</span></span>](ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="108ff-142">Notifica o host de que ele deve desativar a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="108ff-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="108ff-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="108ff-143">Remarks</span></span>  

 <span data-ttu-id="108ff-144">`IHostTaskManager` permite que o CLR crie e gerencie tarefas, para fornecer ganchos para o host tomar uma ação quando o controle transfere de um código gerenciado para não gerenciado e vice-versa, e para especificar determinadas ações que o host pode e não pode executar durante a execução do código.</span><span class="sxs-lookup"><span data-stu-id="108ff-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="108ff-145">Requisitos</span><span class="sxs-lookup"><span data-stu-id="108ff-145">Requirements</span></span>  

 <span data-ttu-id="108ff-146">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="108ff-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="108ff-147">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="108ff-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="108ff-148">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="108ff-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="108ff-149">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="108ff-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108ff-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="108ff-150">See also</span></span>

- [<span data-ttu-id="108ff-151">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="108ff-151">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="108ff-152">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="108ff-152">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="108ff-153">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="108ff-153">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="108ff-154">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="108ff-154">Hosting Interfaces</span></span>](hosting-interfaces.md)
