---
title: Método ICLRDebugManager::IsDebuggerAttached
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: a21391f52a27e7f7a3abe533499c6b2581ec4a73
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615727"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="d70e1-102">Método ICLRDebugManager::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="d70e1-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="d70e1-103">Obtém um valor que indica se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="d70e1-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d70e1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d70e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d70e1-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="d70e1-106">[fora] `true` se um depurador estiver anexado ao processo; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="d70e1-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d70e1-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d70e1-107">Return Value</span></span>  
  
|<span data-ttu-id="d70e1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d70e1-108">HRESULT</span></span>|<span data-ttu-id="d70e1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d70e1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d70e1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d70e1-110">S_OK</span></span>|<span data-ttu-id="d70e1-111">`IsDebuggerAttached`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d70e1-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="d70e1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d70e1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d70e1-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d70e1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d70e1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d70e1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d70e1-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d70e1-115">The call timed out.</span></span>|  
|<span data-ttu-id="d70e1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d70e1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d70e1-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d70e1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d70e1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d70e1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d70e1-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="d70e1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d70e1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d70e1-120">E_FAIL</span></span>|<span data-ttu-id="d70e1-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d70e1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d70e1-122">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="d70e1-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d70e1-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d70e1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d70e1-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="d70e1-124">Remarks</span></span>  
 <span data-ttu-id="d70e1-125">`IsDebuggerAttached`permite que o host consulte o CLR para determinar se um depurador está anexado ao processo.</span><span class="sxs-lookup"><span data-stu-id="d70e1-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70e1-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d70e1-126">Requirements</span></span>  
 <span data-ttu-id="d70e1-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d70e1-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d70e1-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d70e1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d70e1-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d70e1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d70e1-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d70e1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70e1-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="d70e1-131">See also</span></span>

- [<span data-ttu-id="d70e1-132">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="d70e1-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d70e1-133">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="d70e1-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="d70e1-134">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="d70e1-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)
