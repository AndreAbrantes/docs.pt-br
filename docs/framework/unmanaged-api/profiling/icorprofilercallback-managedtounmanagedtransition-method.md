---
title: Método ICorProfilerCallback::ManagedToUnmanagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: 0750ac66c654285e11dbbb5941f029bf5f900842
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866189"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>Método ICorProfilerCallback::ManagedToUnmanagedTransition
Notifica o criador de perfil de que uma transição do código gerenciado para o código não gerenciado ocorreu.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função que está sendo chamada.  
  
 `reason`  
 no Um valor da enumeração [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) que indica se a transição ocorreu devido a uma chamada em código não gerenciado do código gerenciado ou devido a um retorno de uma função gerenciada chamada por um não gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `reason` for COR_PRF_TRANSITION_CALL, a ID da função será a da função não gerenciada, que nunca terá sido compilada usando o compilador just-in-time. As funções não gerenciadas têm informações básicas associadas a elas, como um nome e alguns metadados. Se a função não gerenciada for chamada usando o PInvoke (chamada de plataforma implícita), o tempo de execução não poderá determinar o destino da chamada e o valor de `functionId` será NULL. Para obter mais informações sobre o PInvoke implícito, consulte [usando C++ a interoperabilidade (PInvoke implícito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [Usando PInvoke explícito no C++ (atributo DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
