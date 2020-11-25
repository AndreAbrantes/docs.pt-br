---
title: Método ICorDebugProcess::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: 87b7b7381ef53f7e2abebc053b5c9f87f94d96c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695056"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="b4431-102">Método ICorDebugProcess::GetHandle</span><span class="sxs-lookup"><span data-stu-id="b4431-102">ICorDebugProcess::GetHandle Method</span></span>

<span data-ttu-id="b4431-103">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="b4431-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4431-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4431-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4431-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4431-105">Parameters</span></span>  

 `phProcessHandle`  
 <span data-ttu-id="b4431-106">fora Um ponteiro para um `HPROCESS` que é o identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="b4431-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4431-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4431-107">Remarks</span></span>  

 <span data-ttu-id="b4431-108">O identificador recuperado pertence à interface de depuração.</span><span class="sxs-lookup"><span data-stu-id="b4431-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="b4431-109">O depurador deve duplicar o identificador antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="b4431-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4431-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4431-110">Requirements</span></span>  

 <span data-ttu-id="b4431-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4431-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4431-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4431-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4431-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4431-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4431-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4431-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
