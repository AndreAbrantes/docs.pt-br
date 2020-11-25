---
title: Método IHostTaskManager::BeginDelayAbort
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: f72cc15904d098e159dd7f75f673d43ae987998d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727322"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="9fbba-102">Método IHostTaskManager::BeginDelayAbort</span><span class="sxs-lookup"><span data-stu-id="9fbba-102">IHostTaskManager::BeginDelayAbort Method</span></span>

<span data-ttu-id="9fbba-103">Notifica o host de que o código gerenciado está entrando em um período no qual a tarefa atual não deve ser anulada.</span><span class="sxs-lookup"><span data-stu-id="9fbba-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fbba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fbba-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9fbba-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9fbba-105">Return Value</span></span>  
  
|<span data-ttu-id="9fbba-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9fbba-106">HRESULT</span></span>|<span data-ttu-id="9fbba-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fbba-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9fbba-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9fbba-108">S_OK</span></span>|<span data-ttu-id="9fbba-109">`BeginDelayAbort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9fbba-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="9fbba-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9fbba-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9fbba-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9fbba-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9fbba-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9fbba-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9fbba-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9fbba-113">The call timed out.</span></span>|  
|<span data-ttu-id="9fbba-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9fbba-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9fbba-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9fbba-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9fbba-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9fbba-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9fbba-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9fbba-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9fbba-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9fbba-118">E_FAIL</span></span>|<span data-ttu-id="9fbba-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9fbba-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9fbba-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9fbba-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9fbba-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9fbba-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9fbba-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="9fbba-122">E_UNEXPECTED</span></span>|<span data-ttu-id="9fbba-123">`BeginDelayAbort` Já foi chamado, mas a chamada correspondente a [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) ainda não foi recebida.</span><span class="sxs-lookup"><span data-stu-id="9fbba-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fbba-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="9fbba-124">Remarks</span></span>  

 <span data-ttu-id="9fbba-125">O host não deve abortar a tarefa atual até que `EndDelayAbort` seja chamado.</span><span class="sxs-lookup"><span data-stu-id="9fbba-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="9fbba-126">Se outra chamada para `BeginDelayAbort` for feita sem uma chamada intermediária para `EndDelayAbort` , o host deverá retornar E_UNEXPECTED de `BeginDelayAbort` e não deverá executar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="9fbba-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fbba-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fbba-127">Requirements</span></span>  

 <span data-ttu-id="9fbba-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fbba-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fbba-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9fbba-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fbba-130">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fbba-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fbba-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fbba-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fbba-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="9fbba-132">See also</span></span>

- [<span data-ttu-id="9fbba-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="9fbba-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9fbba-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="9fbba-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9fbba-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="9fbba-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
