---
title: 'Método ICorDebugVariableSymbol:: SetValue'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: 38afd355938ec1beb1dbfd33de36116d25b07b4e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397070"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="76736-102">Método ICorDebugVariableSymbol:: SetValue</span><span class="sxs-lookup"><span data-stu-id="76736-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="76736-103">Atribui o valor de uma matriz de bytes a uma variável.</span><span class="sxs-lookup"><span data-stu-id="76736-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76736-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76736-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76736-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76736-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="76736-106">no O deslocamento inicial na variável na qual definir o valor.</span><span class="sxs-lookup"><span data-stu-id="76736-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="76736-107">Esse parâmetro é usado ao gravar em campos de membro em um objeto.</span><span class="sxs-lookup"><span data-stu-id="76736-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="76736-108">no O identificador de thread do thread cujo contexto deve ser atualizado para refletir o novo valor.</span><span class="sxs-lookup"><span data-stu-id="76736-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="76736-109">no O tamanho em bytes do contexto do thread.</span><span class="sxs-lookup"><span data-stu-id="76736-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="76736-110">no O contexto de thread usado para gravar o valor.</span><span class="sxs-lookup"><span data-stu-id="76736-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="76736-111">no O tamanho em bytes do `pValue` buffer.</span><span class="sxs-lookup"><span data-stu-id="76736-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="76736-112">no O buffer que contém o valor a ser definido.</span><span class="sxs-lookup"><span data-stu-id="76736-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76736-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="76736-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76736-114">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="76736-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76736-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76736-115">Requirements</span></span>  
 <span data-ttu-id="76736-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76736-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76736-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76736-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76736-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76736-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76736-119">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76736-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76736-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="76736-120">See also</span></span>

- [<span data-ttu-id="76736-121">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="76736-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="76736-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="76736-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
