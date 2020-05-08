---
title: Método ICorDebugEval2::CallParameterizedFunction
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: 72bcc2479f7b6f41b384fc2517f0b04694663398
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976142"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="6e62e-102">Método ICorDebugEval2::CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="6e62e-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="6e62e-103">Define uma chamada para o ICorDebugFunction especificado, que pode ser aninhado dentro de uma classe cujo construtor <xref:System.Type> usa parâmetros ou pode usar <xref:System.Type> parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6e62e-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e62e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e62e-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e62e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e62e-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="6e62e-106">no Um ponteiro para um `ICorDebugFunction` objeto que representa a função a ser chamada.</span><span class="sxs-lookup"><span data-stu-id="6e62e-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="6e62e-107">no O número de argumentos que a função usa.</span><span class="sxs-lookup"><span data-stu-id="6e62e-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="6e62e-108">no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugType que representa um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="6e62e-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="6e62e-109">no O número de valores passados na função.</span><span class="sxs-lookup"><span data-stu-id="6e62e-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="6e62e-110">no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugValue que representa um valor passado em um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="6e62e-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e62e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e62e-111">Remarks</span></span>  
 <span data-ttu-id="6e62e-112">`CallParameterizedFunction`é como [ICorDebugEval:: CallFunction](icordebugeval-callfunction-method.md) , exceto que a função pode estar dentro de uma classe com parâmetros de tipo, ela própria pode pegar parâmetros de tipo ou ambos.</span><span class="sxs-lookup"><span data-stu-id="6e62e-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="6e62e-113">Os argumentos de tipo devem ser fornecidos primeiro para a classe e, em seguida, para a função.</span><span class="sxs-lookup"><span data-stu-id="6e62e-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="6e62e-114">Se a função estiver em um domínio de aplicativo diferente, ocorrerá uma transição.</span><span class="sxs-lookup"><span data-stu-id="6e62e-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="6e62e-115">No entanto, todos os argumentos Type e Value devem estar no domínio do aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="6e62e-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="6e62e-116">A avaliação de função pode ser executada somente em cenários limitados.</span><span class="sxs-lookup"><span data-stu-id="6e62e-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="6e62e-117">Se `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` falhar, o HRESULT retornado indicará o motivo mais geral possível para a falha.</span><span class="sxs-lookup"><span data-stu-id="6e62e-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e62e-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e62e-118">Requirements</span></span>  
 <span data-ttu-id="6e62e-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e62e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e62e-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e62e-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e62e-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e62e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e62e-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e62e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
