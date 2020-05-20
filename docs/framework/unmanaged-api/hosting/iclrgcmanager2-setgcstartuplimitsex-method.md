---
title: Método ICLRGCManager2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
ms.openlocfilehash: f71c3b738d8e1f1670ac870d5e8c23ea9182d924
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703977"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="9ffff-102">Método ICLRGCManager2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="9ffff-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="9ffff-103">Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9ffff-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ffff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ffff-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ffff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ffff-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="9ffff-106">no O tamanho especificado de um segmento de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9ffff-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="9ffff-107">O tamanho mínimo do segmento é 4 MB.</span><span class="sxs-lookup"><span data-stu-id="9ffff-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="9ffff-108">Os segmentos podem ser aumentados em incrementos de 1 MB ou mais.</span><span class="sxs-lookup"><span data-stu-id="9ffff-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="9ffff-109">no O tamanho máximo especificado para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="9ffff-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="9ffff-110">O tamanho mínimo de 0 de geração é 64 KB.</span><span class="sxs-lookup"><span data-stu-id="9ffff-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ffff-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9ffff-111">Return Value</span></span>  
  
|<span data-ttu-id="9ffff-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ffff-112">HRESULT</span></span>|<span data-ttu-id="9ffff-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ffff-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ffff-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ffff-114">S_OK</span></span>|<span data-ttu-id="9ffff-115">`SetGCStartupLimitsEx`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9ffff-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="9ffff-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ffff-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ffff-117">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9ffff-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ffff-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9ffff-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9ffff-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9ffff-119">The call timed out.</span></span>|  
|<span data-ttu-id="9ffff-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ffff-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9ffff-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9ffff-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9ffff-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9ffff-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9ffff-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9ffff-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9ffff-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ffff-124">E_FAIL</span></span>|<span data-ttu-id="9ffff-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9ffff-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ffff-126">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="9ffff-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ffff-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9ffff-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ffff-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ffff-128">Remarks</span></span>  
 <span data-ttu-id="9ffff-129">Os valores que `SetGCStartupLimitsEx` conjuntos só podem ser especificados antes do host ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="9ffff-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="9ffff-130">As chamadas posteriores para `SetGCStartupLimitsEx` são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="9ffff-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="9ffff-131">Para definir qualquer parâmetro sem afetar o outro, especifique 0 (zero) para o parâmetro que você não deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="9ffff-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ffff-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ffff-132">Requirements</span></span>  
 <span data-ttu-id="9ffff-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ffff-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ffff-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9ffff-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ffff-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9ffff-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ffff-136">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ffff-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ffff-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="9ffff-137">See also</span></span>

- [<span data-ttu-id="9ffff-138">Gerenciamento automático de memória</span><span class="sxs-lookup"><span data-stu-id="9ffff-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="9ffff-139">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="9ffff-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="9ffff-140">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9ffff-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="9ffff-141">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="9ffff-141">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)
