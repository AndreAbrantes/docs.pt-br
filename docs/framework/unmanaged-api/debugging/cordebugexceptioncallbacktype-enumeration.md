---
title: "Enumeração CorDebugExceptionCallbackType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionCallbackType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionCallbackType
helpviewer_keywords: CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dfffea1044eb2c1e771fe86e5e9b431eb0ab9696
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="39d24-102">Enumeração CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="39d24-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="39d24-103">Indica o tipo de retorno de chamada é feito de um [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) eventos.</span><span class="sxs-lookup"><span data-stu-id="39d24-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39d24-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="39d24-105">Membros</span><span class="sxs-lookup"><span data-stu-id="39d24-105">Members</span></span>  
  
|<span data-ttu-id="39d24-106">Membro</span><span class="sxs-lookup"><span data-stu-id="39d24-106">Member</span></span>|<span data-ttu-id="39d24-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="39d24-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="39d24-108">Uma exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="39d24-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="39d24-109">O processo de windup exceção inseriu o código de usuário.</span><span class="sxs-lookup"><span data-stu-id="39d24-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="39d24-110">O processo de windup exceção encontrou um `catch` bloquear no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="39d24-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="39d24-111">A exceção não foi tratada.</span><span class="sxs-lookup"><span data-stu-id="39d24-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="39d24-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39d24-112">Requirements</span></span>  
 <span data-ttu-id="39d24-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39d24-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39d24-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39d24-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39d24-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39d24-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39d24-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39d24-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d24-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39d24-117">See Also</span></span>  
 [<span data-ttu-id="39d24-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="39d24-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
