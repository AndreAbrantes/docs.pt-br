---
title: Interface ICorDebugModule3
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 543a1a3c79b6cf3eb799da5844f35286dfa91940
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709551"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="e9150-102">Interface ICorDebugModule3</span><span class="sxs-lookup"><span data-stu-id="e9150-102">ICorDebugModule3 Interface</span></span>

<span data-ttu-id="e9150-103">Cria um leitor de símbolos para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="e9150-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9150-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9150-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e9150-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e9150-105">Methods</span></span>  
  
|<span data-ttu-id="e9150-106">Método</span><span class="sxs-lookup"><span data-stu-id="e9150-106">Method</span></span>|<span data-ttu-id="e9150-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="e9150-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9150-108">Método ICorDebugModule3::CreateReaderForInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="e9150-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="e9150-109">Cria um leitor de símbolo (normalmente [interface ISymUnmanagedReader](../diagnostics/isymunmanagedreader-interface.md)) para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="e9150-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9150-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9150-110">Remarks</span></span>  

 <span data-ttu-id="e9150-111">Essa interface estende logicamente as interfaces "ICorDebugModule" e "ICorDebugModule2".</span><span class="sxs-lookup"><span data-stu-id="e9150-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9150-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="e9150-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9150-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9150-113">Requirements</span></span>  

 <span data-ttu-id="e9150-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9150-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9150-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9150-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9150-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9150-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9150-117">**Versões do .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e9150-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e9150-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="e9150-118">See also</span></span>

- [<span data-ttu-id="e9150-119">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="e9150-119">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="e9150-120">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="e9150-120">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="e9150-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e9150-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
