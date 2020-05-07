---
title: Método ICorDebugCode::CreateBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: 40582b1289875d5151ea96e3153c6e4760737e84
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893803"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="2b248-102">Método ICorDebugCode::CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2b248-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="2b248-103">Cria um ponto de interrupção neste segmento de código no deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="2b248-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b248-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b248-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b248-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b248-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="2b248-106">no O deslocamento no qual criar o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="2b248-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="2b248-107">fora Um ponteiro para o endereço de um objeto "ICorDebugFunctionBreakpoint" que representa o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="2b248-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b248-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b248-108">Remarks</span></span>  
 <span data-ttu-id="2b248-109">Antes que o ponto de interrupção esteja ativo, ele deve ser adicionado ao objeto de processo.</span><span class="sxs-lookup"><span data-stu-id="2b248-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="2b248-110">Se esse código for um código MSIL (Microsoft Intermediate Language) e houver uma versão nativa compilada JIT (just-in-time) do código, o ponto de interrupção será aplicado também no código compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="2b248-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="2b248-111">(O mesmo será verdadeiro se o código for compilado em JIT posteriormente.)</span><span class="sxs-lookup"><span data-stu-id="2b248-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b248-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b248-112">Requirements</span></span>  
 <span data-ttu-id="2b248-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b248-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b248-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b248-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b248-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b248-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b248-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b248-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
