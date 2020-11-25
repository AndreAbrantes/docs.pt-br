---
title: Método ICorDebugProcess::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: 87b7b7381ef53f7e2abebc053b5c9f87f94d96c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695056"
---
# <a name="icordebugprocessgethandle-method"></a>Método ICorDebugProcess::GetHandle

Obtém um identificador para o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `phProcessHandle`  
 fora Um ponteiro para um `HPROCESS` que é o identificador para o processo.  
  
## <a name="remarks"></a>Comentários  

 O identificador recuperado pertence à interface de depuração. O depurador deve duplicar o identificador antes de usá-lo.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
