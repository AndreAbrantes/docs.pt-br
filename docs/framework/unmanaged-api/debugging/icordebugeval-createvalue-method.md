---
title: Método ICorDebugEval::CreateValue
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: 41db6ac00d8646651d0e8433d076c37af6020071
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696148"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="2e1d0-102">Método ICorDebugEval::CreateValue</span><span class="sxs-lookup"><span data-stu-id="2e1d0-102">ICorDebugEval::CreateValue Method</span></span>

<span data-ttu-id="2e1d0-103">Cria um valor do tipo especificado, com um valor inicial de zero ou NULL.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="2e1d0-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="2e1d0-105">Use [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-105">Use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e1d0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e1d0-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e1d0-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e1d0-107">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="2e1d0-108">no Um valor da enumeração [CorElementType](../metadata/corelementtype-enumeration.md) que especifica o tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-108">[in] A value of the [CorElementType](../metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="2e1d0-109">no Ponteiro para um objeto [ICorDebugClass](icordebugclass-interface.md) que especifica a classe do valor, se o tipo não for um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-109">[in] Pointer to an [ICorDebugClass](icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="2e1d0-110">fora Ponteiro para o endereço de um objeto "ICorDebugValue" que representa o valor.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e1d0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e1d0-111">Remarks</span></span>  

 <span data-ttu-id="2e1d0-112">`CreateValue` Cria um `ICorDebugValue` objeto do tipo fornecido para o único propósito de usá-lo em uma avaliação de função.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="2e1d0-113">Esse objeto de valor pode ser usado para passar constantes de usuário como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="2e1d0-114">Se o tipo do valor for um tipo primitivo, seu valor inicial será zero ou NULL.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="2e1d0-115">Use [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) para definir o valor de um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-115">Use [ICorDebugGenericValue::SetValue](icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="2e1d0-116">Se o valor de `elementType` for ELEMENT_TYPE_CLASS, você obterá um "ICorDebugReferenceValue" (retornado em `ppValue` ) que representa a referência de objeto nulo.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="2e1d0-117">Você pode usar esse objeto para passar NULL para uma avaliação de função que tem parâmetros de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="2e1d0-118">Você não pode definir `ICorDebugValue` como qualquer coisa; ela sempre permanece nula.</span><span class="sxs-lookup"><span data-stu-id="2e1d0-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e1d0-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e1d0-119">Requirements</span></span>  

 <span data-ttu-id="2e1d0-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e1d0-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e1d0-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e1d0-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e1d0-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e1d0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e1d0-123">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="2e1d0-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e1d0-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e1d0-124">See also</span></span>

- [<span data-ttu-id="2e1d0-125">Método CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="2e1d0-125">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="2e1d0-126">Interface ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="2e1d0-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
