---
title: Método ICorDebugManagedCallback::LoadModule
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 698a5cb88884febc4dfb3b916c00df20c1a77819
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679644"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>Método ICorDebugManagedCallback::LoadModule

Notifica o depurador de que um módulo Common Language Runtime (CLR) foi carregado com êxito.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pAppDomain`  
 no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual o módulo foi carregado.  
  
 `pModule`  
 no Um ponteiro para um objeto ICorDebugModule que representa o módulo CLR.  
  
## <a name="remarks"></a>Comentários  

 O `LoadModule` retorno de chamada fornece um tempo apropriado para examinar os metadados do módulo, definir sinalizadores de compilador JIT (just-in-time) ou habilitar ou desabilitar retornos de chamada de carregamento de classe para o módulo.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método UnloadModule](icordebugmanagedcallback-unloadmodule-method.md)
- [Interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
