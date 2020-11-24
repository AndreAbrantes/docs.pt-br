---
title: Método IHostIoCompletionManager::GetMinThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: d321ce08edf4780fc5f26ac627849b9129c2f283
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673205"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="bb78e-102">Método IHostIoCompletionManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="bb78e-102">IHostIoCompletionManager::GetMinThreads Method</span></span>

<span data-ttu-id="bb78e-103">Obtém o número mínimo de threads que o host fornece para processar solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="bb78e-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb78e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb78e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb78e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb78e-105">Parameters</span></span>  

 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="bb78e-106">fora Um ponteiro para o número mínimo de threads que o host fornece para processar solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="bb78e-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb78e-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="bb78e-107">Return Value</span></span>  
  
|<span data-ttu-id="bb78e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb78e-108">HRESULT</span></span>|<span data-ttu-id="bb78e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb78e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb78e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb78e-110">S_OK</span></span>|<span data-ttu-id="bb78e-111">`GetMinThreads` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bb78e-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="bb78e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb78e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb78e-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bb78e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb78e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb78e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb78e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bb78e-115">The call timed out.</span></span>|  
|<span data-ttu-id="bb78e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb78e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb78e-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bb78e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb78e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb78e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb78e-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="bb78e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb78e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb78e-120">E_FAIL</span></span>|<span data-ttu-id="bb78e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bb78e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb78e-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="bb78e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb78e-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bb78e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bb78e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="bb78e-124">E_NOTIMPL</span></span>|<span data-ttu-id="bb78e-125">O host não fornece uma implementação de `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="bb78e-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb78e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb78e-126">Remarks</span></span>  

 <span data-ttu-id="bb78e-127">Um host pode querer um controle exclusivo sobre o número de threads alocados para solicitações de e/s de serviço, por motivos como implementação, desempenho ou escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="bb78e-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="bb78e-128">Por esse motivo, o host não precisa implementar `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="bb78e-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="bb78e-129">Nesse caso, o host deve retornar E_NOTIMPL desse método.</span><span class="sxs-lookup"><span data-stu-id="bb78e-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb78e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb78e-130">Requirements</span></span>  

 <span data-ttu-id="bb78e-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb78e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb78e-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bb78e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb78e-133">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb78e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb78e-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb78e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb78e-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="bb78e-135">See also</span></span>

- [<span data-ttu-id="bb78e-136">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="bb78e-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="bb78e-137">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="bb78e-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
