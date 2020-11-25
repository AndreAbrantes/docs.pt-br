---
title: 'Método ICorDebugExceptionDebugEvent:: GetNativeIP'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: f3b29b3ceda521afe9543588af332531aa03e84e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697409"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="16918-102">Método ICorDebugExceptionDebugEvent:: GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="16918-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>

<span data-ttu-id="16918-103">Obtém o ponteiro de instrução nativa para este evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="16918-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16918-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16918-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16918-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16918-105">Parameters</span></span>  

 `pIP`  
 <span data-ttu-id="16918-106">fora Um ponteiro para o ponteiro de instrução deste evento de depuração de exceção.</span><span class="sxs-lookup"><span data-stu-id="16918-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="16918-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="16918-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16918-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="16918-108">Remarks</span></span>  

 <span data-ttu-id="16918-109">O significado desse ponteiro de instrução depende do tipo de evento, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="16918-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="16918-110">Tipo de evento</span><span class="sxs-lookup"><span data-stu-id="16918-110">Event type</span></span>|<span data-ttu-id="16918-111">Significado do `pStackPointer` valor</span><span class="sxs-lookup"><span data-stu-id="16918-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="16918-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="16918-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="16918-113">O endereço da instrução com falha.</span><span class="sxs-lookup"><span data-stu-id="16918-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="16918-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="16918-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="16918-115">O endereço do código no quadro indicado pelo método [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) em que a execução será retomada se nenhuma exceção tivesse sido gerada.</span><span class="sxs-lookup"><span data-stu-id="16918-115">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="16918-116">A exceção pode ou não causar código diferente, como o bloco catch de uma `try/catch/finally` cláusula, a ser executado nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="16918-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="16918-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="16918-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="16918-118">O endereço de código onde a `catch` execução do manipulador será iniciada no quadro indicado pelo método [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="16918-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="16918-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="16918-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="16918-120">`pIP` é 0.</span><span class="sxs-lookup"><span data-stu-id="16918-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="16918-121">O tipo de evento está disponível no método [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="16918-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16918-122">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16918-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16918-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16918-123">Requirements</span></span>  

 <span data-ttu-id="16918-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16918-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16918-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16918-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16918-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16918-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16918-127">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16918-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16918-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="16918-128">See also</span></span>

- [<span data-ttu-id="16918-129">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="16918-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="16918-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="16918-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
