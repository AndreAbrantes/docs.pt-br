---
title: Método ICorProfilerCallback::ModuleLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
ms.openlocfilehash: 6fbd009b5785c5dc78df81e4411fbdf8e8eadf71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730325"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a>Método ICorProfilerCallback::ModuleLoadStarted

Notifica o criador de perfil de que um módulo está sendo carregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `moduleId`  
 no A ID do módulo que está sendo carregado.  
  
## <a name="remarks"></a>Comentários  

 O valor de `moduleId` não é válido para uma solicitação de informações até que o método [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) seja chamado.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
