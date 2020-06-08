---
title: Método IMetaDataImport::EnumModuleRefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: fe7350e6d8e400ae37b5b8b7854a56f3c5c53ea7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491735"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="7058c-102">Método IMetaDataImport::EnumModuleRefs</span><span class="sxs-lookup"><span data-stu-id="7058c-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="7058c-103">Enumera tokens ModuleRef que representam módulos importados.</span><span class="sxs-lookup"><span data-stu-id="7058c-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7058c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7058c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7058c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7058c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7058c-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="7058c-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7058c-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="7058c-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="7058c-108">fora A matriz usada para armazenar os tokens de ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="7058c-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7058c-109">no O tamanho máximo da `rModuleRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="7058c-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="7058c-110">fora O número de tokens de ModuleRef retornados em `rModuleRefs` .</span><span class="sxs-lookup"><span data-stu-id="7058c-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7058c-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="7058c-111">Return Value</span></span>  
  
|<span data-ttu-id="7058c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7058c-112">HRESULT</span></span>|<span data-ttu-id="7058c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7058c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7058c-114">`EnumModuleRefs`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7058c-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7058c-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="7058c-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7058c-116">Nesse caso, `pcModuleRefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="7058c-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7058c-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7058c-117">Requirements</span></span>  
 <span data-ttu-id="7058c-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7058c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7058c-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7058c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7058c-120">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7058c-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7058c-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7058c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7058c-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7058c-122">See also</span></span>

- [<span data-ttu-id="7058c-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="7058c-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7058c-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="7058c-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
