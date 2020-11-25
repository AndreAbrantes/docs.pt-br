---
title: Método ICorDebugType::GetStaticFieldValue
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 281b9f46194e93220f47ef8aadbf29ce03084582
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711933"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="e3037-102">Método ICorDebugType::GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="e3037-102">ICorDebugType::GetStaticFieldValue Method</span></span>

<span data-ttu-id="e3037-103">Obtém um ponteiro de interface para um objeto ICorDebugValue que contém o valor do campo estático referenciado pelo token de campo especificado no quadro de ativação especificado.</span><span class="sxs-lookup"><span data-stu-id="e3037-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3037-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3037-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3037-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3037-105">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="e3037-106">no Um `mdFieldDef` token que especifica o campo estático.</span><span class="sxs-lookup"><span data-stu-id="e3037-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="e3037-107">no Um ponteiro para um ICorDebugFrame que representa o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="e3037-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e3037-108">fora Um ponteiro para o endereço de um `ICorDebugValue` que contém o valor do campo estático.</span><span class="sxs-lookup"><span data-stu-id="e3037-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3037-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3037-109">Remarks</span></span>  

 <span data-ttu-id="e3037-110">O `GetStaticFieldValue` método poderá ser usado somente se o tipo for ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, conforme indicado pelo método [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e3037-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="e3037-111">Para tipos não genéricos, a operação executada pelo `GetStaticFieldValue` é idêntica à chamada de [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) no objeto ICorDebugClass retornado por [ICorDebugType:: GetClass](icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="e3037-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="e3037-112">Para tipos genéricos, um valor de campo estático será relativo a uma instanciação específica.</span><span class="sxs-lookup"><span data-stu-id="e3037-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="e3037-113">Além disso, se o campo estático puder ser relativo a um thread, um contexto ou um domínio de aplicativo, o quadro de pilha ajudará o depurador a determinar o valor adequado.</span><span class="sxs-lookup"><span data-stu-id="e3037-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3037-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3037-114">Remarks</span></span>  

 <span data-ttu-id="e3037-115">`GetStaticFieldValue` pode ser usado somente quando uma chamada para `ICorDebugType::GetType` retorna um valor de ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="e3037-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3037-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3037-116">Requirements</span></span>  

 <span data-ttu-id="e3037-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3037-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3037-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3037-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3037-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3037-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3037-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3037-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
