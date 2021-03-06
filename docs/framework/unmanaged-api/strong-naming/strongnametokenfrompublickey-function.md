---
title: Função StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 89556cf0e1ef65c35278a526e10fc791063ea2c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708342"
---
# <a name="strongnametokenfrompublickey-function"></a>Função StrongNameTokenFromPublicKey

Obtém um token que representa uma chave pública. Um token de nome forte é a forma abreviada de uma chave pública.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parâmetros  

 `pbPublicKeyBlob`  
 no Uma estrutura do tipo [PublicKeyBlob](publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.  
  
 `cbPublicKeyBlob`  
 no O tamanho, em bytes, de `pbPublicKeyBlob` .  
  
 `ppbStrongNameToken`  
 fora O token de nome forte correspondente à chave passada `pbPublicKeyBlob` . O Common Language Runtime aloca a memória na qual retornar o token. O chamador deve liberar essa memória usando a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .  
  
 `pcbStrongNameToken`  
 fora O tamanho, em bytes, do token de nome forte retornado.  
  
## <a name="return-value"></a>Valor Retornado  

 `true` após a conclusão bem-sucedida; caso contrário, `false` .  
  
## <a name="remarks"></a>Comentários  

 Um token de nome forte é a forma abreviada de uma chave pública usada para economizar espaço ao armazenar informações de chave em metadados. Especificamente, tokens de nome forte são usados em referências de assembly para fazer referência ao assembly dependente.  
  
 Se a `StrongNameTokenFromPublicKey` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName. h  
  
 **Biblioteca:** Incluído como um recurso no mscoree.dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [Método StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [Estrutura PublicKeyBlob](publickeyblob-structure.md)
