---
title: Enumeração CorDebugThreadState
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 5eee2aee5873fe512136bc5407e395acdc31af29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722603"
---
# <a name="cordebugthreadstate-enumeration"></a>Enumeração CorDebugThreadState

Especifica o estado de um thread para depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|DESCRIÇÃO|  
|------------|-----------------|  
|`THREAD_RUN`|O thread é executado livremente, a menos que ocorra um evento de depuração.|  
|`THREAD_SUSPEND`|Não é possível executar o thread.|  
  
## <a name="remarks"></a>Comentários  

 O depurador usa a `CorDebugThreadState` enumeração para controlar a execução de um thread. O estado de um thread pode ser definido usando o método [ICorDebugThread:: SetDebugState](icordebugthread-setdebugstate-method.md) ou [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) .  
  
 Um retorno de chamada fornecido à [API de hospedagem](../hosting/index.md) permite bombeamento de mensagens, portanto, um estado interrompido não é necessário.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Declarando enumerações](debugging-enumerations.md)
