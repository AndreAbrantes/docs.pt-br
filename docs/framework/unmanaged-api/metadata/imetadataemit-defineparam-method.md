---
title: Método IMetaDataEmit::DefineParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 5b3f89bb14be0d7128682f8702548545b1e50928
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719522"
---
# <a name="imetadataemitdefineparam-method"></a>Método IMetaDataEmit::DefineParam

Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e Obtém um token para essa definição de parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `md`  
 no O token para o método cujo parâmetro está sendo definido.  
  
 `ulParamSeq`  
 no O número de sequência do parâmetro.  
  
 `szName`  
 no O nome do parâmetro em Unicode.  
  
 `dwParamFlags`  
 no Sinalizadores para o parâmetro. Esta é uma bitmask de `CorParamAttr` valores.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** para o valor constante.  
  
 `pValue`  
 no O valor da constante para o parâmetro.  
  
 `cchValue`  
 no O tamanho, em caracteres Unicode, de `pValue` .  
  
 `ppd`  
 fora O `mdParamDef` token atribuído.  
  
## <a name="remarks"></a>Comentários  

 Os valores de sequência em `ulParamSeq` começam com 1 para parâmetros. Um valor de retorno tem um número de sequência de 0.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso no MSCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](imetadataemit-interface.md)
- [Interface IMetaDataEmit2](imetadataemit2-interface.md)
