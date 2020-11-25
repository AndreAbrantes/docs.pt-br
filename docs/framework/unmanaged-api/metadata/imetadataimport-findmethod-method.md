---
title: Método IMetaDataImport::FindMethod
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 111e42a6d8f413c616779bc44e0722ab38781588
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711332"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="ded1a-102">Método IMetaDataImport::FindMethod</span><span class="sxs-lookup"><span data-stu-id="ded1a-102">IMetaDataImport::FindMethod Method</span></span>

<span data-ttu-id="ded1a-103">Obtém um ponteiro para o token MethodDef do método que está incluído pelo especificado <xref:System.Type> e que tem o nome e a assinatura de metadados especificados.</span><span class="sxs-lookup"><span data-stu-id="ded1a-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ded1a-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ded1a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ded1a-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="ded1a-106">no O `mdTypeDef` token do tipo (uma classe ou interface) que inclui o membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="ded1a-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="ded1a-107">Se esse valor for `mdTokenNil` , a pesquisa será feita para uma função global.</span><span class="sxs-lookup"><span data-stu-id="ded1a-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="ded1a-108">no O nome do método a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="ded1a-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ded1a-109">no Um ponteiro para a assinatura de metadados binários do método.</span><span class="sxs-lookup"><span data-stu-id="ded1a-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ded1a-110">no O tamanho em bytes de `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="ded1a-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="ded1a-111">fora Um ponteiro para o token MethodDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="ded1a-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ded1a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ded1a-112">Remarks</span></span>  

 <span data-ttu-id="ded1a-113">Você especifica o método usando sua classe ou interface de delimitadora ( `td` ), seu nome ( `szName` ) e, opcionalmente, sua assinatura ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="ded1a-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="ded1a-114">Pode haver vários métodos com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="ded1a-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="ded1a-115">Nesse caso, passe a assinatura do método para localizar a correspondência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="ded1a-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="ded1a-116">A assinatura passada para `FindMethod` deve ter sido gerada no escopo atual, porque as assinaturas estão associadas a um escopo específico.</span><span class="sxs-lookup"><span data-stu-id="ded1a-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="ded1a-117">Uma assinatura pode inserir um token que identifica a classe de circunscrição ou o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="ded1a-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="ded1a-118">O token é um índice na tabela de TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="ded1a-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="ded1a-119">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para entrada no `FindMethod` .</span><span class="sxs-lookup"><span data-stu-id="ded1a-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="ded1a-120">`FindMethod` localiza somente os métodos que foram definidos diretamente na classe ou interface; Ele não encontra os métodos herdados.</span><span class="sxs-lookup"><span data-stu-id="ded1a-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded1a-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ded1a-121">Requirements</span></span>  

 <span data-ttu-id="ded1a-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ded1a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded1a-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ded1a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ded1a-124">**Biblioteca:** Incluído como um recurso no MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ded1a-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ded1a-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ded1a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded1a-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="ded1a-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="ded1a-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ded1a-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ded1a-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ded1a-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
