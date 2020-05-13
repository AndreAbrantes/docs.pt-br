---
title: Método ICorDebugModule2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: d5109043a8601d7997f52e88ea472644f1b9ca03
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208740"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="4f751-102">Método ICorDebugModule2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="4f751-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="4f751-103">Define o status de Apenas Meu Código (JMC) de todos os métodos de todas as classes nesse ICorDebugModule2 para o valor especificado, exceto aqueles na `pTokens` matriz, que ele define para o valor oposto.</span><span class="sxs-lookup"><span data-stu-id="4f751-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f751-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f751-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f751-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f751-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="4f751-106">no Defina como `true` se o código deve ser depurado; caso contrário, defina como `false` .</span><span class="sxs-lookup"><span data-stu-id="4f751-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="4f751-107">no O tamanho da `pTokens` matriz.</span><span class="sxs-lookup"><span data-stu-id="4f751-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="4f751-108">no Uma matriz de `mdToken` valores, cada um dos quais se refere a um método que terá seu status JMC definido como! `bIsJustMycode` .</span><span class="sxs-lookup"><span data-stu-id="4f751-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f751-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f751-109">Remarks</span></span>  
 <span data-ttu-id="4f751-110">O status de JMC de cada método especificado na `pTokens` matriz é definido como o oposto do `bIsJustMycode` valor.</span><span class="sxs-lookup"><span data-stu-id="4f751-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="4f751-111">O status de todos os outros métodos neste módulo é definido como o `bIsJustMycode` valor.</span><span class="sxs-lookup"><span data-stu-id="4f751-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="4f751-112">O `SetJMCStatus` método apaga todas as configurações de JMC anteriores neste módulo.</span><span class="sxs-lookup"><span data-stu-id="4f751-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="4f751-113">O `SetJMCStatus` método retornará um S_OK HRESULT se todas as funções tiverem sido definidas com êxito.</span><span class="sxs-lookup"><span data-stu-id="4f751-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="4f751-114">Ele retornará um CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT se algumas funções marcadas `true` não forem depurável.</span><span class="sxs-lookup"><span data-stu-id="4f751-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f751-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f751-115">Requirements</span></span>  
 <span data-ttu-id="4f751-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f751-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f751-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f751-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f751-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f751-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f751-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f751-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
