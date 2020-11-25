---
title: Método IHostTaskManager::GetStackGuarantee
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
ms.openlocfilehash: 718e6f3f19a5c368091c8a8aad3bd1f6598228df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727270"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="aa87f-102">Método IHostTaskManager::GetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="aa87f-102">IHostTaskManager::GetStackGuarantee Method</span></span>

<span data-ttu-id="aa87f-103">Obtém a quantidade de espaço de pilha que tem garantia de disponibilidade após a conclusão de uma operação de pilha, mas antes do fechamento de um processo.</span><span class="sxs-lookup"><span data-stu-id="aa87f-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa87f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa87f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa87f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa87f-105">Parameters</span></span>  

 `pGuarantee`  
 <span data-ttu-id="aa87f-106">fora Um ponteiro para o número de bytes que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="aa87f-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa87f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa87f-107">Requirements</span></span>  

 <span data-ttu-id="aa87f-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa87f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa87f-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aa87f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa87f-110">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa87f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa87f-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa87f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa87f-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa87f-112">See also</span></span>

- [<span data-ttu-id="aa87f-113">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="aa87f-113">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
