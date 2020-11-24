---
title: Método ICorDebugManagedCallback::LogMessage
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: 92b2a7f7f1dd98f0d847119a6431e3816c16d5da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679566"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="45738-102">Método ICorDebugManagedCallback::LogMessage</span><span class="sxs-lookup"><span data-stu-id="45738-102">ICorDebugManagedCallback::LogMessage Method</span></span>

<span data-ttu-id="45738-103">Notifica o depurador de que um thread gerenciado Common Language Runtime (CLR) chamou um método na <xref:System.Diagnostics.EventLog> classe para registrar um evento.</span><span class="sxs-lookup"><span data-stu-id="45738-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45738-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45738-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45738-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45738-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="45738-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado que registrou o evento.</span><span class="sxs-lookup"><span data-stu-id="45738-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="45738-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="45738-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="45738-108">no Um valor da enumeração [LoggingLevelEnum](logginglevelenum-enumeration.md) que indica o nível de severidade da mensagem descritiva que foi gravada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="45738-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="45738-109">no Um ponteiro para o nome da opção de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="45738-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="45738-110">no Um ponteiro para a mensagem que foi gravada no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="45738-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45738-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45738-111">Requirements</span></span>  

 <span data-ttu-id="45738-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45738-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45738-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45738-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45738-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45738-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45738-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45738-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45738-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="45738-116">See also</span></span>

- [<span data-ttu-id="45738-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="45738-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
