---
title: Método IMetaDataEmit::TranslateSigWithScope
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: 80d33da2eb2a7f0cfbe5dcb7279fff9973dada2e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712918"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="501fa-102">Método IMetaDataEmit::TranslateSigWithScope</span><span class="sxs-lookup"><span data-stu-id="501fa-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>

<span data-ttu-id="501fa-103">Importa um assembly para o escopo atual e obtém uma nova assinatura de metadados para o escopo mesclado.</span><span class="sxs-lookup"><span data-stu-id="501fa-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="501fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="501fa-104">Syntax</span></span>  
  
```cpp  
HRESULT TranslateSigWithScope (
    [in]  IMetaDataAssemblyImport   *pAssemImport,
    [in]  const void                *pbHashValue,
    [in]  ULONG                     cbHashValue,
    [in]  IMetaDataImport           *import,
    [in]  PCCOR_SIGNATURE           pbSigBlob,
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,
    [in]  IMetaDataEmit             *emit,
    [out] PCOR_SIGNATURE            pvTranslatedSig,
    [in]  ULONG                     cbTranslatedSigMax,
    [out] ULONG                     *pcbTranslatedSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="501fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="501fa-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="501fa-106">no A interface para importar assembly (onde a assinatura é definida).</span><span class="sxs-lookup"><span data-stu-id="501fa-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="501fa-107">no O blob de hash para o assembly.</span><span class="sxs-lookup"><span data-stu-id="501fa-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="501fa-108">no A contagem de bytes em `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="501fa-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="501fa-109">no A interface para o escopo de metadados de importação.</span><span class="sxs-lookup"><span data-stu-id="501fa-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="501fa-110">no A assinatura a ser importada.</span><span class="sxs-lookup"><span data-stu-id="501fa-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="501fa-111">no O tamanho, em bytes, de `pbSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="501fa-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="501fa-112">no A interface para o assembly de exportação.</span><span class="sxs-lookup"><span data-stu-id="501fa-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="501fa-113">no A interface para o escopo de metadados de exportação.</span><span class="sxs-lookup"><span data-stu-id="501fa-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="501fa-114">fora O buffer para armazenar o blob de assinatura traduzido.</span><span class="sxs-lookup"><span data-stu-id="501fa-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="501fa-115">no A capacidade, em bytes, de `pvTranslatedSig` .</span><span class="sxs-lookup"><span data-stu-id="501fa-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="501fa-116">fora O número de bytes reais na assinatura traduzida.</span><span class="sxs-lookup"><span data-stu-id="501fa-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="501fa-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="501fa-117">Requirements</span></span>  

 <span data-ttu-id="501fa-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="501fa-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="501fa-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="501fa-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="501fa-120">**Biblioteca:** Usado como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="501fa-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="501fa-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="501fa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="501fa-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="501fa-122">See also</span></span>

- [<span data-ttu-id="501fa-123">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="501fa-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="501fa-124">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="501fa-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="501fa-125">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="501fa-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="501fa-126">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="501fa-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="501fa-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="501fa-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
