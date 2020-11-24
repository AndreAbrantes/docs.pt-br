---
title: Método IMetaDataAssemblyEmit::DefineFile
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 1dd71dbe0ddb894cb5ed05c32e50429d27c66aa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689323"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="829b3-102">Método IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="829b3-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>

<span data-ttu-id="829b3-103">Cria uma `File` estrutura de metadados que contém metadados para o assembly referenciado por esse assembly e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="829b3-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="829b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="829b3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="829b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="829b3-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="829b3-106">no O nome do arquivo a ser consumido.</span><span class="sxs-lookup"><span data-stu-id="829b3-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="829b3-107">no Um ponteiro para os dados de hash associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="829b3-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="829b3-108">no O tamanho em bytes de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="829b3-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="829b3-109">no Uma combinação de bits de `FileFlags` valores que especifica as configurações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="829b3-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="829b3-110">fora Um ponteiro para o `File` token retornado.</span><span class="sxs-lookup"><span data-stu-id="829b3-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="829b3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="829b3-111">Remarks</span></span>  

 <span data-ttu-id="829b3-112">Uma `File` estrutura de metadados deve ser definida para cada arquivo que faz parte desse assembly no momento em que esse assembly foi criado, excluindo o arquivo que contém os metadados.</span><span class="sxs-lookup"><span data-stu-id="829b3-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="829b3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="829b3-113">Requirements</span></span>  

 <span data-ttu-id="829b3-114">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="829b3-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="829b3-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="829b3-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="829b3-116">**Biblioteca:** Usado como um recurso no MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="829b3-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="829b3-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="829b3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="829b3-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="829b3-118">See also</span></span>

- [<span data-ttu-id="829b3-119">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="829b3-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
