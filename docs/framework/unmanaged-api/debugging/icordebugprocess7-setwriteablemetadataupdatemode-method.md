---
title: ICorDebugProcess7::Método SetWriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 5671f8cb51210c27dffdedba28b4b145b3fedc55
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732548"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::Método SetWriteableMetadataUpdateMode

[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Configura como o depurador lida com atualizações em memória para metadados dentro do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `flags`  
 Um valor de enumeração [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) que especifica se as atualizações na memória para os metadados no processo de destino são visíveis ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) ou não visíveis ( `WriteableMetadataUpdateMode::LegacyCompatPolicy` ) para o depurador.  
  
## <a name="remarks"></a>Comentários  

 As atualizações para metadados do processo de destino podem ser obtidas de Editar e Continuar, um criador de perfil ou <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugProcess7](icordebugprocess7-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
