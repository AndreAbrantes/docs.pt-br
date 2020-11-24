---
title: 'Método ICorDebugVirtualUnwinder:: GetContext'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: a5a1afa47e52eff7c930698a3354a03d8c62259f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679449"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="2cb3a-102">Método ICorDebugVirtualUnwinder:: GetContext</span><span class="sxs-lookup"><span data-stu-id="2cb3a-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>

<span data-ttu-id="2cb3a-103">Obtém o contexto atual deste desenrolador.</span><span class="sxs-lookup"><span data-stu-id="2cb3a-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cb3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cb3a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2cb3a-105">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="2cb3a-106">no Sinalizadores que especificam quais partes do contexto retornar (definido em WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="2cb3a-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="2cb3a-107">no O número de bytes em `contextBuf` .</span><span class="sxs-lookup"><span data-stu-id="2cb3a-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2cb3a-108">fora Um ponteiro para o número de bytes realmente gravados no `contextBuf` .</span><span class="sxs-lookup"><span data-stu-id="2cb3a-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="2cb3a-109">fora Uma matriz de bytes que contém o contexto atual deste desenrolador.</span><span class="sxs-lookup"><span data-stu-id="2cb3a-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cb3a-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="2cb3a-110">Return Value</span></span>  

 <span data-ttu-id="2cb3a-111">Qualquer valor HRESULT com falha recebido por MSCorDbi é considerado fatal e fará com que as APIs do ICorDebug sejam retornadas `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="2cb3a-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb3a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="2cb3a-112">Remarks</span></span>  

 <span data-ttu-id="2cb3a-113">Você define o valor inicial do `contextBuf` argumento para o buffer de contexto retornado chamando o método [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2cb3a-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cb3a-114">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2cb3a-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="2cb3a-115">Como o desenrolamento só pode restaurar um subconjunto dos registros, como somente os registros não voláteis, o contexto pode não corresponder exatamente ao estado de registro no momento da chamada de método real.</span><span class="sxs-lookup"><span data-stu-id="2cb3a-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb3a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cb3a-116">Requirements</span></span>  

 <span data-ttu-id="2cb3a-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cb3a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cb3a-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cb3a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cb3a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cb3a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cb3a-120">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cb3a-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb3a-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="2cb3a-121">See also</span></span>

- [<span data-ttu-id="2cb3a-122">Interface ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="2cb3a-122">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="2cb3a-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2cb3a-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
