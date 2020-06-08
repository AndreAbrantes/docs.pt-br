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
ms.openlocfilehash: c2ec907759a25048444ebcc81bf5bb0fd23ced58
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503647"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="5dd58-102">Método IMetaDataImport::FindMethod</span><span class="sxs-lookup"><span data-stu-id="5dd58-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="5dd58-103">Obtém um ponteiro para o token MethodDef do método que está incluído pelo especificado <xref:System.Type> e que tem o nome e a assinatura de metadados especificados.</span><span class="sxs-lookup"><span data-stu-id="5dd58-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dd58-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dd58-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dd58-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5dd58-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5dd58-106">no O `mdTypeDef` token do tipo (uma classe ou interface) que inclui o membro a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="5dd58-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="5dd58-107">Se esse valor for `mdTokenNil` , a pesquisa será feita para uma função global.</span><span class="sxs-lookup"><span data-stu-id="5dd58-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="5dd58-108">no O nome do método a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="5dd58-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5dd58-109">no Um ponteiro para a assinatura de metadados binários do método.</span><span class="sxs-lookup"><span data-stu-id="5dd58-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5dd58-110">no O tamanho em bytes de `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="5dd58-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="5dd58-111">fora Um ponteiro para o token MethodDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="5dd58-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dd58-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5dd58-112">Remarks</span></span>  
 <span data-ttu-id="5dd58-113">Você especifica o método usando sua classe ou interface de delimitadora ( `td` ), seu nome ( `szName` ) e, opcionalmente, sua assinatura ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="5dd58-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="5dd58-114">Pode haver vários métodos com o mesmo nome em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="5dd58-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="5dd58-115">Nesse caso, passe a assinatura do método para localizar a correspondência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="5dd58-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="5dd58-116">A assinatura passada para `FindMethod` deve ter sido gerada no escopo atual, porque as assinaturas estão associadas a um escopo específico.</span><span class="sxs-lookup"><span data-stu-id="5dd58-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="5dd58-117">Uma assinatura pode inserir um token que identifica a classe de circunscrição ou o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="5dd58-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="5dd58-118">O token é um índice na tabela de TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="5dd58-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="5dd58-119">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para entrada no `FindMethod` .</span><span class="sxs-lookup"><span data-stu-id="5dd58-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="5dd58-120">`FindMethod`localiza somente os métodos que foram definidos diretamente na classe ou interface; Ele não encontra os métodos herdados.</span><span class="sxs-lookup"><span data-stu-id="5dd58-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dd58-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5dd58-121">Requirements</span></span>  
 <span data-ttu-id="5dd58-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dd58-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dd58-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5dd58-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5dd58-124">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5dd58-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5dd58-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dd58-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd58-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="5dd58-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="5dd58-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5dd58-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5dd58-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5dd58-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
