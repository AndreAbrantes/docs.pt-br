---
title: Método ICorProfilerInfo2::GetArrayObjectInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: a1e321e141059ccf1da7292d28e7099418a5134e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727192"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>Método ICorProfilerInfo2::GetArrayObjectInfo

Obtém informações detalhadas sobre um objeto de matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `objectId`  
 no A ID de um objeto de matriz válido.  
  
 `cDimensions`  
 no A classificação (número de dimensões) da matriz.  
  
 `pDimensionSizes`  
 fora Uma matriz que contém inteiros, cada um representando o tamanho de uma dimensão da matriz.  
  
 `pDimensionLowerBounds`  
 fora Uma matriz que contém inteiros, cada um representando o limite inferior de uma dimensão da matriz.  
  
 `ppData`  
 fora Um ponteiro para o endereço do buffer bruto para a matriz, que é disposta de acordo com a Convenção de C++.  
  
## <a name="remarks"></a>Comentários  

 Os `pDimensionSizes` e `pDimensionLowerBounds` são matrizes paralelas, portanto, os elementos localizados no mesmo índice em cada matriz são características da mesma entidade.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](icorprofilerinfo2-interface.md)
