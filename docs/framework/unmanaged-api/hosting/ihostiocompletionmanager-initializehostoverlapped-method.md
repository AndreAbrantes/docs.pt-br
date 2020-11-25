---
title: Método IHostIoCompletionManager::InitializeHostOverlapped
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: 397dbbeb0b85cb549a8b5917f977ecb13b3d6539
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720211"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="0d428-102">Método IHostIoCompletionManager::InitializeHostOverlapped</span><span class="sxs-lookup"><span data-stu-id="0d428-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>

<span data-ttu-id="0d428-103">Fornece ao host uma oportunidade de inicializar quaisquer dados personalizados para acrescentar a uma estrutura Win32 `OVERLAPPED` que é usada para solicitações de e/s assíncronas.</span><span class="sxs-lookup"><span data-stu-id="0d428-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d428-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d428-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d428-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d428-105">Parameters</span></span>  

 `pvOverlapped`  
 <span data-ttu-id="0d428-106">no Um ponteiro para a estrutura do Win32 `OVERLAPPED` a ser incluído na solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="0d428-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d428-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="0d428-107">Return Value</span></span>  
  
|<span data-ttu-id="0d428-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d428-108">HRESULT</span></span>|<span data-ttu-id="0d428-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d428-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d428-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d428-110">S_OK</span></span>|<span data-ttu-id="0d428-111">`InitializeHostOverlapped` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="0d428-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="0d428-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0d428-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0d428-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0d428-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0d428-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0d428-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0d428-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0d428-115">The call timed out.</span></span>|  
|<span data-ttu-id="0d428-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0d428-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0d428-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0d428-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0d428-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0d428-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0d428-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="0d428-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0d428-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0d428-120">E_FAIL</span></span>|<span data-ttu-id="0d428-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0d428-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0d428-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="0d428-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0d428-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0d428-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0d428-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0d428-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0d428-125">Não havia memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="0d428-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d428-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d428-126">Remarks</span></span>  

 <span data-ttu-id="0d428-127">As funções da plataforma Windows usam a `OVERLAPPED` estrutura para armazenar o estado para solicitações de e/s assíncronas.</span><span class="sxs-lookup"><span data-stu-id="0d428-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="0d428-128">O CLR chama o `InitializeHostOverlapped` método para dar ao host a oportunidade de acrescentar dados personalizados a uma `OVERLAPPED` instância.</span><span class="sxs-lookup"><span data-stu-id="0d428-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0d428-129">Para chegar ao início do bloco de dados personalizado, os hosts devem definir o deslocamento para o tamanho da `OVERLAPPED` estrutura ( `sizeof(OVERLAPPED)` ).</span><span class="sxs-lookup"><span data-stu-id="0d428-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="0d428-130">Um valor de retorno de E_OUTOFMEMORY indica que o host falhou ao inicializar seus dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="0d428-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="0d428-131">Nesse caso, o CLR relata um erro e falha na chamada.</span><span class="sxs-lookup"><span data-stu-id="0d428-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d428-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d428-132">Requirements</span></span>  

 <span data-ttu-id="0d428-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d428-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d428-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0d428-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d428-135">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d428-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d428-136">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d428-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d428-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d428-137">See also</span></span>

- [<span data-ttu-id="0d428-138">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="0d428-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0d428-139">Método GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="0d428-139">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="0d428-140">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="0d428-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
