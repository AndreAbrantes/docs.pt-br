---
title: Enumeração CorDebugBlockingReason
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
ms.openlocfilehash: ddd03d70656ad52fd9d577beedc60b51c7b305d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672845"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="98cd1-102">Enumeração CorDebugBlockingReason</span><span class="sxs-lookup"><span data-stu-id="98cd1-102">CorDebugBlockingReason Enumeration</span></span>

<span data-ttu-id="98cd1-103">Especifica os motivos pelos quais um thread pode ficar bloqueado em um determinado objeto.</span><span class="sxs-lookup"><span data-stu-id="98cd1-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98cd1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98cd1-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="98cd1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="98cd1-105">Members</span></span>  
  
|<span data-ttu-id="98cd1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="98cd1-106">Member</span></span>|<span data-ttu-id="98cd1-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="98cd1-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="98cd1-108">Somente para uso interno.</span><span class="sxs-lookup"><span data-stu-id="98cd1-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="98cd1-109">Um thread está tentando adquirir a seção crítica associada ao bloqueio de monitor em um objeto.</span><span class="sxs-lookup"><span data-stu-id="98cd1-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="98cd1-110">Normalmente, isso ocorre quando você chama um dos <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> métodos ou <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="98cd1-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="98cd1-111">Um thread está aguardando o evento que está associado a um bloqueio de monitor para um objeto.</span><span class="sxs-lookup"><span data-stu-id="98cd1-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="98cd1-112">Normalmente, isso ocorre quando você chama um dos <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` métodos.</span><span class="sxs-lookup"><span data-stu-id="98cd1-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98cd1-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="98cd1-113">Remarks</span></span>  

 <span data-ttu-id="98cd1-114">Quando o `BLOCKING_MONITOR_CRITICAL_SECTION` `BLOCKING_MONITOR_EVENT` membro ou é usado em uma estrutura [CorDebugBlockingObject](cordebugblockingobject-structure.md) , o `pBlockingObject` membro da estrutura aponta para uma interface "ICorDebugValue" que representa o objeto que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="98cd1-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="98cd1-115">Também é garantido implementar a interface [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="98cd1-115">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98cd1-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98cd1-116">Requirements</span></span>  

 <span data-ttu-id="98cd1-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98cd1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98cd1-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98cd1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98cd1-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98cd1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98cd1-120">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98cd1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cd1-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="98cd1-121">See also</span></span>

- [<span data-ttu-id="98cd1-122">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="98cd1-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="98cd1-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="98cd1-123">Debugging</span></span>](index.md)
