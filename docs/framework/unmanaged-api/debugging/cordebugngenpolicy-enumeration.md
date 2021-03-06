---
title: Enumeração CorDebugNGenPolicy
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: b64de0fa2ecbddd2decf69a4099d9897ec42a563
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696421"
---
# <a name="cordebugngenpolicy-enumeration"></a>Enumeração CorDebugNGenPolicy

Fornece um valor que determina se um depurador carrega imagens nativas (NGen) do cache de imagens nativas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Membros  
  
|Nome do membro|DESCRIÇÃO|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|Em um aplicativo da loja do Windows 8. x, o uso de imagens do cache de imagem nativa local está desabilitado. Em um aplicativo de área de trabalho, essa configuração não tem efeito.|  
  
## <a name="remarks"></a>Comentários  

 A `CorDebugNGENPolicy` enumeração é usada pelo método [ICorDebugProcess5:: EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) . A desabilitação do uso de imagens do cache de imagem nativa local fornece uma experiência de depuração consistente, garantindo que o depurador Carregue imagens depurável compiladas por JIT em vez de imagens nativas otimizadas.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Declarando enumerações](debugging-enumerations.md)
