---
title: 'Método ICorDebugSymbolProvider:: GetInstanceFieldSymbols'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 1a74b355b695f65166d0fe63bbdd41d789db5cfe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730858"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a>Método ICorDebugSymbolProvider:: GetInstanceFieldSymbols

Obtém os símbolos de campo de instância que correspondem a uma assinatura de TypeSpec.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `cbSignature`  
 no O número de bytes na `typeSig` matriz.  
  
 `typeSig`  
 no Uma matriz de bytes que contém a `typespec` assinatura.  
  
 `cRequestedSymbols`  
 no O número de símbolos solicitados.  
  
 `pcFetchedSymbols`  
 fora Um ponteiro para o número de símbolos recuperados pelo método.  
  
 `pSymbols`  
 fora Um ponteiro para uma matriz [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) que contém os símbolos de campo de instância solicitados.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetStaticFieldSymbols](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
