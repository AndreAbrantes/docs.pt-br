---
title: Método ICLRControl::GetCLRManager
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
ms.openlocfilehash: d18b3a5c06ac0d3a86f7823f3b140c76c6c9a746
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728349"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="04a98-102">Método ICLRControl::GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="04a98-102">ICLRControl::GetCLRManager Method</span></span>

<span data-ttu-id="04a98-103">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador que o host pode usar para configurar o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="04a98-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04a98-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04a98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04a98-105">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="04a98-106">no O `IID` do tipo de Gerenciador a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="04a98-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="04a98-107">Há `IID` suporte para os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="04a98-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="04a98-108">IID_ICLRDebugManager: Especifica que `ppObject` será do tipo [ICLRDebugManager](iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="04a98-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="04a98-109">IID_ICLRErrorReportingManager: Especifica que `ppObject` será do tipo [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="04a98-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="04a98-110">IID_ICLRGCManager: Especifica que `ppObject` será do tipo [ICLRGCManager](iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="04a98-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="04a98-111">IID_ICLRHostProtectionManager: Especifica que `ppObject` será do tipo [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="04a98-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="04a98-112">IID_ICLROnEventManager: Especifica que `ppObject` será do tipo [ICLROnEventManager](iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="04a98-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="04a98-113">IID_ICLRPolicyManager: Especifica que `ppObject` será do tipo [ICLRPolicyManager](iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="04a98-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="04a98-114">IID_ICLRTaskManager: Especifica que `ppObject` será do tipo [ICLRTaskManager](iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="04a98-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="04a98-115">fora Um ponteiro de interface para o Gerenciador solicitado, ou NULL, se um tipo de Gerenciador inválido foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="04a98-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04a98-116">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="04a98-116">Return Value</span></span>  
  
|<span data-ttu-id="04a98-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04a98-117">HRESULT</span></span>|<span data-ttu-id="04a98-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="04a98-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04a98-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="04a98-119">S_OK</span></span>|<span data-ttu-id="04a98-120">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="04a98-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="04a98-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04a98-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04a98-122">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="04a98-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04a98-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04a98-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04a98-124">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="04a98-124">The call timed out.</span></span>|  
|<span data-ttu-id="04a98-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04a98-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04a98-126">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="04a98-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04a98-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04a98-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04a98-128">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="04a98-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04a98-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04a98-129">E_FAIL</span></span>|<span data-ttu-id="04a98-130">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="04a98-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04a98-131">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="04a98-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04a98-132">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="04a98-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="04a98-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="04a98-133">E_NOINTERFACE</span></span>|<span data-ttu-id="04a98-134">Não há suporte para o tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="04a98-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04a98-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04a98-135">Requirements</span></span>  

 <span data-ttu-id="04a98-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a98-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a98-137">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="04a98-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04a98-138">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04a98-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04a98-139">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a98-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a98-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="04a98-140">See also</span></span>

- [<span data-ttu-id="04a98-141">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="04a98-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="04a98-142">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="04a98-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
