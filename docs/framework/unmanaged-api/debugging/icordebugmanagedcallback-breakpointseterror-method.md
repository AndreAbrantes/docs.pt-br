---
title: Método ICorDebugManagedCallback::BreakpointSetError
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: cac8393408de626efe2360999e259780eac29f38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721329"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a>Método ICorDebugManagedCallback::BreakpointSetError

Notifica o depurador de que o Common Language Runtime não pôde ligar com precisão um ponto de interrupção definido antes que uma função tenha sido compilada JIT (just-in-time).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o ponto de interrupção não associado.  
  
 `pThread`  
 no Um ponteiro para um objeto ICorDebugThread que representa o thread que contém o ponto de interrupção não associado.  
  
 `pBreakpoint`  
 no Um ponteiro para um objeto ICorDebugBreakpoint que representa o ponto de interrupção não associado.  
  
 `dwError`  
 no Um inteiro que indica o erro.  
  
## <a name="remarks"></a>Comentários  

 O ponto de interrupção fornecido nunca será atingido. O depurador deve desativar e reassociá-lo.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
