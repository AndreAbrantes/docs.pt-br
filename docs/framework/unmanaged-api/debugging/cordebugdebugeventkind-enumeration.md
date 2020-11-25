---
title: Enumeração CorDebugDebugEventKind
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
ms.openlocfilehash: e348e0070a5ce619f95dad9ebe4085d17f7ade6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733367"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="8ea09-102">Enumeração CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="8ea09-102">CorDebugDebugEventKind Enumeration</span></span>

<span data-ttu-id="8ea09-103">Indica o tipo de evento cujas informações são decodificadas pelo método [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8ea09-103">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ea09-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ea09-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="8ea09-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8ea09-105">Members</span></span>  
  
|<span data-ttu-id="8ea09-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8ea09-106">Member</span></span>|<span data-ttu-id="8ea09-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="8ea09-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="8ea09-108">Um evento de carga do módulo.</span><span class="sxs-lookup"><span data-stu-id="8ea09-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="8ea09-109">Um evento de descarga do módulo.</span><span class="sxs-lookup"><span data-stu-id="8ea09-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="8ea09-110">Uma exceção de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="8ea09-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="8ea09-111">Uma exceção de usuário de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="8ea09-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="8ea09-112">Uma exceção para a qual existe um manipulador `catch`.</span><span class="sxs-lookup"><span data-stu-id="8ea09-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="8ea09-113">Uma exceção não manipulada.</span><span class="sxs-lookup"><span data-stu-id="8ea09-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ea09-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ea09-114">Remarks</span></span>  

 <span data-ttu-id="8ea09-115">Um membro da `CorDebugDebugEventKind` enumeração é retornado chamando o método [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8ea09-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ea09-116">Essa enumeração destina-se ao uso em cenários de depuração .NET Native apenas.</span><span class="sxs-lookup"><span data-stu-id="8ea09-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ea09-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ea09-117">Requirements</span></span>  

 <span data-ttu-id="8ea09-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ea09-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ea09-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ea09-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ea09-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ea09-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ea09-121">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ea09-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea09-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="8ea09-122">See also</span></span>

- [<span data-ttu-id="8ea09-123">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="8ea09-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
