---
title: Método ICLRMetadataLocator::GetMetadata
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: f0ba2342e9704ba06dd1d3612f699298c734a5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723513"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>Método ICLRMetadataLocator::GetMetadata

Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para recuperar os metadados de uma imagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `imagePath`  
 no Uma cadeia de caracteres que especifica o caminho do arquivo de imagem.  
  
 `imageTimestamp`  
 no O carimbo de data/hora do arquivo de imagem.  
  
 `imageSize`  
 no O tamanho do arquivo de imagem.  
  
 `mvid`  
 no O identificador global exclusivo da imagem.  
  
 `mdRva`  
 no O endereço virtual relativo (RVA) dos metadados. O endereço é relativo ao endereço base da imagem.  
  
 `flags`  
 no Reservado para uso futuro.  
  
 `bufferSize`  
 no O tamanho do buffer no qual os metadados são colocados.  
  
 `buffer`  
 fora O buffer no qual os metadados são colocados.  
  
 `dataSize`  
 fora O tamanho dos metadados retornados.  
  
## <a name="remarks"></a>Comentários  

 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRMetadataLocator](iclrmetadatalocator-interface.md)
