---
title: Método ICorDebugArrayValue::GetElement
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: 0b6b6f46c7fff8f1d4c2ad555c93423f9ca8ac09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698137"
---
# <a name="icordebugarrayvaluegetelement-method"></a>Método ICorDebugArrayValue::GetElement

Obtém o valor do elemento da matriz fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `cdim`  
 no O número de dimensões deste `ICorDebugArrayValue` objeto.  
  
 Esse valor também é o tamanho da `indices` matriz porque seu tamanho é igual ao número de dimensões do `ICorDebugArrayValue` objeto.  
  
 `indices`  
 no Uma matriz de valores de índice, cada um deles especifica uma posição dentro de uma dimensão do `ICorDebugArrayValue` objeto.  
  
 Esse valor não deve ser nulo.  
  
 `ppValue`  
 fora Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do elemento especificado.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
