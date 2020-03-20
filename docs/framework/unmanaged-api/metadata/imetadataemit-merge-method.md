---
title: Método IMetaDataEmit::Merge
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175701"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="b68bf-102">Método IMetaDataEmit::Merge</span><span class="sxs-lookup"><span data-stu-id="b68bf-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="b68bf-103">Adiciona o escopo importado especificado à lista de escopos a serem mesclados.</span><span class="sxs-lookup"><span data-stu-id="b68bf-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b68bf-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b68bf-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b68bf-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="b68bf-106">[em] Um ponteiro para um objeto [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que identifica o escopo importado a ser mesclado.</span><span class="sxs-lookup"><span data-stu-id="b68bf-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="b68bf-107">[em] Um ponteiro para um objeto [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) que especifica o remapa do token.</span><span class="sxs-lookup"><span data-stu-id="b68bf-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="b68bf-108">[em] Um ponteiro para um objeto [IUnknown](/cpp/atl/iunknown) que especifica os erros.</span><span class="sxs-lookup"><span data-stu-id="b68bf-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b68bf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b68bf-109">Remarks</span></span>  
 <span data-ttu-id="b68bf-110">Chamada [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) para desencadear a fusão de metadados em um único escopo.</span><span class="sxs-lookup"><span data-stu-id="b68bf-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b68bf-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b68bf-111">Requirements</span></span>  
 <span data-ttu-id="b68bf-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b68bf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68bf-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b68bf-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b68bf-114">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b68bf-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b68bf-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68bf-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b68bf-116">See also</span></span>

- [<span data-ttu-id="b68bf-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b68bf-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b68bf-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b68bf-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
