---
title: Método ICLRRuntimeHost::ExecuteInAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: 4c28c4a5cc64b20c9ac9c57e1aef5e7b90a20e01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728882"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="d166f-102">Método ICLRRuntimeHost::ExecuteInAppDomain</span><span class="sxs-lookup"><span data-stu-id="d166f-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>

<span data-ttu-id="d166f-103">Especifica o <xref:System.AppDomain> no qual executar o código gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="d166f-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d166f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d166f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d166f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d166f-105">Parameters</span></span>  

 `AppDomainId`  
 <span data-ttu-id="d166f-106">no A ID numérica do <xref:System.AppDomain> na qual executar o método especificado.</span><span class="sxs-lookup"><span data-stu-id="d166f-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="d166f-107">no Um ponteiro para a função a ser executada dentro do especificado <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="d166f-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="d166f-108">no Um ponteiro para uma memória opaca alocada pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="d166f-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="d166f-109">Esse parâmetro é passado pelo Common Language Runtime (CLR) para o retorno de chamada do domínio.</span><span class="sxs-lookup"><span data-stu-id="d166f-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="d166f-110">Não é uma memória heap gerenciada pelo tempo de execução; a alocação e o tempo de vida dessa memória são controlados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="d166f-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d166f-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="d166f-111">Return Value</span></span>  
  
|<span data-ttu-id="d166f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d166f-112">HRESULT</span></span>|<span data-ttu-id="d166f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d166f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d166f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d166f-114">S_OK</span></span>|<span data-ttu-id="d166f-115">`ExecuteInAppDomain` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d166f-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="d166f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d166f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d166f-117">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d166f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d166f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d166f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d166f-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d166f-119">The call timed out.</span></span>|  
|<span data-ttu-id="d166f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d166f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d166f-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d166f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d166f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d166f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d166f-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="d166f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d166f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d166f-124">E_FAIL</span></span>|<span data-ttu-id="d166f-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d166f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d166f-126">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="d166f-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d166f-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d166f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d166f-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="d166f-128">Remarks</span></span>  

 <span data-ttu-id="d166f-129">`ExecuteInAppDomain` permite que o host assuma o controle sobre qual gerenciado <xref:System.AppDomain> o método gerenciado especificado deve ser executado.</span><span class="sxs-lookup"><span data-stu-id="d166f-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="d166f-130">Você pode obter o valor do identificador de um domínio de aplicativo, que corresponde ao valor da <xref:System.AppDomain.Id%2A> propriedade, chamando o [método GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="d166f-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d166f-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d166f-131">Requirements</span></span>  

 <span data-ttu-id="d166f-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d166f-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d166f-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d166f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d166f-134">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d166f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d166f-135">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d166f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d166f-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="d166f-136">See also</span></span>

- [<span data-ttu-id="d166f-137">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d166f-137">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
