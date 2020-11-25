---
title: Método ICorThreadpool::CorCreateTimer
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
ms.openlocfilehash: 3eac575e18c7371754401da6498d85ba7ed6c8cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717593"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="447ad-102">Método ICorThreadpool::CorCreateTimer</span><span class="sxs-lookup"><span data-stu-id="447ad-102">ICorThreadpool::CorCreateTimer Method</span></span>

<span data-ttu-id="447ad-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="447ad-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="447ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="447ad-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="447ad-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="447ad-105">Requirements</span></span>  

 <span data-ttu-id="447ad-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="447ad-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="447ad-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="447ad-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="447ad-108">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="447ad-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="447ad-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="447ad-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="447ad-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="447ad-110">See also</span></span>

- [<span data-ttu-id="447ad-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="447ad-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
