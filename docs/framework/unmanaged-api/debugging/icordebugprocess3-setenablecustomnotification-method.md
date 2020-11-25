---
title: Método ICorDebugProcess3::SetEnableCustomNotification
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: 078e5cb03848564b42e30a079101d5a61e0074bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734017"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>Método ICorDebugProcess3::SetEnableCustomNotification

Habilita e desabilita as notificações do depurador personalizado do tipo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pClass`  
 no O tipo que especifica as notificações de depurador personalizadas.  
  
 `fEnable`  
 [in] `true` para habilitar notificações personalizadas do depurador; `false` para desabilitar as notificações. O valor padrão é `false`.  
  
## <a name="remarks"></a>Comentários  

 Quando `fEnable` é definido como `true` , as chamadas para o <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> método disparam um retorno de chamada [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) . As notificações são desabilitadas por padrão; Portanto, o depurador deve especificar os tipos de notificação que ele conhece e deseja manipular. Como a classe [ICorDebugClass](icordebug-interface.md) tem o escopo definido pelo domínio do aplicativo, o depurador deve chamar `SetEnableCustomNotification` cada domínio do aplicativo no processo se desejar receber a notificação em todo o processo.  
  
 Começando com o .NET Framework 4, a única notificação com suporte é uma notificação de dependência entre threads.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugProcess3](icordebugprocess3-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
