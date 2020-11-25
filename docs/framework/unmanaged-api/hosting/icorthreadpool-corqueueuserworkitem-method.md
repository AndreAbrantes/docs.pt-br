---
title: Método ICorThreadpool::CorQueueUserWorkItem
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
ms.openlocfilehash: 42de7cd566db53e43985088851fd01fb66feabd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720487"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="84533-102">Método ICorThreadpool::CorQueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="84533-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>

<span data-ttu-id="84533-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="84533-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84533-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84533-104">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="84533-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84533-105">Requirements</span></span>  

 <span data-ttu-id="84533-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84533-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84533-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="84533-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84533-108">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84533-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84533-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84533-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84533-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="84533-110">See also</span></span>

- [<span data-ttu-id="84533-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="84533-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
