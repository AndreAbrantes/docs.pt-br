---
title: Método ICLRStrongName::StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: 6375fd8e4a314403267a4cdf2e8356677e9e7a06
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899485"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a>Método ICLRStrongName::StrongNameSignatureVerification
Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 no O caminho para o arquivo executável portátil (. dll ou. exe) para o assembly verificar.  
  
 `dwInFlags`  
 no Sinalizadores para modificar o comportamento de verificação. Os valores a seguir têm suporte:  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) – força a verificação mesmo que seja necessário substituir as configurações do registro.  
  
- `SN_INFLAG_INSTALL` (0x00000002) – especifica que esta é a primeira vez que o manifesto é verificado.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) – especifica que o cache permitirá acesso somente aos usuários que têm privilégios administrativos.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) – especifica que o assembly será acessível somente para o usuário atual.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) – especifica que o cache não fornecerá nenhuma garantia de restrição de acesso.  
  
- `SN_INFLAG_RUNTIME` (0x80000000) – reservado para depuração interna.  
  
 `pdwOutFlags`  
 fora Sinalizadores que indicam se a assinatura de nome forte foi verificada. Há suporte para o seguinte valor:  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-esse valor é definido como `false` para especificar que a verificação foi bem-sucedida devido às configurações do registro.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
