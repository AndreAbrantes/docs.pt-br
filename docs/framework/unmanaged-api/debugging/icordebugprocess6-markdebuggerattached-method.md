---
title: Método ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: b2ecd6da11bffb156826fa0c31b5f32abb54ff4a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792215"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="e8d36-102">Método ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="e8d36-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="e8d36-103">Altera o estado interno do depurado para que o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> na biblioteca de classes .NET Framework retorne `true`.</span><span class="sxs-lookup"><span data-stu-id="e8d36-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d36-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8d36-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8d36-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8d36-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="e8d36-106">`true` se o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> deve indicar que um depurador é anexado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e8d36-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8d36-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e8d36-107">Return Value</span></span>  
 <span data-ttu-id="e8d36-108">O método pode retornar os valores listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e8d36-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="e8d36-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e8d36-109">Return value</span></span>|<span data-ttu-id="e8d36-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8d36-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="e8d36-111">A depuração foi atualizada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e8d36-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="e8d36-112">O assembly que contém o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> não é carregado, ou outros erros como metadados ausentes estão impedindo que ele seja reconhecido.</span><span class="sxs-lookup"><span data-stu-id="e8d36-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="e8d36-113">Esse erro é comum e benigno.</span><span class="sxs-lookup"><span data-stu-id="e8d36-113">This error is common and benign.</span></span> <span data-ttu-id="e8d36-114">Você deve chamar o método novamente ao carregar assemblies adicionais.</span><span class="sxs-lookup"><span data-stu-id="e8d36-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="e8d36-115">Outros valores `HRESULT` com falha.</span><span class="sxs-lookup"><span data-stu-id="e8d36-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="e8d36-116">Outros valores provavelmente indicam depurador ou componentes do compilador com comportamento inadequado.</span><span class="sxs-lookup"><span data-stu-id="e8d36-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8d36-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8d36-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8d36-118">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e8d36-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8d36-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e8d36-119">Requirements</span></span>  
 <span data-ttu-id="e8d36-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8d36-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8d36-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8d36-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8d36-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8d36-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8d36-123">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8d36-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d36-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="e8d36-124">See also</span></span>

- [<span data-ttu-id="e8d36-125">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="e8d36-125">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="e8d36-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e8d36-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
