---
title: Método ICLRTask2::BeginPreventAsyncAbort
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: daf211fcc496f63ef71575abf6a28655004db264
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720237"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="3e504-102">Método ICLRTask2::BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="3e504-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>

<span data-ttu-id="3e504-103">Atrasa novas solicitações de anulação de threads resultando em anulações de thread no thread atual.</span><span class="sxs-lookup"><span data-stu-id="3e504-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e504-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e504-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3e504-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3e504-105">Return Value</span></span>  

 <span data-ttu-id="3e504-106">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="3e504-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3e504-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e504-107">HRESULT</span></span>|<span data-ttu-id="3e504-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e504-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e504-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e504-109">S_OK</span></span>|<span data-ttu-id="3e504-110">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="3e504-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="3e504-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3e504-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3e504-112">O método foi chamado em um thread que não é o thread atual.</span><span class="sxs-lookup"><span data-stu-id="3e504-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e504-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e504-113">Remarks</span></span>  

 <span data-ttu-id="3e504-114">Chamar esse método incrementa o contador atraso-thread-anulação para o thread atual por um.</span><span class="sxs-lookup"><span data-stu-id="3e504-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="3e504-115">Chamadas para `BeginPreventAsyncAbort` e [ICLRTask2:: EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="3e504-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="3e504-116">Desde que o contador seja maior que zero, as anulações de thread para o thread atual serão atrasadas.</span><span class="sxs-lookup"><span data-stu-id="3e504-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="3e504-117">Se essa chamada não for emparelhada com uma chamada para o `EndPreventAsyncAbort` método, é possível alcançar um estado no qual as anulações de thread não podem ser entregues ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="3e504-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="3e504-118">O atraso não é respeitado para um thread que se anula.</span><span class="sxs-lookup"><span data-stu-id="3e504-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="3e504-119">A funcionalidade exposta por esse recurso é usada internamente pela VM (máquina virtual).</span><span class="sxs-lookup"><span data-stu-id="3e504-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="3e504-120">O uso indevido desses métodos pode causar um comportamento não especificado na VM.</span><span class="sxs-lookup"><span data-stu-id="3e504-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="3e504-121">Por exemplo, chamar `EndPreventAsyncAbort` sem primeiro chamar `BeginPreventAsyncAbort` pode definir o contador como zero quando a VM o tiver aumentado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3e504-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="3e504-122">Da mesma forma, o contador interno não é verificado quanto ao estouro.</span><span class="sxs-lookup"><span data-stu-id="3e504-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="3e504-123">Se ele exceder seu limite integral porque é incrementado pelo host e pela VM, o comportamento resultante não é especificado.</span><span class="sxs-lookup"><span data-stu-id="3e504-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e504-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e504-124">Requirements</span></span>  

 <span data-ttu-id="3e504-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e504-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e504-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3e504-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e504-127">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e504-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e504-128">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e504-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e504-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="3e504-129">See also</span></span>

- [<span data-ttu-id="3e504-130">Método EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="3e504-130">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="3e504-131">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="3e504-131">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="3e504-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3e504-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="3e504-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="3e504-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="3e504-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3e504-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="3e504-135">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="3e504-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
