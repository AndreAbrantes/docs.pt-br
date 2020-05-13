---
title: Método ICorDebugStackWalk::SetContext
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 896e797acc76e8d8034bd964e488317a62eed97b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378772"
---
# <a name="icordebugstackwalksetcontext-method"></a>Método ICorDebugStackWalk::SetContext
Define o contexto atual do objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) como um contexto válido para o thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `flag`  
 no Um sinalizador [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) que indica se o contexto é do quadro ativo na pilha ou um contexto obtido com o desenrolamento da pilha.  
  
 `contextSize`  
 no O tamanho alocado do `CONTEXT` buffer.  
  
 `context`  
 no O `CONTEXT` buffer.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O `ICorDebugStackWalk` contexto do objeto foi definido com êxito.|  
|E_FAIL|O `ICorDebugStackWalk` contexto do objeto não foi definido.|  
|E_INVALIDARG|O contexto é nulo.|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|O buffer de contexto é muito pequeno.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Esse método não altera o contexto atual do thread.  
  
 A definição do contexto atual como um contexto inválido pode causar resultados imprevisíveis do Stack Walker.  
  
 Você pode recuperar uma cópia de bit exata desse contexto chamando imediatamente o método [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
