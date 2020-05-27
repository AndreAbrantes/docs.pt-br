---
title: Método IHostThreadPoolManager::QueueUserWorkItem
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
ms.openlocfilehash: b3d77e30cd48310c392d38dc29f62fab565c8b42
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842459"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="4c763-102">Método IHostThreadPoolManager::QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="4c763-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="4c763-103">Enfileira uma função para execução e especifica um objeto que contém os dados a serem usados por essa função.</span><span class="sxs-lookup"><span data-stu-id="4c763-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="4c763-104">A função é executada quando um thread se torna disponível.</span><span class="sxs-lookup"><span data-stu-id="4c763-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c763-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c763-105">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c763-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c763-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="4c763-107">no Um ponteiro de função que representa a função a ser executada.</span><span class="sxs-lookup"><span data-stu-id="4c763-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="4c763-108">no Um objeto que contém dados a serem usados pelo `Function` .</span><span class="sxs-lookup"><span data-stu-id="4c763-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="4c763-109">no Um dos valores de flags, conforme definido para o `QueueUserWorkItem` método Win32, que controla a execução.</span><span class="sxs-lookup"><span data-stu-id="4c763-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c763-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="4c763-110">Return Value</span></span>  
  
|<span data-ttu-id="4c763-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c763-111">HRESULT</span></span>|<span data-ttu-id="4c763-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c763-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c763-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c763-113">S_OK</span></span>|<span data-ttu-id="4c763-114">`QueueUserWorkItem`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="4c763-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="4c763-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c763-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c763-116">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4c763-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c763-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c763-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c763-118">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4c763-118">The call timed out.</span></span>|  
|<span data-ttu-id="4c763-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c763-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c763-120">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4c763-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c763-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c763-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c763-122">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="4c763-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c763-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c763-123">E_FAIL</span></span>|<span data-ttu-id="4c763-124">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4c763-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c763-125">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="4c763-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c763-126">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4c763-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c763-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c763-127">Remarks</span></span>  
 <span data-ttu-id="4c763-128">`QueueUserWorkItem`Enfileira um item de trabalho para um thread de trabalho no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="4c763-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="4c763-129">Seus tipos de assinatura e parâmetro são idênticos aos da função Win32 correspondente, que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4c763-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="4c763-130">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="4c763-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c763-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c763-131">Requirements</span></span>  
 <span data-ttu-id="4c763-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c763-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c763-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4c763-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c763-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c763-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c763-135">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c763-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c763-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c763-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="4c763-137">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="4c763-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
