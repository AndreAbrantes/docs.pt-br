---
title: Estrutura CorDebugGuidToTypeMapping
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugGuidToTypeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGuidToTypeMapping
helpviewer_keywords: CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4c829f4a74c3d2e84a070dfbe5d35d89b1b7ae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugguidtotypemapping-structure"></a>Estrutura CorDebugGuidToTypeMapping
Mapeia um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID correspondente ao objeto ICorDebugType.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`iid`|O GUID do cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipo.|  
|`pType`|Um ponteiro para um objeto de ICorDebugType que fornece informações sobre o tipo de cache.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
