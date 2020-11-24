---
title: Método IHostTaskManager::ReverseLeaveRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
ms.openlocfilehash: 8e0981415c03120cc30e6349daced51e79216938
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669959"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="57ff7-102">Método IHostTaskManager::ReverseLeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="57ff7-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>

<span data-ttu-id="57ff7-103">Notifica o host que o controle está deixando o Common Language Runtime (CLR) e inserindo uma função não gerenciada que, por sua vez, foi chamada a partir do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="57ff7-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ff7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57ff7-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="57ff7-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="57ff7-105">Return Value</span></span>  
  
|<span data-ttu-id="57ff7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57ff7-106">HRESULT</span></span>|<span data-ttu-id="57ff7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="57ff7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57ff7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="57ff7-108">S_OK</span></span>|<span data-ttu-id="57ff7-109">`ReverseLeaveRuntime` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="57ff7-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="57ff7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57ff7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57ff7-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="57ff7-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57ff7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57ff7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57ff7-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="57ff7-113">The call timed out.</span></span>|  
|<span data-ttu-id="57ff7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57ff7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57ff7-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="57ff7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57ff7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57ff7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57ff7-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="57ff7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57ff7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57ff7-118">E_FAIL</span></span>|<span data-ttu-id="57ff7-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="57ff7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57ff7-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="57ff7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57ff7-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57ff7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="57ff7-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="57ff7-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="57ff7-123">Não há memória suficiente disponível para concluir a alocação de recursos solicitada.</span><span class="sxs-lookup"><span data-stu-id="57ff7-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57ff7-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="57ff7-124">Remarks</span></span>  

 <span data-ttu-id="57ff7-125">O CLR chama `ReverseLeaveRuntime` para informar ao host que a tarefa em execução no momento está retornando o controle a uma função não gerenciada que, por sua vez, foi chamada a partir de código gerenciado por meio de invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="57ff7-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="57ff7-126">Cada chamada para `ReverseLeaveRuntime` corresponde a uma chamada correspondente para [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="57ff7-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ff7-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57ff7-127">Requirements</span></span>  

 <span data-ttu-id="57ff7-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57ff7-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57ff7-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57ff7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57ff7-130">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57ff7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57ff7-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57ff7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ff7-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="57ff7-132">See also</span></span>

- [<span data-ttu-id="57ff7-133">Método CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="57ff7-133">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="57ff7-134">Método EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="57ff7-134">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="57ff7-135">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="57ff7-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="57ff7-136">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="57ff7-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="57ff7-137">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="57ff7-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="57ff7-138">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="57ff7-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="57ff7-139">Método LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="57ff7-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="57ff7-140">[Um olhar detalhado sobre invocação de plataforma](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="57ff7-140">[A Closer Look at Platform Invoke](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
