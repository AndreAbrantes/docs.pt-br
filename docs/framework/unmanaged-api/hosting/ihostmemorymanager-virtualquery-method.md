---
title: "Método IHostMemoryManager::VirtualQuery"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fd893cd92f7e7621aefe59595cfd9905bc77afd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="7135a-102">Método IHostMemoryManager::VirtualQuery</span><span class="sxs-lookup"><span data-stu-id="7135a-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="7135a-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="7135a-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="7135a-104">A implementação do Win32 de `VirtualQuery` recupera informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="7135a-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7135a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7135a-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7135a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7135a-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="7135a-107">[in] Um ponteiro para o endereço na memória virtual a ser consultado.</span><span class="sxs-lookup"><span data-stu-id="7135a-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="7135a-108">[out] Um ponteiro para uma estrutura que contém informações sobre a região de memória especificada.</span><span class="sxs-lookup"><span data-stu-id="7135a-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7135a-109">[in] O tamanho, em bytes, do buffer que `lpBuffer` aponta para.</span><span class="sxs-lookup"><span data-stu-id="7135a-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="7135a-110">[out] Um ponteiro para o número de bytes retornados pelo buffer de informações.</span><span class="sxs-lookup"><span data-stu-id="7135a-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7135a-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7135a-111">Return Value</span></span>  
  
|<span data-ttu-id="7135a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7135a-112">HRESULT</span></span>|<span data-ttu-id="7135a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7135a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7135a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7135a-114">S_OK</span></span>|<span data-ttu-id="7135a-115">`VirtualQuery`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="7135a-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="7135a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7135a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7135a-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7135a-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7135a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7135a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7135a-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="7135a-119">The call timed out.</span></span>|  
|<span data-ttu-id="7135a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7135a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7135a-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7135a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7135a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7135a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7135a-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="7135a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7135a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7135a-124">E_FAIL</span></span>|<span data-ttu-id="7135a-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7135a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7135a-126">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7135a-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7135a-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7135a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7135a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="7135a-128">Remarks</span></span>  
 <span data-ttu-id="7135a-129">`VirtualQuery`Fornece informações sobre um intervalo de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="7135a-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="7135a-130">Esta implementação define o valor de `pResult` parâmetro para o número de bytes retornados no buffer de informações e retorna um valor HRESULT.</span><span class="sxs-lookup"><span data-stu-id="7135a-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="7135a-131">Em Win32 `VirtualQuery` função, o valor de retorno é o tamanho do buffer.</span><span class="sxs-lookup"><span data-stu-id="7135a-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="7135a-132">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="7135a-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7135a-133">A implementação do sistema operacional de `VirtualQuery` não incorrerá em deadlock e pode executar o preenchimento com aleatórios threads suspensos no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="7135a-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="7135a-134">Use muito cuidado ao implementar uma versão hospedada deste método.</span><span class="sxs-lookup"><span data-stu-id="7135a-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7135a-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7135a-135">Requirements</span></span>  
 <span data-ttu-id="7135a-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7135a-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7135a-137">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7135a-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7135a-138">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7135a-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7135a-139">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7135a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7135a-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7135a-140">See Also</span></span>  
 [<span data-ttu-id="7135a-141">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="7135a-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
