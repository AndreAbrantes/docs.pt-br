---
title: Método ICLRStrongName::StrongNameGetBlobFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: ad5fa510a17a3ce823ff90c4131b349b0d9efd39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671740"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a>Método ICLRStrongName::StrongNameGetBlobFromImage

Obtém uma representação binária da imagem do assembly no endereço de memória especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pbBase`  
 no O endereço de memória do manifesto do assembly mapeado.  
  
 `dwLength`  
 no O tamanho, em bytes, da imagem em `pbBase` .  
  
 `pbBlob`  
 no Um buffer para conter a representação binária da imagem.  
  
 `pcbBlob`  
 [entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob` . No retorno, o tamanho real, em bytes, de `pbBlob` .  
  
## <a name="return-value"></a>Valor Retornado  

 `S_OK` Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso no MSCorEE.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameGetBlob](iclrstrongname-strongnamegetblob-method.md)
- [Interface ICLRStrongName](iclrstrongname-interface.md)
