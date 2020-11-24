---
title: Método ICLRSyncManager::DeleteRWLockOwnerIterator
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: db651e3fe51f90b84449874f2c60a12050b0350e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687106"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="66707-102">Método ICLRSyncManager::DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="66707-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>

<span data-ttu-id="66707-103">Solicita que o Common Language Runtime (CLR) destrua um iterador criado por uma chamada para [ICLRSyncManager:: CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="66707-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66707-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66707-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66707-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66707-105">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="66707-106">no O iterador criado usando uma chamada para `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="66707-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66707-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="66707-107">Return Value</span></span>  
  
|<span data-ttu-id="66707-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66707-108">HRESULT</span></span>|<span data-ttu-id="66707-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="66707-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66707-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="66707-110">S_OK</span></span>|<span data-ttu-id="66707-111">`DeleteRWLockOwnerIterator` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="66707-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="66707-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="66707-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="66707-113">O CLR não foi carregado em um processo ou está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="66707-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="66707-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="66707-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="66707-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="66707-115">The call timed out.</span></span>|  
|<span data-ttu-id="66707-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="66707-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="66707-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="66707-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="66707-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="66707-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="66707-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="66707-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="66707-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="66707-120">E_FAIL</span></span>|<span data-ttu-id="66707-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="66707-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="66707-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="66707-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="66707-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="66707-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66707-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="66707-124">Remarks</span></span>  

 <span data-ttu-id="66707-125">O host pode chamar esse método e `CreateRWLockOwnerIterator` garantir que sua implementação de Threading permaneça sincronizada.</span><span class="sxs-lookup"><span data-stu-id="66707-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66707-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66707-126">Requirements</span></span>  

 <span data-ttu-id="66707-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66707-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66707-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="66707-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66707-129">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66707-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66707-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66707-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66707-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="66707-131">See also</span></span>

- [<span data-ttu-id="66707-132">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="66707-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="66707-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="66707-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
