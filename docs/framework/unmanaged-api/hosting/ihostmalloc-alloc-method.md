---
title: Método IHostMAlloc::Alloc
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: 5858b03676db0839621b121131ded4da9950ce88
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675120"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="de1e7-102">Método IHostMAlloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="de1e7-102">IHostMAlloc::Alloc Method</span></span>

<span data-ttu-id="de1e7-103">Solicita que o host aloque a quantidade especificada de memória do heap.</span><span class="sxs-lookup"><span data-stu-id="de1e7-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de1e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de1e7-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de1e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de1e7-105">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="de1e7-106">no O tamanho, em bytes, da solicitação de alocação de memória atual.</span><span class="sxs-lookup"><span data-stu-id="de1e7-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="de1e7-107">no Um dos valores de [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) , indicando o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="de1e7-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="de1e7-108">fora Um ponteiro para a memória alocada ou NULL se a solicitação não puder ser concluída.</span><span class="sxs-lookup"><span data-stu-id="de1e7-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de1e7-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="de1e7-109">Return Value</span></span>  
  
|<span data-ttu-id="de1e7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de1e7-110">HRESULT</span></span>|<span data-ttu-id="de1e7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="de1e7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de1e7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="de1e7-112">S_OK</span></span>|<span data-ttu-id="de1e7-113">`Alloc` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="de1e7-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="de1e7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="de1e7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="de1e7-115">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="de1e7-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="de1e7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="de1e7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="de1e7-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="de1e7-117">The call timed out.</span></span>|  
|<span data-ttu-id="de1e7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="de1e7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="de1e7-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="de1e7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="de1e7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="de1e7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="de1e7-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="de1e7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="de1e7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="de1e7-122">E_FAIL</span></span>|<span data-ttu-id="de1e7-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="de1e7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="de1e7-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="de1e7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="de1e7-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="de1e7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="de1e7-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="de1e7-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="de1e7-127">Não havia memória suficiente disponível para concluir a solicitação de alocação.</span><span class="sxs-lookup"><span data-stu-id="de1e7-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de1e7-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="de1e7-128">Remarks</span></span>  

 <span data-ttu-id="de1e7-129">O CLR Obtém um ponteiro de interface para uma `IHostMalloc` instância chamando o método [IHostMemoryManager:: CreateMAlloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de1e7-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de1e7-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de1e7-130">Requirements</span></span>  

 <span data-ttu-id="de1e7-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de1e7-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de1e7-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="de1e7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de1e7-133">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de1e7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de1e7-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de1e7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1e7-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="de1e7-135">See also</span></span>

- [<span data-ttu-id="de1e7-136">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="de1e7-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="de1e7-137">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="de1e7-137">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
