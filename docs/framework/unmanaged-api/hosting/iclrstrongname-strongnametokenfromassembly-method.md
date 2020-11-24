---
title: Método ICLRStrongName::StrongNameTokenFromAssembly
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: 90a7e60e35e1fc555681102ffa62967eb5ac01fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671532"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="9bccb-102">Método ICLRStrongName::StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="9bccb-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>

<span data-ttu-id="9bccb-103">Cria um token de nome forte do arquivo do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="9bccb-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bccb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bccb-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bccb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bccb-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="9bccb-106">no O caminho para o arquivo executável portátil (PE) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="9bccb-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="9bccb-107">fora O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="9bccb-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="9bccb-108">fora O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="9bccb-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bccb-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="9bccb-109">Return Value</span></span>  

 <span data-ttu-id="9bccb-110">`S_OK` Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="9bccb-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bccb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bccb-111">Remarks</span></span>  

 <span data-ttu-id="9bccb-112">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="9bccb-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="9bccb-113">O token é um hash de 64 bits que é criado a partir da chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="9bccb-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="9bccb-114">O token é uma parte do nome forte para o assembly e pode ser lido nos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="9bccb-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="9bccb-115">Depois que o token é criado, você deve chamar o método [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="9bccb-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bccb-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bccb-116">Requirements</span></span>  

 <span data-ttu-id="9bccb-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bccb-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bccb-118">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9bccb-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9bccb-119">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bccb-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bccb-120">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bccb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bccb-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="9bccb-121">See also</span></span>

- [<span data-ttu-id="9bccb-122">Método StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="9bccb-122">StrongNameTokenFromAssemblyEx Method</span></span>](iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="9bccb-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9bccb-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
