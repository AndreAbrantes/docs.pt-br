---
title: Método ICorDebugModule::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: c2aecadf8688e763a69bd40ca877e44bc0ce5c29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710020"
---
# <a name="icordebugmodulegetname-method"></a>Método ICorDebugModule::GetName

Obtém o nome do arquivo do módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `cchname`  
 no O tamanho da `szName` matriz.  
  
 `pcchName`  
 no Um ponteiro para o comprimento do nome retornado.  
  
 `szName`  
 fora Uma matriz que armazena o nome retornado.  
  
## <a name="remarks"></a>Comentários  

 O `GetName` método retornará um S_OK HRESULT se o nome do arquivo do módulo corresponder ao nome no disco. `GetName` Retorna um S_FALSE HRESULT se o nome for criei, como para um módulo dinâmico ou na memória.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também
