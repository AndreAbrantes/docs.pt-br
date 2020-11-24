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
ms.openlocfilehash: 2d53eebcc272ab87a2af5b3c081ca37dde5c74b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674457"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="d52b5-102">Método ICLRStrongName::StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="d52b5-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>

<span data-ttu-id="d52b5-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="d52b5-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d52b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d52b5-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d52b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d52b5-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="d52b5-106">no O caminho para o arquivo executável portátil (. dll ou. exe) para o assembly verificar.</span><span class="sxs-lookup"><span data-stu-id="d52b5-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="d52b5-107">no Sinalizadores para modificar o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="d52b5-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="d52b5-108">Os seguintes valores têm suporte:</span><span class="sxs-lookup"><span data-stu-id="d52b5-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="d52b5-109">`SN_INFLAG_FORCE_VER` (0x00000001) – força a verificação mesmo que seja necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="d52b5-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="d52b5-110">`SN_INFLAG_INSTALL` (0x00000002) – especifica que esta é a primeira vez que o manifesto é verificado.</span><span class="sxs-lookup"><span data-stu-id="d52b5-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="d52b5-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) – especifica que o cache permitirá acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="d52b5-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="d52b5-112">`SN_INFLAG_USER_ACCESS` (0x00000008) – especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="d52b5-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="d52b5-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) – especifica que o cache não oferecerá nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="d52b5-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="d52b5-114">`SN_INFLAG_RUNTIME` (0x80000000)-reservado para depuração interna.</span><span class="sxs-lookup"><span data-stu-id="d52b5-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="d52b5-115">fora Sinalizadores que indicam se a assinatura de nome forte foi verificada.</span><span class="sxs-lookup"><span data-stu-id="d52b5-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="d52b5-116">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="d52b5-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="d52b5-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-esse valor é definido como `false` para especificar que a verificação foi bem-sucedida devido a configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="d52b5-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d52b5-118">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="d52b5-118">Return Value</span></span>  

 <span data-ttu-id="d52b5-119">`S_OK` Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="d52b5-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d52b5-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d52b5-120">Requirements</span></span>  

 <span data-ttu-id="d52b5-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d52b5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d52b5-122">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d52b5-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d52b5-123">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d52b5-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d52b5-124">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d52b5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d52b5-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="d52b5-125">See also</span></span>

- [<span data-ttu-id="d52b5-126">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="d52b5-126">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="d52b5-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d52b5-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
