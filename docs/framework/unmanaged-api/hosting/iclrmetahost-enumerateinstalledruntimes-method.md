---
title: Método ICLRMetaHost::EnumerateInstalledRuntimes
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
ms.openlocfilehash: f8f67edde7f99878429ca0bbd89aaf52336aa79c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730442"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="aaf23-102">Método ICLRMetaHost::EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="aaf23-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>

<span data-ttu-id="aaf23-103">Retorna uma enumeração que contém uma interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) válida para cada versão do Common Language Runtime (CLR) que está instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="aaf23-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aaf23-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaf23-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aaf23-105">Parameters</span></span>  

 `ppEnumerator`  
 <span data-ttu-id="aaf23-106">fora Uma enumeração de interfaces [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) correspondentes a cada versão do CLR instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="aaf23-106">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaf23-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="aaf23-107">Return Value</span></span>  

 <span data-ttu-id="aaf23-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="aaf23-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aaf23-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aaf23-109">HRESULT</span></span>|<span data-ttu-id="aaf23-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="aaf23-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aaf23-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aaf23-111">S_OK</span></span>|<span data-ttu-id="aaf23-112">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="aaf23-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="aaf23-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="aaf23-113">E_POINTER</span></span>|<span data-ttu-id="aaf23-114">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="aaf23-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aaf23-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aaf23-115">Requirements</span></span>  

 <span data-ttu-id="aaf23-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaf23-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaf23-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="aaf23-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aaf23-118">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aaf23-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aaf23-119">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaf23-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf23-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="aaf23-120">See also</span></span>

- [<span data-ttu-id="aaf23-121">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="aaf23-121">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="aaf23-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="aaf23-122">Hosting</span></span>](index.md)
