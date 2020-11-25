---
title: Enumeração EClrOperation
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: c24e4557695d26666682ee385131abaab707a24d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720705"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="e8927-102">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="e8927-102">EClrOperation Enumeration</span></span>

<span data-ttu-id="e8927-103">Descreve o conjunto de operações para as quais um host pode aplicar ações de política.</span><span class="sxs-lookup"><span data-stu-id="e8927-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8927-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8927-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="e8927-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e8927-105">Members</span></span>  
  
|<span data-ttu-id="e8927-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e8927-106">Member</span></span>|<span data-ttu-id="e8927-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="e8927-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="e8927-108">O host pode especificar ações de política a serem executadas quando um <xref:System.AppDomain> for descarregado em um modo não normal (rude).</span><span class="sxs-lookup"><span data-stu-id="e8927-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="e8927-109">O host pode especificar ações de política a serem executadas quando um <xref:System.AppDomain> for descarregado.</span><span class="sxs-lookup"><span data-stu-id="e8927-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="e8927-110">O host pode especificar ações de política a serem executadas quando os finalizadores forem executados.</span><span class="sxs-lookup"><span data-stu-id="e8927-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="e8927-111">O host pode especificar ações de política a serem executadas quando o processo for encerrado.</span><span class="sxs-lookup"><span data-stu-id="e8927-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="e8927-112">O host pode especificar ações de política a serem executadas quando um thread for anulado.</span><span class="sxs-lookup"><span data-stu-id="e8927-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="e8927-113">O host pode especificar ações de política a serem executadas quando uma anulação de thread rude ocorrer em uma região crítica de código.</span><span class="sxs-lookup"><span data-stu-id="e8927-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="e8927-114">O host pode especificar ações de política a serem executadas quando uma anulação de thread rude ocorrer em uma região não crítica de código.</span><span class="sxs-lookup"><span data-stu-id="e8927-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8927-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8927-115">Remarks</span></span>  

 <span data-ttu-id="e8927-116">A infraestrutura de confiabilidade do Common Language Runtime (CLR) distingue entre anulações e falhas de alocação de recursos que ocorrem em regiões críticas de código e aquelas que ocorrem em regiões não críticas de código.</span><span class="sxs-lookup"><span data-stu-id="e8927-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="e8927-117">Essa distinção foi projetada para permitir que os hosts definam políticas diferentes dependendo de onde ocorrer uma falha no código.</span><span class="sxs-lookup"><span data-stu-id="e8927-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="e8927-118">Uma *região crítica de código* é qualquer espaço em que o CLR não possa garantir que a anulação de uma tarefa ou a falha de concluir uma solicitação de recursos afetará apenas a tarefa atual.</span><span class="sxs-lookup"><span data-stu-id="e8927-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="e8927-119">Por exemplo, se uma tarefa estiver mantendo um bloqueio e receber um HRESULT que indica falha ao fazer uma solicitação de alocação de memória, é insuficiente simplesmente anular essa tarefa para garantir a estabilidade do <xref:System.AppDomain> , pois o <xref:System.AppDomain> pode conter outras tarefas aguardando o mesmo bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e8927-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="e8927-120">Para abandonar, a tarefa atual pode fazer com que essas outras tarefas parem de responder.</span><span class="sxs-lookup"><span data-stu-id="e8927-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="e8927-121">Nesse caso, o host precisa da capacidade de descarregar todo o <xref:System.AppDomain> risco em potencial de instabilidade.</span><span class="sxs-lookup"><span data-stu-id="e8927-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="e8927-122">Uma *região não-crítica de código*, por outro lado, é uma região em que o CLR pode garantir que uma anulação ou uma falha afete apenas a tarefa sobre a qual o erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="e8927-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="e8927-123">O CLR também distingue entre anulações normais e não normais (rudes).</span><span class="sxs-lookup"><span data-stu-id="e8927-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="e8927-124">Em geral, uma anulação normal ou regular faz cada esforço para executar rotinas de manipulação de exceção e finalizadores antes de abortar uma tarefa, enquanto uma anulação rude não faz nenhuma garantia.</span><span class="sxs-lookup"><span data-stu-id="e8927-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8927-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8927-125">Requirements</span></span>  

 <span data-ttu-id="e8927-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8927-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8927-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e8927-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8927-128">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8927-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8927-129">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8927-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8927-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8927-130">See also</span></span>

- [<span data-ttu-id="e8927-131">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="e8927-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="e8927-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="e8927-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="e8927-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e8927-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="e8927-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e8927-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="e8927-135">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="e8927-135">Hosting Enumerations</span></span>](hosting-enumerations.md)
