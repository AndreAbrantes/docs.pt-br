---
title: Método IGCHost2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: 4dca62903a123765ceb8bb251b79455ad0e4730a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726802"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="47fa8-102">Método IGCHost2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="47fa8-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="47fa8-103">Define o tamanho do segmento e o tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="47fa8-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47fa8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47fa8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47fa8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47fa8-105">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="47fa8-106">no O tamanho do segmento usado pelo sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="47fa8-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="47fa8-107">no O tamanho máximo para a geração 0.</span><span class="sxs-lookup"><span data-stu-id="47fa8-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47fa8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="47fa8-108">Remarks</span></span>  

 <span data-ttu-id="47fa8-109">Os valores que `SetGCStartupLimitsEx` conjuntos só podem ser especificados antes do host ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="47fa8-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="47fa8-110">Esses valores não podem ser alterados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="47fa8-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47fa8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47fa8-111">Requirements</span></span>  

 <span data-ttu-id="47fa8-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47fa8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47fa8-113">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="47fa8-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="47fa8-114">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47fa8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47fa8-115">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47fa8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47fa8-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="47fa8-116">See also</span></span>

- [<span data-ttu-id="47fa8-117">Interface IGCHost2</span><span class="sxs-lookup"><span data-stu-id="47fa8-117">IGCHost2 Interface</span></span>](igchost2-interface.md)
