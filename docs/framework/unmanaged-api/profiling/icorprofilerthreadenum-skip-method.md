---
title: Método ICorProfilerThreadEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: 12b7b53c408388c21d7508f6591ead5ccf55936b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721173"
---
# <a name="icorprofilerthreadenumskip-method"></a>Método ICorProfilerThreadEnum::Skip

Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `celt`  
 no O número de elementos a serem ignorados.  
  
## <a name="return-value"></a>Valor Retornado  

 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`celt` os elementos foram ignorados.|  
|S_FALSE|Menos de `celt` elementos foram ignorados, o que indica que não há mais elementos.|  
  
## <a name="remarks"></a>Comentários  

 A nova posição do cursor deste enumerador é (posição atual) + `celt` .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)
- [Criação de perfil de interfaces](profiling-interfaces.md)
