---
title: Método IHostMAlloc::Free
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: 1dd5ed4c556a5a4d4425a9c0730cebf22ff1785b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804617"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="26ae5-102">Método IHostMAlloc::Free</span><span class="sxs-lookup"><span data-stu-id="26ae5-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="26ae5-103">Libera a memória que foi alocada usando a função de [alocação](ihostmalloc-alloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="26ae5-103">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26ae5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26ae5-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26ae5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26ae5-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="26ae5-106">no Um ponteiro para a memória a ser liberada.</span><span class="sxs-lookup"><span data-stu-id="26ae5-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26ae5-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="26ae5-107">Return Value</span></span>  
  
|<span data-ttu-id="26ae5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26ae5-108">HRESULT</span></span>|<span data-ttu-id="26ae5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="26ae5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26ae5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="26ae5-110">S_OK</span></span>|<span data-ttu-id="26ae5-111">`Free`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="26ae5-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="26ae5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26ae5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26ae5-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="26ae5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26ae5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26ae5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26ae5-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="26ae5-115">The call timed out.</span></span>|  
|<span data-ttu-id="26ae5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26ae5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26ae5-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="26ae5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26ae5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26ae5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26ae5-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="26ae5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26ae5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26ae5-120">E_FAIL</span></span>|<span data-ttu-id="26ae5-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="26ae5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26ae5-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="26ae5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26ae5-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="26ae5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="26ae5-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="26ae5-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="26ae5-125">Foi feita uma tentativa de liberar memória que não foi alocada por meio do host.</span><span class="sxs-lookup"><span data-stu-id="26ae5-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26ae5-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="26ae5-126">Remarks</span></span>  
 <span data-ttu-id="26ae5-127">Se o `pMem` parâmetro se referir a uma região de memória que não foi alocada usando uma chamada para `Alloc` , o host deverá retornar HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="26ae5-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26ae5-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26ae5-128">Requirements</span></span>  
 <span data-ttu-id="26ae5-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26ae5-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26ae5-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26ae5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26ae5-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26ae5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26ae5-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26ae5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ae5-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="26ae5-133">See also</span></span>

- [<span data-ttu-id="26ae5-134">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="26ae5-134">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="26ae5-135">Interface IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="26ae5-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
