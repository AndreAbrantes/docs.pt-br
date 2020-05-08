---
title: Método ICorDebugEval2::CreateValueForType
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: fd7acaa8bcb4d53893855bcd25ff68cf26e30354
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976155"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="1d635-102">Método ICorDebugEval2::CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="1d635-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="1d635-103">Obtém um ponteiro para um novo ICorDebugValue do tipo especificado, com um valor inicial de zero ou NULL.</span><span class="sxs-lookup"><span data-stu-id="1d635-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d635-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d635-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d635-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d635-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="1d635-106">no Ponteiro para um objeto ICorDebugType que representa o tipo.</span><span class="sxs-lookup"><span data-stu-id="1d635-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1d635-107">fora Ponteiro para o endereço de um `ICorDebugValue` objeto que representa o valor.</span><span class="sxs-lookup"><span data-stu-id="1d635-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d635-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d635-108">Remarks</span></span>  
 <span data-ttu-id="1d635-109">`CreateValueForType`generaliza [ICorDebugEval:: CreateValue](icordebugeval-createvalue-method.md) permitindo que você especifique um tipo de objeto arbitrário, incluindo tipos construídos, como `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="1d635-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="1d635-110">A única finalidade desse método é gerar um valor que possa ser passado para uma avaliação de função.</span><span class="sxs-lookup"><span data-stu-id="1d635-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="1d635-111">O tipo deve ser uma classe ou um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="1d635-111">The type must be a class or a value type.</span></span> <span data-ttu-id="1d635-112">Você não pode usar esse método para criar valores de matriz ou de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d635-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d635-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d635-113">Requirements</span></span>  
 <span data-ttu-id="1d635-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d635-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d635-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d635-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d635-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d635-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d635-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d635-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
