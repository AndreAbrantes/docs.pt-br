---
title: Método ICLRAppDomainResourceMonitor::GetCurrentSurvived
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
ms.openlocfilehash: a73c0731c79dea3a0c411fe27a864ec9ac4e20b2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616015"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="15ed7-102">Método ICLRAppDomainResourceMonitor::GetCurrentSurvived</span><span class="sxs-lookup"><span data-stu-id="15ed7-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="15ed7-103">Obtém o número de bytes que sobreviveram o último total, bloqueando a coleta de lixo e que são referenciados pelo domínio do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="15ed7-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15ed7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15ed7-104">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15ed7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15ed7-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="15ed7-106">no A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="15ed7-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="15ed7-107">fora Um ponteiro para o número de bytes que sobreviveram após a última coleta de lixo que é mantida por esse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="15ed7-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="15ed7-108">Após uma coleção completa, esse número é preciso e completo.</span><span class="sxs-lookup"><span data-stu-id="15ed7-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="15ed7-109">Após uma coleção efêmera, esse número é potencialmente incompleto.</span><span class="sxs-lookup"><span data-stu-id="15ed7-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="15ed7-110">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="15ed7-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="15ed7-111">fora Um ponteiro para o número total de bytes que sobreviveram da última coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="15ed7-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="15ed7-112">Após uma coleção completa, esse número representa o número de bytes que são mantidos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="15ed7-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="15ed7-113">Após uma coleção efêmera, esse número representa o número de bytes que são mantidos ao vivo em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="15ed7-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="15ed7-114">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="15ed7-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15ed7-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="15ed7-115">Return Value</span></span>  
 <span data-ttu-id="15ed7-116">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="15ed7-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="15ed7-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15ed7-117">HRESULT</span></span>|<span data-ttu-id="15ed7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="15ed7-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15ed7-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="15ed7-119">S_OK</span></span>|<span data-ttu-id="15ed7-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="15ed7-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="15ed7-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="15ed7-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="15ed7-122">O domínio do aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="15ed7-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15ed7-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="15ed7-123">Remarks</span></span>  
 <span data-ttu-id="15ed7-124">As estatísticas são atualizadas somente após um total, bloqueando a coleta de lixo; ou seja, uma coleção que inclui todas as gerações e que interrompe o aplicativo enquanto a coleta ocorre.</span><span class="sxs-lookup"><span data-stu-id="15ed7-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="15ed7-125">Por exemplo, a <xref:System.GC.Collect?displayProperty=nameWithType> sobrecarga do método executa uma coleção de bloqueio completa.</span><span class="sxs-lookup"><span data-stu-id="15ed7-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="15ed7-126">A coleta de lixo simultânea ocorre em segundo plano e não bloqueia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="15ed7-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="15ed7-127">O `GetCurrentSurvived` método é o equivalente não gerenciado da propriedade gerenciada <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="15ed7-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15ed7-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15ed7-128">Requirements</span></span>  
 <span data-ttu-id="15ed7-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15ed7-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15ed7-130">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="15ed7-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="15ed7-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15ed7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15ed7-132">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15ed7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ed7-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="15ed7-133">See also</span></span>

- [<span data-ttu-id="15ed7-134">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="15ed7-134">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="15ed7-135">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="15ed7-135">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="15ed7-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="15ed7-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="15ed7-137">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="15ed7-137">Hosting</span></span>](index.md)
