---
title: Estrutura COR_ACTIVE_FUNCTION
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: c50ba530d78296ebb956329b2f34b4f1e5cae94c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727413"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="8bda8-102">Estrutura COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="8bda8-102">COR_ACTIVE_FUNCTION Structure</span></span>

<span data-ttu-id="8bda8-103">Contém informações sobre as funções que estão atualmente ativas nos quadros de um thread.</span><span class="sxs-lookup"><span data-stu-id="8bda8-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="8bda8-104">Essa estrutura é usada pelo método [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8bda8-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bda8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8bda8-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="8bda8-106">Membros</span><span class="sxs-lookup"><span data-stu-id="8bda8-106">Members</span></span>  
  
|<span data-ttu-id="8bda8-107">Membro</span><span class="sxs-lookup"><span data-stu-id="8bda8-107">Member</span></span>|<span data-ttu-id="8bda8-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="8bda8-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="8bda8-109">Ponteiro para o proprietário do campo do domínio do aplicativo `ilOffset` .</span><span class="sxs-lookup"><span data-stu-id="8bda8-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="8bda8-110">Ponteiro para o proprietário do módulo do `ilOffset` campo.</span><span class="sxs-lookup"><span data-stu-id="8bda8-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="8bda8-111">Ponteiro para o proprietário da função do `ilOffset` campo.</span><span class="sxs-lookup"><span data-stu-id="8bda8-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="8bda8-112">O deslocamento da MSIL (Microsoft Intermediate Language) do quadro.</span><span class="sxs-lookup"><span data-stu-id="8bda8-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="8bda8-113">Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="8bda8-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bda8-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8bda8-114">Requirements</span></span>  

 <span data-ttu-id="8bda8-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bda8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bda8-116">**Cabeçalho:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="8bda8-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8bda8-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bda8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bda8-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bda8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bda8-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="8bda8-119">See also</span></span>

- [<span data-ttu-id="8bda8-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="8bda8-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="8bda8-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="8bda8-121">Debugging</span></span>](index.md)
