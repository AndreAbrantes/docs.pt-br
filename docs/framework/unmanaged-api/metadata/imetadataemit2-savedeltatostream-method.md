---
title: Método IMetaDataEmit2::SaveDeltaToStream
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: 7e8376f3a029b0e3ec51a1e7587dd14b3e7530ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177419"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="b89c2-102">Método IMetaDataEmit2::SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="b89c2-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="b89c2-103">Salva alterações da sessão de edição e continuação atual para o fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="b89c2-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b89c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b89c2-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b89c2-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b89c2-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="b89c2-106">[em] Um ponteiro de interface para o fluxo gravável para salvar alterações.</span><span class="sxs-lookup"><span data-stu-id="b89c2-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="b89c2-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="b89c2-107">[in] Reserved.</span></span> <span data-ttu-id="b89c2-108">Esse valor precisa ser zero.</span><span class="sxs-lookup"><span data-stu-id="b89c2-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b89c2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b89c2-109">Requirements</span></span>  
 <span data-ttu-id="b89c2-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b89c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b89c2-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b89c2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b89c2-112">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b89c2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b89c2-113">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b89c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89c2-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b89c2-114">See also</span></span>

- [<span data-ttu-id="b89c2-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b89c2-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="b89c2-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b89c2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
