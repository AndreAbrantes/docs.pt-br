---
title: Método ICorDebugBreakpoint::IsActive
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
ms.openlocfilehash: 064f9727b221dd64a58f8cd5e103271e37020786
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730169"
---
# <a name="icordebugbreakpointisactive-method"></a>Método ICorDebugBreakpoint::IsActive

Obtém um valor que indica se ele `ICorDebugBreakpoint` está ativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pbActive`  
 [fora] `true` Se esse ponto de interrupção estiver ativo; caso contrário, `false` .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
