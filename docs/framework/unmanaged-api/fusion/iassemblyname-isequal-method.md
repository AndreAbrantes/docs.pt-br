---
title: Método IAssemblyName::IsEqual
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
ms.openlocfilehash: 0fabf8159c2626d4e1716e3be60baaf1ec834032
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712970"
---
# <a name="iassemblynameisequal-method"></a>Método IAssemblyName::IsEqual

Determina se um objeto [IAssemblyName](iassemblyname-interface.md) especificado é igual a este `IAssemblyName` , com base nos sinalizadores de comparação especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pName`  
 no O `IAssemblyName` objeto para o qual comparar `IAssemblyName` .  
  
 `dwCmpFlags`  
 no Uma combinação de bits de [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) de valores que influencia a comparação.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Versões do .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IAssemblyName](iassemblyname-interface.md)
- [Enumerações Fusion](fusion-enumerations.md)
