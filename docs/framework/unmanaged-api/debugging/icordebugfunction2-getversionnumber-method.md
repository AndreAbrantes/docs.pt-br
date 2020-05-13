---
title: Método ICorDebugFunction2::GetVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: f47263872b1baf1038a5fa9816c96e3e2569e705
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213212"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="6a2bd-102">Método ICorDebugFunction2::GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="6a2bd-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="6a2bd-103">Obtém a versão editar e continuar desta função.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a2bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a2bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a2bd-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="6a2bd-106">fora Um ponteiro para um inteiro que é o número de versão da função que é representada por esse objeto ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a2bd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a2bd-107">Remarks</span></span>  
 <span data-ttu-id="6a2bd-108">O tempo de execução controla o número de edições que foram feitas em cada módulo durante uma sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="6a2bd-109">O número de versão de uma função é mais um que o número da edição que introduziu a função.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="6a2bd-110">A versão original da função é a versão 1.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-110">The function's original version is version 1.</span></span> <span data-ttu-id="6a2bd-111">O número é incrementado para um módulo toda vez que [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md) é chamado nesse módulo.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="6a2bd-112">Portanto, se o corpo de uma função foi substituído na primeira e terceira chamada para `ICorDebugModule2::ApplyChanges` , o `GetVersionNumber` pode retornar a versão 1, 2 ou 4 para essa função, mas não a versão 3.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="6a2bd-113">(Essa função não teria nenhuma versão 3.)</span><span class="sxs-lookup"><span data-stu-id="6a2bd-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="6a2bd-114">O número de versão é acompanhado separadamente para cada módulo.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="6a2bd-115">Portanto, se você executar quatro edições no módulo 1 e nenhum no módulo 2, a próxima edição no módulo 1 atribuirá um número de versão de 6 a todas as funções editadas no módulo 1.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="6a2bd-116">Se os mesmos toques de edição do módulo 2, as funções no módulo 2 receberão um número de versão 2.</span><span class="sxs-lookup"><span data-stu-id="6a2bd-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="6a2bd-117">O número de versão obtido pelo `GetVersionNumber` método pode ser menor que o obtido por [ICorDebugFunction:: GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a2bd-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="6a2bd-118">O método [ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) executa a mesma operação que `ICorDebugFunction2::GetVersionNumber` .</span><span class="sxs-lookup"><span data-stu-id="6a2bd-118">The [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a2bd-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a2bd-119">Requirements</span></span>  
 <span data-ttu-id="6a2bd-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a2bd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a2bd-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a2bd-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a2bd-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a2bd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a2bd-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a2bd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
