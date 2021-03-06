---
title: Método ICorDebugNativeFrame2::IsMatchingParentFrame
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: 213bee96531fa0bbc9bf0ae76b2505019833abfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724696"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>Método ICorDebugNativeFrame2::IsMatchingParentFrame

Determina se o quadro especificado é o pai do quadro atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pPotentialParentFrame`  
 no Um ponteiro para o objeto de quadro que você deseja avaliar para o status pai.  
  
 `pIsParent`  
 [fora] `true` Se `pPotentialParentFrame` for o pai do quadro atual; caso contrário, `false` .  
  
## <a name="return-value"></a>Valor Retornado  

 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O status pai foi retornado com êxito.|  
|E_FAIL|Não foi possível retornar o status pai.|  
|E_INVALIDARG|`pPotentialParentFrame` ou `pIsParent` é nulo.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  

 `IsMatchingParentFrame` retorna `true` se o objeto frame que você passa para o método é o pai do objeto frame no qual o método foi chamado. Se você chamar o método em um quadro que não seja um filho do quadro especificado, ele retornará um erro.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
