---
title: Método ICLRDebugManager::SetConnectionTasks
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
ms.openlocfilehash: 5df01ac929874d00a5fddda83f532927dc46d67b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719834"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="20372-102">Método ICLRDebugManager::SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="20372-102">ICLRDebugManager::SetConnectionTasks Method</span></span>

<span data-ttu-id="20372-103">Associa uma lista de instâncias [ICLRTask](iclrtask-interface.md) com um identificador e um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="20372-103">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20372-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20372-104">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20372-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20372-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="20372-106">no O identificador específico do host para a conexão com a qual associar a `ppCLRTask` matriz.</span><span class="sxs-lookup"><span data-stu-id="20372-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="20372-107">no O número de membros de `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="20372-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="20372-108">Esse número deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="20372-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="20372-109">no Uma matriz de `ICLRTask` ponteiros para associar à conexão identificada pelo `id` .</span><span class="sxs-lookup"><span data-stu-id="20372-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="20372-110">Essa matriz deve conter pelo menos um membro.</span><span class="sxs-lookup"><span data-stu-id="20372-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20372-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="20372-111">Return Value</span></span>  
  
|<span data-ttu-id="20372-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20372-112">HRESULT</span></span>|<span data-ttu-id="20372-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="20372-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20372-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="20372-114">S_OK</span></span>|<span data-ttu-id="20372-115">`SetConnectionTasks` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="20372-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="20372-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20372-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20372-117">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="20372-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20372-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20372-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20372-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="20372-119">The call timed out.</span></span>|  
|<span data-ttu-id="20372-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20372-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20372-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="20372-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20372-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20372-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20372-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="20372-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20372-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20372-124">E_FAIL</span></span>|<span data-ttu-id="20372-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="20372-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20372-126">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="20372-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20372-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="20372-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="20372-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="20372-128">E_INVALIDARG</span></span>|<span data-ttu-id="20372-129">A [beginconnectização](iclrdebugmanager-beginconnection-method.md) não foi chamada usando esse valor de `id` , ou `dwCount` ou `id` é zero, ou um dos elementos de `ppCLRTask` é nulo.</span><span class="sxs-lookup"><span data-stu-id="20372-129">[BeginConnection](iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20372-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="20372-130">Remarks</span></span>  

 <span data-ttu-id="20372-131">O [ICLRDebugManager](iclrdebugmanager-interface.md) fornece três métodos,, `BeginConnection` `SetConnectionTasks` e [EndConnect](iclrdebugmanager-endconnection-method.md), para associar listas de tarefas com identificadores e nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="20372-131">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="20372-132">Esses três métodos devem ser chamados em uma ordem específica para cada conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="20372-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="20372-133">`BeginConnection` é chamado primeiro para estabelecer uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="20372-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="20372-134">`SetConnectionTasks` é chamado ao lado de fornecer o conjunto de tarefas a ser associado a essa conexão.</span><span class="sxs-lookup"><span data-stu-id="20372-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="20372-135">`EndConnection` é chamado por último para remover a associação entre a lista de tarefas e o identificador e o nome amigável. No entanto, as chamadas para diferentes conexões podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="20372-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20372-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20372-136">Requirements</span></span>  

 <span data-ttu-id="20372-137">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20372-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20372-138">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20372-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20372-139">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20372-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20372-140">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20372-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20372-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="20372-141">See also</span></span>

- [<span data-ttu-id="20372-142">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="20372-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="20372-143">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="20372-143">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="20372-144">Método BeginConnection</span><span class="sxs-lookup"><span data-stu-id="20372-144">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="20372-145">Método EndConnection</span><span class="sxs-lookup"><span data-stu-id="20372-145">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="20372-146">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="20372-146">IHostControl Interface</span></span>](ihostcontrol-interface.md)
