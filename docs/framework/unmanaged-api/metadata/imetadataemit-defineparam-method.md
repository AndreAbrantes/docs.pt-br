---
title: Método IMetaDataEmit::DefineParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 5b3f89bb14be0d7128682f8702548545b1e50928
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719522"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="666a5-102">Método IMetaDataEmit::DefineParam</span><span class="sxs-lookup"><span data-stu-id="666a5-102">IMetaDataEmit::DefineParam Method</span></span>

<span data-ttu-id="666a5-103">Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e Obtém um token para essa definição de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="666a5-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="666a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="666a5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="666a5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="666a5-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="666a5-106">no O token para o método cujo parâmetro está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="666a5-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="666a5-107">no O número de sequência do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="666a5-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="666a5-108">no O nome do parâmetro em Unicode.</span><span class="sxs-lookup"><span data-stu-id="666a5-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="666a5-109">no Sinalizadores para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="666a5-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="666a5-110">Esta é uma bitmask de `CorParamAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="666a5-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="666a5-111">[in] `ELEMENT_TYPE_` *\** para o valor constante.</span><span class="sxs-lookup"><span data-stu-id="666a5-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="666a5-112">no O valor da constante para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="666a5-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="666a5-113">no O tamanho, em caracteres Unicode, de `pValue` .</span><span class="sxs-lookup"><span data-stu-id="666a5-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="666a5-114">fora O `mdParamDef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="666a5-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="666a5-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="666a5-115">Remarks</span></span>  

 <span data-ttu-id="666a5-116">Os valores de sequência em `ulParamSeq` começam com 1 para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="666a5-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="666a5-117">Um valor de retorno tem um número de sequência de 0.</span><span class="sxs-lookup"><span data-stu-id="666a5-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="666a5-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="666a5-118">Requirements</span></span>  

 <span data-ttu-id="666a5-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="666a5-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="666a5-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="666a5-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="666a5-121">**Biblioteca:** Usado como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="666a5-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="666a5-122">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="666a5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666a5-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="666a5-123">See also</span></span>

- [<span data-ttu-id="666a5-124">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="666a5-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="666a5-125">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="666a5-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
