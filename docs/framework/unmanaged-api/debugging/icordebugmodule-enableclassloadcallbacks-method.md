---
title: Método ICorDebugModule::EnableClassLoadCallbacks
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: 1f6c6ae3b7cb45b049d0fb0d88bbf89121bccfd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710409"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>Método ICorDebugModule::EnableClassLoadCallbacks

Controla se os retornos de chamada [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) são chamados para este módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `bClassLoadCallbacks`  
 no Defina esse valor como `true` para habilitar o Common Language Runtime (CLR) para chamar os `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` métodos e quando os eventos associados ocorrerem.  
  
 O valor padrão é `false` para módulos não dinâmicos. O valor é sempre `true` para módulos dinâmicos e não pode ser alterado.  
  
## <a name="remarks"></a>Comentários  

 Os `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` retornos de chamada e estão sempre habilitados para módulos dinâmicos e não podem ser desabilitados.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também
