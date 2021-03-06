---
title: Método ICorDebugModule::EnableJITDebugging
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: 359db27878ea4adf794bcd6221d4b5387026e5c0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710305"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>Método ICorDebugModule::EnableJITDebugging

Controla se o compilador JIT (just-in-time) preserva informações de depuração para métodos dentro deste módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `bTrackJITInfo`  
 no Defina esse valor como `true` para habilitar o compilador JIT para preservar informações de mapeamento entre a versão do Microsoft Intermediate Language (MSIL) e a versão compilada em JIT de cada método neste módulo.  
  
 `bAllowJitOpts`  
 no Defina esse valor como `true` para habilitar o compilador JIT para gerar código com determinadas otimizações específicas de JIT para depuração.  
  
## <a name="remarks"></a>Comentários  

 A depuração JIT é habilitada por padrão para todos os módulos que são carregados quando o depurador está ativo. Habilitar ou desabilitar programaticamente as configurações substitui as configurações globais.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
