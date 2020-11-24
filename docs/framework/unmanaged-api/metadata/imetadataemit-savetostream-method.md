---
title: Método IMetaDataEmit::SaveToStream
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 3f8da08b96c47c90ecccae28dd1662a7abffaf1d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688556"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="7fd48-102">Método IMetaDataEmit::SaveToStream</span><span class="sxs-lookup"><span data-stu-id="7fd48-102">IMetaDataEmit::SaveToStream Method</span></span>

<span data-ttu-id="7fd48-103">Salva todos os metadados no escopo atual para o especificado `IStream` .</span><span class="sxs-lookup"><span data-stu-id="7fd48-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fd48-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fd48-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fd48-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fd48-105">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="7fd48-106">no O fluxo gravável no qual salvar.</span><span class="sxs-lookup"><span data-stu-id="7fd48-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="7fd48-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="7fd48-107">[in] Reserved.</span></span> <span data-ttu-id="7fd48-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="7fd48-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fd48-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fd48-109">Requirements</span></span>  

 <span data-ttu-id="7fd48-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fd48-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fd48-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7fd48-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7fd48-112">**Biblioteca:** Usado como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7fd48-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fd48-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fd48-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd48-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="7fd48-114">See also</span></span>

- [<span data-ttu-id="7fd48-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7fd48-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7fd48-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7fd48-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
