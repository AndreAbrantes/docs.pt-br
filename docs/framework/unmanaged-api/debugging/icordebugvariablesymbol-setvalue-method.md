---
title: 'Método ICorDebugVariableSymbol:: SetValue'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: 3ef9b9b9a095d6d6026ffc38873661355d660488
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707835"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>Método ICorDebugVariableSymbol:: SetValue

Atribui o valor de uma matriz de bytes a uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `offset`  
 no O deslocamento inicial na variável na qual definir o valor. Esse parâmetro é usado ao gravar em campos de membro em um objeto.  
  
 `threadID`  
 no O identificador de thread do thread cujo contexto deve ser atualizado para refletir o novo valor.  
  
 `cbContext`  
 no O tamanho em bytes do contexto do thread.  
  
 `context`  
 no O contexto de thread usado para gravar o valor.  
  
 `cbValue`  
 no O tamanho em bytes do `pValue` buffer.  
  
 `pValue`  
 no O buffer que contém o valor a ser definido.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
