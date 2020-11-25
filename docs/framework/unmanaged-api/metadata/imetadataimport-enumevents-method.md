---
title: Método IMetaDataImport::EnumEvents
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: 3a181f1ef29810058c57bdb13338a01aa1fe7dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700464"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="477bd-102">Método IMetaDataImport::EnumEvents</span><span class="sxs-lookup"><span data-stu-id="477bd-102">IMetaDataImport::EnumEvents Method</span></span>

<span data-ttu-id="477bd-103">Enumera os tokens de definição de evento para o token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="477bd-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="477bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="477bd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="477bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="477bd-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="477bd-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="477bd-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="477bd-107">no O token de TypeDef cujas definições de evento devem ser enumeradas.</span><span class="sxs-lookup"><span data-stu-id="477bd-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="477bd-108">fora A matriz de eventos retornados.</span><span class="sxs-lookup"><span data-stu-id="477bd-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="477bd-109">no O tamanho máximo da `rEvents` matriz.</span><span class="sxs-lookup"><span data-stu-id="477bd-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="477bd-110">fora O número real de eventos retornados em `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="477bd-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="477bd-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="477bd-111">Return Value</span></span>  
  
|<span data-ttu-id="477bd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="477bd-112">HRESULT</span></span>|<span data-ttu-id="477bd-113">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="477bd-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="477bd-114">`EnumEvents` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="477bd-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="477bd-115">Não há eventos a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="477bd-115">There are no events to enumerate.</span></span> <span data-ttu-id="477bd-116">Nesse caso, `pcEvents` é zero.</span><span class="sxs-lookup"><span data-stu-id="477bd-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="477bd-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="477bd-117">Requirements</span></span>  

 <span data-ttu-id="477bd-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="477bd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="477bd-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="477bd-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="477bd-120">**Biblioteca:** Incluído como um recurso no MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="477bd-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="477bd-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="477bd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477bd-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="477bd-122">See also</span></span>

- [<span data-ttu-id="477bd-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="477bd-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="477bd-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="477bd-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
