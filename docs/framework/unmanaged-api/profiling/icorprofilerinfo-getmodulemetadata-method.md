---
title: Método ICorProfilerInfo::GetModuleMetaData
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 74df0fb412e7fb3d9f779391ec84f07a0379a2cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724111"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>Método ICorProfilerInfo::GetModuleMetaData

Obtém uma instância de interface de metadados que mapeia para o módulo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `moduleId`  
 no A ID do módulo para o qual a instância de interface será mapeada.  
  
 `dwOpenFlags`  
 no Um valor da enumeração [CorOpenFlags](../metadata/coropenflags-enumeration.md) que especifica o modo para abrir arquivos de manifesto. Somente os `ofRead` `ofWrite` bits e `ofNoTransform` são válidos.  
  
 `riid`  
 no A ID de referência (GUID) da interface de metadados cuja instância será recuperada. Consulte [interfaces de metadados](../metadata/metadata-interfaces.md) para obter uma lista das interfaces.  
  
 `ppOut`  
 fora Um ponteiro para o endereço da instância da interface de metadados.  
  
## <a name="remarks"></a>Comentários  

 Você pode solicitar que os metadados sejam abertos no modo de leitura/gravação, mas isso resultará em uma execução de metadados mais lenta do programa, pois as alterações feitas nos metadados não podem ser otimizadas como eram do compilador.  
  
 Alguns módulos (como módulos de recurso) não têm metadados. Nesses casos, o `GetModuleMetaData` retornará um valor HRESULT de S_FALSE e um nulo em * `ppOut` .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
