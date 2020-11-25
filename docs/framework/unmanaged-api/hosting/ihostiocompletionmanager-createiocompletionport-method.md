---
title: Método IHostIoCompletionManager::CreateIoCompletionPort
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: 0c74e073d55ab7dc98620052a0cfd68c294f7a1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724267"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="74603-102">Método IHostIoCompletionManager::CreateIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="74603-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>

<span data-ttu-id="74603-103">Solicita que o host crie uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="74603-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74603-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74603-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74603-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74603-105">Parameters</span></span>  

 `phPort`  
 <span data-ttu-id="74603-106">fora Um ponteiro para um identificador para a porta de conclusão de e/s recém-criada ou 0 (zero), se a porta não pôde ser criada.</span><span class="sxs-lookup"><span data-stu-id="74603-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74603-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="74603-107">Return Value</span></span>  
  
|<span data-ttu-id="74603-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74603-108">HRESULT</span></span>|<span data-ttu-id="74603-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="74603-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74603-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="74603-110">S_OK</span></span>|<span data-ttu-id="74603-111">`CreateIoCompletionPort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="74603-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="74603-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74603-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74603-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="74603-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74603-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74603-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74603-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="74603-115">The call timed out.</span></span>|  
|<span data-ttu-id="74603-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74603-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74603-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="74603-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74603-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74603-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74603-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="74603-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74603-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74603-120">E_FAIL</span></span>|<span data-ttu-id="74603-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="74603-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74603-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="74603-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74603-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74603-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="74603-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="74603-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="74603-125">Não havia memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="74603-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74603-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="74603-126">Remarks</span></span>  

 <span data-ttu-id="74603-127">O CLR chama o `CreateIoCompletionPort` método para solicitar que o host crie uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="74603-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="74603-128">Ele associa as operações de e/s a essa porta por meio de uma chamada para o método [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="74603-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="74603-129">O host relata o status de volta para o CLR chamando [ICLRIoCompletionManager:: OnComplete](iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="74603-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74603-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74603-130">Requirements</span></span>  

 <span data-ttu-id="74603-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74603-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74603-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="74603-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74603-133">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74603-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74603-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74603-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74603-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="74603-135">See also</span></span>

- [<span data-ttu-id="74603-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="74603-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="74603-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="74603-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
