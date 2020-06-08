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
ms.openlocfilehash: a8f46871dde4c664a502c261fc882f3badf0f362
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492734"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="96e3b-102">Método IMetaDataEmit2::SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="96e3b-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="96e3b-103">Salva as alterações da sessão de edição e continuação atual para o fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="96e3b-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96e3b-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96e3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96e3b-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="96e3b-106">no Um ponteiro de interface para o fluxo gravável no qual salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="96e3b-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="96e3b-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="96e3b-107">[in] Reserved.</span></span> <span data-ttu-id="96e3b-108">Esse valor precisa ser zero.</span><span class="sxs-lookup"><span data-stu-id="96e3b-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e3b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96e3b-109">Requirements</span></span>  
 <span data-ttu-id="96e3b-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96e3b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e3b-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="96e3b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96e3b-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="96e3b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96e3b-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e3b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e3b-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="96e3b-114">See also</span></span>

- [<span data-ttu-id="96e3b-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="96e3b-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="96e3b-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="96e3b-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
