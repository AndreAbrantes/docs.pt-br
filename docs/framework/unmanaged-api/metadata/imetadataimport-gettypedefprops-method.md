---
title: Método IMetaDataImport::GetTypeDefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: 9dd973fe3e0802c49c220db51a21c223730e5aec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729155"
---
# <a name="imetadataimportgettypedefprops-method"></a>Método IMetaDataImport::GetTypeDefProps

Retorna informações de metadados para o <xref:System.Type> representado pelo token de TypeDef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `td`  
 no O token de TypeDef que representa o tipo para o qual retornar metadados.  
  
 `szTypeDef`  
 fora Um buffer que contém o nome do tipo.  
  
 `cchTypeDef`  
 no O tamanho em caracteres largos de `szTypeDef` .  
  
 `pchTypeDef`  
 fora O número de caracteres largos retornados em `szTypeDef` .  
  
 `pdwTypeDefFlags`  
 fora Um ponteiro para quaisquer sinalizadores que modificam a definição de tipo. Esse valor é um bitmask da enumeração [CorTypeAttr](cortypeattr-enumeration.md) .  
  
 `ptkExtends`  
 fora Um token de metadados TypeDef ou TypeRef que representa o tipo base do tipo solicitado.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso no MsCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](imetadataimport-interface.md)
- [Interface IMetaDataImport2](imetadataimport2-interface.md)
