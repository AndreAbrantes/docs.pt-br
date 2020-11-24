---
title: Método IHostSecurityManager::RevertToSelf
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
ms.openlocfilehash: a54c25cb0cae906dc2d030900b9a1e1dbbbb2f1e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680515"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="075c0-102">Método IHostSecurityManager::RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="075c0-102">IHostSecurityManager::RevertToSelf Method</span></span>

<span data-ttu-id="075c0-103">Encerra a representação da identidade do usuário atual e retorna o token do thread original.</span><span class="sxs-lookup"><span data-stu-id="075c0-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="075c0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="075c0-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="075c0-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="075c0-105">Return Value</span></span>  
  
|<span data-ttu-id="075c0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="075c0-106">HRESULT</span></span>|<span data-ttu-id="075c0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="075c0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="075c0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="075c0-108">S_OK</span></span>|<span data-ttu-id="075c0-109">`RevertToSelf` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="075c0-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="075c0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="075c0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="075c0-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="075c0-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="075c0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="075c0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="075c0-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="075c0-113">The call timed out.</span></span>|  
|<span data-ttu-id="075c0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="075c0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="075c0-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="075c0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="075c0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="075c0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="075c0-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="075c0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="075c0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="075c0-118">E_FAIL</span></span>|<span data-ttu-id="075c0-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="075c0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="075c0-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="075c0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="075c0-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="075c0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="075c0-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="075c0-122">Remarks</span></span>  

 <span data-ttu-id="075c0-123">`RevertToSelf` é chamado para retornar ao token de thread original, após uma chamada anterior para o método [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) .</span><span class="sxs-lookup"><span data-stu-id="075c0-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="075c0-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="075c0-124">Requirements</span></span>  

 <span data-ttu-id="075c0-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="075c0-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="075c0-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="075c0-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="075c0-127">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="075c0-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="075c0-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="075c0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="075c0-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="075c0-129">See also</span></span>

- [<span data-ttu-id="075c0-130">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="075c0-130">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="075c0-131">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="075c0-131">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="075c0-132">Método ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="075c0-132">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)
