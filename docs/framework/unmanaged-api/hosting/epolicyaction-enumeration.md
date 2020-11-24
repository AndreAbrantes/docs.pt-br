---
title: Enumeração EPolicyAction
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: 72b371d72b2f055f2840da5595d9022ffd7e2507
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674722"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="31ef9-102">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="31ef9-102">EPolicyAction Enumeration</span></span>

<span data-ttu-id="31ef9-103">Descreve as ações de política que o host pode definir para operações descritas por [EClrOperation](eclroperation-enumeration.md) e falhas descritas por [EClrFailure](eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="31ef9-103">Describes the policy actions the host can set for operations described by [EClrOperation](eclroperation-enumeration.md) and failures described by [EClrFailure](eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31ef9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31ef9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="31ef9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="31ef9-105">Members</span></span>  
  
|<span data-ttu-id="31ef9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="31ef9-106">Member</span></span>|<span data-ttu-id="31ef9-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="31ef9-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="31ef9-108">Especifica que o Common Language Runtime (CLR) deve abortar o thread normalmente.</span><span class="sxs-lookup"><span data-stu-id="31ef9-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="31ef9-109">Uma anulação normal inclui tentativas de executar todos os `finally` blocos, todos os `catch` blocos relacionados a anulações de thread e finalizadores.</span><span class="sxs-lookup"><span data-stu-id="31ef9-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="31ef9-110">Especifica que o CLR deve entrar em um estado desabilitado.</span><span class="sxs-lookup"><span data-stu-id="31ef9-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="31ef9-111">Nenhum código gerenciado adicional pode ser executado no processo afetado e os threads são impedidos de entrar no CLR.</span><span class="sxs-lookup"><span data-stu-id="31ef9-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="31ef9-112">Especifica que o CLR deve tentar uma saída normal do processo, incluindo a execução de finalizadores e a execução de operações de limpeza e registro em log.</span><span class="sxs-lookup"><span data-stu-id="31ef9-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="31ef9-113">Especifica que o CLR deve sair do processo imediatamente, sem executar finalizadores ou executar operações de limpeza e registro em log.</span><span class="sxs-lookup"><span data-stu-id="31ef9-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="31ef9-114">No entanto, a notificação é enviada ao depurador.</span><span class="sxs-lookup"><span data-stu-id="31ef9-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="31ef9-115">Especifica que nenhuma ação deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="31ef9-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="31ef9-116">Especifica que o CLR deve executar uma anulação de thread rude.</span><span class="sxs-lookup"><span data-stu-id="31ef9-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="31ef9-117">Somente os `catch` `finally` blocos and marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="31ef9-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="31ef9-118">Especifica que o CLR deve sair do processo sem executar finalizadores ou operações de registro em log.</span><span class="sxs-lookup"><span data-stu-id="31ef9-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="31ef9-119">Especifica que o CLR deve executar um descarregamento rude do <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="31ef9-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="31ef9-120">Somente finalizadores marcados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="31ef9-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="31ef9-121">Da mesma forma, todos os threads com isso <xref:System.AppDomain> em sua pilha recebem um `ThreadAbortException` , mas somente os `catch` `finally` blocos e bloqueados com <xref:System.EnterpriseServices.MustRunInClientContextAttribute> são executados.</span><span class="sxs-lookup"><span data-stu-id="31ef9-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="31ef9-122">Especifica que uma exceção apropriada para a condição, como memória insuficiente, estouro de buffer e assim por diante, deve ser lançada.</span><span class="sxs-lookup"><span data-stu-id="31ef9-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="31ef9-123">Especifica que o <xref:System.AppDomain> deve ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="31ef9-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="31ef9-124">O CLR tenta executar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="31ef9-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31ef9-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="31ef9-125">Remarks</span></span>  

 <span data-ttu-id="31ef9-126">O host define as ações de política chamando métodos da interface [ICLRPolicyManager](iclrpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="31ef9-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="31ef9-127">Para obter informações sobre anulações rudes e normais, consulte a enumeração [EClrOperation](eclroperation-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="31ef9-127">For information about rude and graceful aborts, see the [EClrOperation](eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ef9-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31ef9-128">Requirements</span></span>  

 <span data-ttu-id="31ef9-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31ef9-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31ef9-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="31ef9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31ef9-131">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31ef9-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31ef9-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31ef9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ef9-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="31ef9-133">See also</span></span>

- [<span data-ttu-id="31ef9-134">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="31ef9-134">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="31ef9-135">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="31ef9-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="31ef9-136">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="31ef9-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="31ef9-137">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="31ef9-137">Hosting Enumerations</span></span>](hosting-enumerations.md)
