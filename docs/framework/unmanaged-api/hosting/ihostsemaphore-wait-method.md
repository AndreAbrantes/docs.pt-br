---
title: Método IHostSemaphore::Wait
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
ms.openlocfilehash: 69b2338e6992c386a3cd34a632d69b73a67f14fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682998"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="2c9f9-102">Método IHostSemaphore::Wait</span><span class="sxs-lookup"><span data-stu-id="2c9f9-102">IHostSemaphore::Wait Method</span></span>

<span data-ttu-id="2c9f9-103">Faz com que a instância de [IHostSemaphore](ihostsemaphore-interface.md) atual aguarde até que ela seja propriedade ou a quantidade especificada de tempo decorre.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-103">Causes the current [IHostSemaphore](ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c9f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c9f9-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c9f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c9f9-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="2c9f9-106">no O número de milissegundos a aguardar antes de retornar, se a `IHostSemaphore` instância atual não pertence.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="2c9f9-107">no Um dos valores de [WAIT_OPTION](wait-option-enumeration.md) , especificando a ação que o host deve executar se essa operação bloquear.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c9f9-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="2c9f9-108">Return Value</span></span>  
  
|<span data-ttu-id="2c9f9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c9f9-109">HRESULT</span></span>|<span data-ttu-id="2c9f9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c9f9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c9f9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c9f9-111">S_OK</span></span>|<span data-ttu-id="2c9f9-112">`Wait` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="2c9f9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c9f9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c9f9-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c9f9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c9f9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c9f9-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-116">The call timed out.</span></span>|  
|<span data-ttu-id="2c9f9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c9f9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c9f9-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c9f9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c9f9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c9f9-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c9f9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c9f9-121">E_FAIL</span></span>|<span data-ttu-id="2c9f9-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c9f9-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c9f9-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2c9f9-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="2c9f9-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="2c9f9-126">O host detectou um deadlock durante o intervalo de espera e escolheu a `IHostSemaphore` instância atual como uma vítima de deadlock.</span><span class="sxs-lookup"><span data-stu-id="2c9f9-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c9f9-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c9f9-127">Requirements</span></span>  

 <span data-ttu-id="2c9f9-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c9f9-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c9f9-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2c9f9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c9f9-130">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c9f9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c9f9-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c9f9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c9f9-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c9f9-132">See also</span></span>

- [<span data-ttu-id="2c9f9-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="2c9f9-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2c9f9-134">Interface IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="2c9f9-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="2c9f9-135">Interface IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="2c9f9-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="2c9f9-136">Interface IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="2c9f9-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="2c9f9-137">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="2c9f9-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
