---
title: Estrutura CorDebugBlockingObject
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
ms.openlocfilehash: b16feb1af0d4975411876e78940d21096750d2ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726579"
---
# <a name="cordebugblockingobject-structure"></a>Estrutura CorDebugBlockingObject

Define um objeto que está bloqueando um thread e o motivo específico pelo qual o thread está bloqueado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|DESCRIÇÃO|  
|------------|-----------------|  
|`pBlockingObject`|O objeto no qual o thread está sendo bloqueado. Esse objeto é válido somente pela duração do estado atual sincronizado. Se dois threads estiverem bloqueando o mesmo objeto dentro do mesmo estado sincronizado, você poderá esperar que o método [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) retorne o mesmo valor. No entanto, as interfaces podem ou não ser equivalentes ao ponteiro.|  
|`dwTimeout`|O número de milissegundos antes da operação de bloqueio atingirá o tempo limite ou o valor infinito, que indica que ele não atingirá o tempo limite. O valor de tempo limite especifica o período de tempo total para a operação de bloqueio, não a hora que ainda resta.|  
|`blockingReason`|O motivo pelo qual o thread está bloqueado neste objeto.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
