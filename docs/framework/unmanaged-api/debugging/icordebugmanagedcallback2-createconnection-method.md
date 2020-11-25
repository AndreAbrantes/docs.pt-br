---
title: Método ICorDebugManagedCallback2::CreateConnection
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: 5a4ebf65dfaaa487e87f3fd78e54c468c7e24a89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697225"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="23f44-102">Método ICorDebugManagedCallback2::CreateConnection</span><span class="sxs-lookup"><span data-stu-id="23f44-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>

<span data-ttu-id="23f44-103">Notifica o depurador de que uma nova conexão foi criada.</span><span class="sxs-lookup"><span data-stu-id="23f44-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23f44-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23f44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23f44-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="23f44-106">no Um ponteiro para um objeto "ICorDebugProcess" que representa o processo no qual a conexão foi criada</span><span class="sxs-lookup"><span data-stu-id="23f44-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="23f44-107">no A ID da nova conexão.</span><span class="sxs-lookup"><span data-stu-id="23f44-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="23f44-108">no Um ponteiro para o nome da nova conexão.</span><span class="sxs-lookup"><span data-stu-id="23f44-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23f44-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="23f44-109">Remarks</span></span>  

 <span data-ttu-id="23f44-110">Um `CreateConnection` retorno de chamada será acionado em qualquer um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="23f44-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="23f44-111">Quando um depurador é anexado a um processo que contém conexões.</span><span class="sxs-lookup"><span data-stu-id="23f44-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="23f44-112">Nesse caso, o tempo de execução irá gerar e distribuir um evento `CreateConnection` e um evento [ICorDebugManagedCallback2:: ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) para cada conexão no processo.</span><span class="sxs-lookup"><span data-stu-id="23f44-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="23f44-113">Quando um host chama [ICLRDebugManager:: BeginConnect](../hosting/iclrdebugmanager-beginconnection-method.md) na API de [hospedagem](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="23f44-113">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23f44-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23f44-114">Requirements</span></span>  

 <span data-ttu-id="23f44-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23f44-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f44-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23f44-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23f44-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23f44-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23f44-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f44-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f44-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="23f44-119">See also</span></span>

- [<span data-ttu-id="23f44-120">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="23f44-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="23f44-121">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="23f44-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
