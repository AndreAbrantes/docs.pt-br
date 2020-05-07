---
title: Método ICorDebugBlockingObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
ms.openlocfilehash: 0ef49d2d833841eac62b2b964a0fdc902b4fb6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894768"
---
# <a name="icordebugblockingobjectenumnext-method"></a>Método ICorDebugBlockingObjectEnum::Next
Obtém o número especificado de objetos [CorDebugBlockingObject](cordebugblockingobject-structure.md) da enumeração, começando na posição atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de objetos a serem recuperados.  
  
 `values`  
 fora Uma matriz de ponteiros para objetos [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
 `pceltFetched`  
 fora Um ponteiro para o número de objetos que foram recuperados.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|S_FALSE|`pceltFetched` não é igual a `celt`.|  
  
## <a name="remarks"></a>Comentários  
 Esse método funciona como um enumerador COM típico.  
  
 Os valores da matriz de entrada devem ter pelo menos `celt`tamanho. A matriz será preenchida com os valores seguintes `celt` na enumeração ou com todos os valores restantes, se houver menos `celt` de permanecer. Quando esse método retornar, `pceltFetched` será preenchido com o número de valores que foram recuperados. Se `values` contiver ponteiros ou pontos inválidos para um buffer `celt`menor que, `pceltFetched` ou se for um ponteiro inválido, o resultado será indefinido.  
  
> [!NOTE]
> Embora a estrutura [CorDebugBlockingObject](cordebugblockingobject-structure.md) não precise ser liberada, a interface "ICorDebugValue" dentro dela precisa ser liberada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugDataTarget](icordebugdatatarget-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
