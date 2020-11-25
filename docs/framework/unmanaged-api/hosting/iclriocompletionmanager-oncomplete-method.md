---
title: Método ICLRIoCompletionManager::OnComplete
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: 15119974acf74b49669e5ffbee59fbff9e5c84c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714088"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="f6b7e-102">Método ICLRIoCompletionManager::OnComplete</span><span class="sxs-lookup"><span data-stu-id="f6b7e-102">ICLRIoCompletionManager::OnComplete Method</span></span>

<span data-ttu-id="f6b7e-103">Notifica o Common Language Runtime (CLR) do status de uma solicitação de e/s que foi feita usando uma chamada para o método [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f6b7e-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6b7e-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6b7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6b7e-105">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="f6b7e-106">no Um valor HRESULT que indica o status da operação de associação.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="f6b7e-107">S_OK indica que a operação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="f6b7e-108">HOST_E_INTERRUPTED indica que a chamada foi encerrada antes da conclusão.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="f6b7e-109">E_FAIL indica que ocorreu uma falha catastrófica desconhecida e irrecuperável.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="f6b7e-110">no O número de bytes transferidos durante o processamento da solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="f6b7e-111">no Um ponteiro para a `OVERLAPPED` estrutura que foi passada para a chamada para o `IHostIoCompletionManager::Bind` método.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6b7e-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="f6b7e-112">Return Value</span></span>  
  
|<span data-ttu-id="f6b7e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6b7e-113">HRESULT</span></span>|<span data-ttu-id="f6b7e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6b7e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6b7e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6b7e-115">S_OK</span></span>|<span data-ttu-id="f6b7e-116">`OnComplete` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="f6b7e-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6b7e-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6b7e-118">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6b7e-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6b7e-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6b7e-120">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-120">The call timed out.</span></span>|  
|<span data-ttu-id="f6b7e-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6b7e-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6b7e-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6b7e-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6b7e-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6b7e-124">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6b7e-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6b7e-125">E_FAIL</span></span>|<span data-ttu-id="f6b7e-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6b7e-127">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f6b7e-128">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6b7e-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6b7e-129">Remarks</span></span>  

 <span data-ttu-id="f6b7e-130">Se o host implementar uma abstração de conclusão de e/s, o CLR fará solicitações de e/s por meio do host usando métodos de [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f6b7e-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="f6b7e-131">O host então chama o `OnComplete` método para notificar o tempo de execução do resultado de tais solicitações.</span><span class="sxs-lookup"><span data-stu-id="f6b7e-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6b7e-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6b7e-132">Requirements</span></span>  

 <span data-ttu-id="f6b7e-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6b7e-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6b7e-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f6b7e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6b7e-135">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6b7e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6b7e-136">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6b7e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b7e-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="f6b7e-137">See also</span></span>

- [<span data-ttu-id="f6b7e-138">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="f6b7e-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="f6b7e-139">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="f6b7e-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="f6b7e-140">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="f6b7e-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
