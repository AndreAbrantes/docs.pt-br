---
title: Método ICLROnEventManager::UnregisterActionOnEvent
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
ms.openlocfilehash: 8a9fdcd650e18bb91e2a4e30e5a22fb2a991d25c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703486"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="08fc2-102">Método ICLROnEventManager::UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="08fc2-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="08fc2-103">Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="08fc2-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08fc2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08fc2-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08fc2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08fc2-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="08fc2-106">no Um dos valores de [EClrEvent](eclrevent-enumeration.md) , indicando o evento para o qual cancelar o registro do ponteiro de retorno de chamada descrito por `pAction` .</span><span class="sxs-lookup"><span data-stu-id="08fc2-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="08fc2-107">no Um ponteiro para um objeto [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) que foi passado como um parâmetro para o método [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="08fc2-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08fc2-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="08fc2-108">Return Value</span></span>  
  
|<span data-ttu-id="08fc2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08fc2-109">HRESULT</span></span>|<span data-ttu-id="08fc2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="08fc2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08fc2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="08fc2-111">S_OK</span></span>|<span data-ttu-id="08fc2-112">`UnregisterActionOnEvent`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="08fc2-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="08fc2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08fc2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08fc2-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="08fc2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08fc2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08fc2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08fc2-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="08fc2-116">The call timed out.</span></span>|  
|<span data-ttu-id="08fc2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08fc2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08fc2-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="08fc2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08fc2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08fc2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08fc2-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="08fc2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08fc2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08fc2-121">E_FAIL</span></span>|<span data-ttu-id="08fc2-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="08fc2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08fc2-123">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="08fc2-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08fc2-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="08fc2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08fc2-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08fc2-125">Requirements</span></span>  
 <span data-ttu-id="08fc2-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08fc2-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08fc2-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="08fc2-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08fc2-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08fc2-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08fc2-129">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08fc2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08fc2-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="08fc2-130">See also</span></span>

- [<span data-ttu-id="08fc2-131">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="08fc2-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="08fc2-132">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="08fc2-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="08fc2-133">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="08fc2-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="08fc2-134">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="08fc2-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
