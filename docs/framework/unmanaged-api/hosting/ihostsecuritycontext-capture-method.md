---
title: Método IHostSecurityContext::Capture
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
ms.openlocfilehash: 40857620e47befce361ff8cb04af527915051df3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804204"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="696cc-102">Método IHostSecurityContext::Capture</span><span class="sxs-lookup"><span data-stu-id="696cc-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="696cc-103">Obtém um clone da instância [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) retornada de uma chamada para [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="696cc-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="696cc-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="696cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="696cc-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="696cc-106">fora Um ponteiro para o endereço de um clone do `IHostSecurityContext` objeto a ser capturado.</span><span class="sxs-lookup"><span data-stu-id="696cc-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="696cc-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="696cc-107">Return Value</span></span>  
  
|<span data-ttu-id="696cc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="696cc-108">HRESULT</span></span>|<span data-ttu-id="696cc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="696cc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="696cc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="696cc-110">S_OK</span></span>|<span data-ttu-id="696cc-111">`Capture`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="696cc-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="696cc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="696cc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="696cc-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="696cc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="696cc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="696cc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="696cc-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="696cc-115">The call timed out.</span></span>|  
|<span data-ttu-id="696cc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="696cc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="696cc-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="696cc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="696cc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="696cc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="696cc-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="696cc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="696cc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="696cc-120">E_FAIL</span></span>|<span data-ttu-id="696cc-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="696cc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="696cc-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="696cc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="696cc-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="696cc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="696cc-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="696cc-124">Remarks</span></span>  
 <span data-ttu-id="696cc-125">O ponteiro de interface retornado de `Capture` é um clone do contexto capturado.</span><span class="sxs-lookup"><span data-stu-id="696cc-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="696cc-126">Quando essas informações são movidas em um ponto de código assíncrono, seu tempo de vida é separado do ponteiro no qual a chamada foi feita.</span><span class="sxs-lookup"><span data-stu-id="696cc-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="696cc-127">Portanto, o ponteiro original pode ser liberado.</span><span class="sxs-lookup"><span data-stu-id="696cc-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="696cc-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="696cc-128">Requirements</span></span>  
 <span data-ttu-id="696cc-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="696cc-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="696cc-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="696cc-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="696cc-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="696cc-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="696cc-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="696cc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696cc-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="696cc-133">See also</span></span>

- [<span data-ttu-id="696cc-134">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="696cc-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="696cc-135">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="696cc-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
