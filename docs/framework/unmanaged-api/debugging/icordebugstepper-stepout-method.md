---
title: Método ICorDebugStepper::StepOut
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 1396e7a8ca61734a9363a9c852502290675249d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727660"
---
# <a name="icordebugstepperstepout-method"></a>Método ICorDebugStepper::StepOut

Faz com que esse ICorDebugStepper faça uma única etapa por meio de seu thread que o contém e seja concluído quando o quadro atual retorna o controle para o quadro de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Comentários  

 Uma `StepOut` operação será concluída depois de retornar normalmente do quadro atual para o quadro de chamada.  
  
 Se `StepOut` for chamado quando estiver no código não gerenciado, a etapa será concluída quando o quadro atual retornar ao código gerenciado que o chamou.  
  
 No .NET Framework versão 2,0, não use `StepOut` com o sinalizador STOP_UNMANAGED definido porque ele falhará. (Use [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) para definir sinalizadores para depuração.) Os depuradores de interoperabilidade devem sair para o próprio código nativo.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
