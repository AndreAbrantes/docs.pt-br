---
title: Método ICorPublishProcess::IsManaged
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: dfe247bda75c3695c7c09b85729b4e057c13c62d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692625"
---
# <a name="icorpublishprocessismanaged-method"></a>Método ICorPublishProcess::IsManaged

Obtém um valor que indica se o processo referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md) é conhecido por ter código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pbManaged`  
 fora Um ponteiro para um valor booliano que indica se o processo tem código gerenciado. O valor é `true` se o processo tiver código gerenciado; caso contrário, `false` .  
  
## <a name="remarks"></a>Comentários  

 Como a versão atual do `ICorPublishProcess` permite acesso apenas a processos que têm código gerenciado, o `IsManaged` sempre retorna `true` .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorPublishProcess](icorpublishprocess-interface.md)
