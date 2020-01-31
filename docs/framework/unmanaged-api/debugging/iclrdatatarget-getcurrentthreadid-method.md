---
title: Método ICLRDataTarget::GetCurrentThreadID
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
ms.openlocfilehash: 35515d7c2b82ec2c42461406363964e0b60eb243
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785463"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="db067-102">Método ICLRDataTarget::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="db067-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="db067-103">Obtém o identificador do sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="db067-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db067-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db067-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db067-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db067-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="db067-106">fora Um ponteiro para o identificador do sistema operacional do thread atual para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="db067-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db067-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="db067-107">Remarks</span></span>  
 <span data-ttu-id="db067-108">Se não houver nenhum thread atual para o processo de destino, o método `GetCurrentThreadID` poderá falhar.</span><span class="sxs-lookup"><span data-stu-id="db067-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db067-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="db067-109">Requirements</span></span>  
 <span data-ttu-id="db067-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db067-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db067-111">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="db067-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="db067-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db067-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db067-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db067-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db067-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="db067-114">See also</span></span>

- [<span data-ttu-id="db067-115">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="db067-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
