---
title: Interface ICorDebugModule3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3
helpviewer_keywords: ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6ef8314329aba60d8c23c6f00725192d83961ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="002f3-102">Interface ICorDebugModule3</span><span class="sxs-lookup"><span data-stu-id="002f3-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="002f3-103">Cria um leitor de símbolos para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="002f3-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="002f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="002f3-104">Syntax</span></span>  
  
```  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="002f3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="002f3-105">Methods</span></span>  
  
|<span data-ttu-id="002f3-106">Método</span><span class="sxs-lookup"><span data-stu-id="002f3-106">Method</span></span>|<span data-ttu-id="002f3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="002f3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="002f3-108">Método Icordebugmodule3::</span><span class="sxs-lookup"><span data-stu-id="002f3-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="002f3-109">Cria um leitor de símbolo (normalmente [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) para um módulo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="002f3-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="002f3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="002f3-110">Remarks</span></span>  
 <span data-ttu-id="002f3-111">Essa interface logicamente estende as interfaces "ICorDebugModule" e "ICorDebugModule2".</span><span class="sxs-lookup"><span data-stu-id="002f3-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="002f3-112">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="002f3-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="002f3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="002f3-113">Requirements</span></span>  
 <span data-ttu-id="002f3-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="002f3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="002f3-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="002f3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="002f3-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="002f3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="002f3-117">**Versões do .NET framework:**4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="002f3-117">**.NET Framework Versions:**4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002f3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="002f3-118">See Also</span></span>  
 [<span data-ttu-id="002f3-119">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="002f3-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="002f3-120">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="002f3-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="002f3-121">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="002f3-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
