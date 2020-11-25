---
title: Método IHostTaskManager::SetLocale
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 7730c2dddaca98e4cb06cdb381e8a46ff23c97f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699190"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="7f789-102">Método IHostTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="7f789-102">IHostTaskManager::SetLocale Method</span></span>

<span data-ttu-id="7f789-103">Notifica o host de que o Common Language Runtime (CLR) alterou a localidade, ou cultura, na tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="7f789-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f789-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f789-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f789-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f789-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="7f789-106">no O valor do identificador de localidade que mapeia para a cultura geográfica e a linguagem recém atribuídas.</span><span class="sxs-lookup"><span data-stu-id="7f789-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f789-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="7f789-107">Return Value</span></span>  
  
|<span data-ttu-id="7f789-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f789-108">HRESULT</span></span>|<span data-ttu-id="7f789-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f789-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f789-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f789-110">S_OK</span></span>|<span data-ttu-id="7f789-111">`SetLocale` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7f789-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="7f789-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f789-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f789-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7f789-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f789-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f789-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f789-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7f789-115">The call timed out.</span></span>|  
|<span data-ttu-id="7f789-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f789-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f789-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7f789-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f789-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f789-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f789-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="7f789-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f789-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f789-120">E_FAIL</span></span>|<span data-ttu-id="7f789-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7f789-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f789-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="7f789-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f789-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7f789-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7f789-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="7f789-124">E_NOTIMPL</span></span>|<span data-ttu-id="7f789-125">O host não permite que o código de usuário gerenciado modifique a localidade.</span><span class="sxs-lookup"><span data-stu-id="7f789-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f789-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f789-126">Remarks</span></span>  

 <span data-ttu-id="7f789-127">O tempo de execução chama `SetLocale` quando o valor da <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriedade é alterado por código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7f789-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="7f789-128">Esse método fornece uma oportunidade para o host executar qualquer mecanismo que ele possa ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="7f789-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="7f789-129">Se um host não permitir que a localidade seja alterada do código gerenciado ou não implementar um mecanismo para sincronizar as localidades, ele deverá retornar E_NOTIMPL desse método.</span><span class="sxs-lookup"><span data-stu-id="7f789-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f789-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f789-130">Requirements</span></span>  

 <span data-ttu-id="7f789-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f789-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f789-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f789-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f789-133">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f789-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f789-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f789-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f789-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f789-135">See also</span></span>

- [<span data-ttu-id="7f789-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7f789-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7f789-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7f789-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7f789-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7f789-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7f789-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7f789-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="7f789-140">Método SetUILocale</span><span class="sxs-lookup"><span data-stu-id="7f789-140">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)
