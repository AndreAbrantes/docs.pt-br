---
title: Método ICLRTaskManager::GetCurrentTaskType
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 684b94471c53701c5ebe1dc7e7593eae16ad50fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728778"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="4ca7f-102">Método ICLRTaskManager::GetCurrentTaskType</span><span class="sxs-lookup"><span data-stu-id="4ca7f-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="4ca7f-103">Obtém o tipo da tarefa que está sendo executada no momento.</span><span class="sxs-lookup"><span data-stu-id="4ca7f-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ca7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ca7f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ca7f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ca7f-105">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="4ca7f-106">fora Um ponteiro para um valor da enumeração [ETaskType](etasktype-enumeration.md) que indica o tipo de tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="4ca7f-106">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ca7f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ca7f-107">Requirements</span></span>  

 <span data-ttu-id="4ca7f-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ca7f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ca7f-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4ca7f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ca7f-110">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ca7f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ca7f-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ca7f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca7f-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="4ca7f-112">See also</span></span>

- [<span data-ttu-id="4ca7f-113">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="4ca7f-113">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
