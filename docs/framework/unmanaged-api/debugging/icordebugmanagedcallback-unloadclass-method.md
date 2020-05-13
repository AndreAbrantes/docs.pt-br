---
title: Método ICorDebugManagedCallback::UnloadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: a7b71170f58ddfe0295da28b8c9fc73286b074e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212263"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="98ada-102">Método ICorDebugManagedCallback::UnloadClass</span><span class="sxs-lookup"><span data-stu-id="98ada-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="98ada-103">Notifica o depurador de que uma classe está sendo descarregada.</span><span class="sxs-lookup"><span data-stu-id="98ada-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98ada-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98ada-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98ada-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98ada-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="98ada-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="98ada-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="98ada-107">no Um ponteiro para um objeto ICorDebugClass que representa a classe.</span><span class="sxs-lookup"><span data-stu-id="98ada-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98ada-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="98ada-108">Remarks</span></span>  
 <span data-ttu-id="98ada-109">A classe não deve ser referenciada após esta chamada.</span><span class="sxs-lookup"><span data-stu-id="98ada-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98ada-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98ada-110">Requirements</span></span>  
 <span data-ttu-id="98ada-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98ada-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98ada-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98ada-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98ada-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98ada-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98ada-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98ada-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ada-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="98ada-115">See also</span></span>

- [<span data-ttu-id="98ada-116">Método LoadClass</span><span class="sxs-lookup"><span data-stu-id="98ada-116">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="98ada-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="98ada-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
