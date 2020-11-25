---
title: Método ICLRMetaHost::GetRuntime
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: 093fa64a7d51e0c2fdc304d2bb4f1c9f7b03e2ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730403"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="90a31-102">Método ICLRMetaHost::GetRuntime</span><span class="sxs-lookup"><span data-stu-id="90a31-102">ICLRMetaHost::GetRuntime Method</span></span>

<span data-ttu-id="90a31-103">Obtém a interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) que corresponde a uma versão específica do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="90a31-103">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="90a31-104">Esse método substitui a função [CorBindToRuntimeEx](corbindtoruntimeex-function.md) usada com o sinalizador [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="90a31-104">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90a31-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90a31-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90a31-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90a31-106">Parameters</span></span>  

 `pwzVersion`  
 <span data-ttu-id="90a31-107">no A versão de compilação .NET Framework armazenada nos metadados, no formato "v *A*. *B*[.*X*] ".</span><span class="sxs-lookup"><span data-stu-id="90a31-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="90a31-108">*A*, *B* e *X* são números decimais que correspondem à versão principal, à versão secundária e ao número da compilação.</span><span class="sxs-lookup"><span data-stu-id="90a31-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90a31-109">Esse parâmetro deve corresponder ao nome do diretório para a versão .NET Framework, pois ele aparece em C:\Windows\Microsoft.NET\Framework ou C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="90a31-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="90a31-110">Os valores de exemplo são "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" e "v 4.0. *X*", em que *x* depende do número de Build instalado.</span><span class="sxs-lookup"><span data-stu-id="90a31-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="90a31-111">O prefixo "v" é necessário.</span><span class="sxs-lookup"><span data-stu-id="90a31-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="90a31-112">no O identificador para a interface desejada.</span><span class="sxs-lookup"><span data-stu-id="90a31-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="90a31-113">Atualmente, o único valor válido para esse parâmetro é IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="90a31-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="90a31-114">fora Um ponteiro para a interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) que corresponde ao tempo de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="90a31-114">[out] A pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90a31-115">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="90a31-115">Return Value</span></span>  

 <span data-ttu-id="90a31-116">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="90a31-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90a31-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90a31-117">HRESULT</span></span>|<span data-ttu-id="90a31-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="90a31-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90a31-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="90a31-119">S_OK</span></span>|<span data-ttu-id="90a31-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="90a31-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="90a31-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="90a31-121">E_POINTER</span></span>|<span data-ttu-id="90a31-122">`pwzVersion` ou `ppRuntime` é nulo.</span><span class="sxs-lookup"><span data-stu-id="90a31-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90a31-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="90a31-123">Remarks</span></span>  

 <span data-ttu-id="90a31-124">Esse método interage consistentemente com interfaces herdadas, como a interface [ICorRuntimeHost](icorruntimehost-interface.md) e funções herdadas, como as funções preteridas `CorBindTo*` (consulte [funções de Hospedagem de CLR preteridas](deprecated-clr-hosting-functions.md) na API de hospedagem do .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="90a31-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="90a31-125">Ou seja, os tempos de execução que são carregados com a API herdada são visíveis para a nova API, e os tempos de execução que são carregados com a nova API são visíveis para a API herdada.</span><span class="sxs-lookup"><span data-stu-id="90a31-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90a31-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90a31-126">Requirements</span></span>  

 <span data-ttu-id="90a31-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90a31-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90a31-128">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="90a31-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="90a31-129">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90a31-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90a31-130">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90a31-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a31-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="90a31-131">See also</span></span>

- [<span data-ttu-id="90a31-132">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="90a31-132">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="90a31-133">Interfaces e coclasse de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="90a31-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="90a31-134">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="90a31-134">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="90a31-135">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="90a31-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="90a31-136">Hosting</span><span class="sxs-lookup"><span data-stu-id="90a31-136">Hosting</span></span>](index.md)
