---
title: Método ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: a0b77724a5a70461073d554a9794c5a904f6a363
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178574"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="7f7c6-102">Método ICorDebugProcess6::DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="7f7c6-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="7f7c6-103">Decodifica eventos de depuração gerenciados que foram encapsulados na carga de eventos de depuração de exceção nativo especialmente criado.</span><span class="sxs-lookup"><span data-stu-id="7f7c6-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f7c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f7c6-104">Syntax</span></span>  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,
        [in] DWORD dwThreadId,
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f7c6-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f7c6-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="7f7c6-106">[in] Um ponteiro para uma matriz de bytes de um evento de depuração de exceção nativo que inclui informações sobre um evento de depuração gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7f7c6-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="7f7c6-107">[in] O número de elementos nas matrizes de byte `pRecord`.</span><span class="sxs-lookup"><span data-stu-id="7f7c6-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="7f7c6-108">[em] Um membro de enumeração [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) que especifica o formato do evento de depuração não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="7f7c6-108">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7f7c6-109">[in] Um campo de bits que depende da arquitetura de destino e que especifica informações adicionais sobre o evento de depuração.</span><span class="sxs-lookup"><span data-stu-id="7f7c6-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="7f7c6-110">Para sistemas Windows, ele pode ser um membro da [enumeração CorDebugDecodeEventFlagsWindows.](cordebugdecodeeventflagswindows-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="7f7c6-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="7f7c6-111">[in] O identificador de sistema operacional do thread em que a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="7f7c6-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="7f7c6-112">[fora] Um ponteiro para o endereço de um objeto [ICorDebugDebugEvent](icordebugdebugevent-interface.md) que representa um evento de depuração gerenciada decodificado.</span><span class="sxs-lookup"><span data-stu-id="7f7c6-112">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f7c6-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f7c6-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f7c6-114">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7f7c6-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f7c6-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f7c6-115">Requirements</span></span>  
 <span data-ttu-id="7f7c6-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f7c6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f7c6-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f7c6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f7c6-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f7c6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f7c6-119">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f7c6-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7c6-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f7c6-120">See also</span></span>

- [<span data-ttu-id="7f7c6-121">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="7f7c6-121">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="7f7c6-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7f7c6-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
