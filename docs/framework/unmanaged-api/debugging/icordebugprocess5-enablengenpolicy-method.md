---
title: Método ICorDebugProcess5::EnableNGENPolicy
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: e3dfd3cae83c7891d246ff3a81427c161cc0e2d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731382"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="03298-102">Método ICorDebugProcess5::EnableNGENPolicy</span><span class="sxs-lookup"><span data-stu-id="03298-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>

<span data-ttu-id="03298-103">Define um valor que determina como um aplicativo carrega imagens nativas durante a execução em um depurador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="03298-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03298-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03298-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03298-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03298-105">Parameters</span></span>  

 `ePolicy`  
 <span data-ttu-id="03298-106">no Uma constante [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) que determina como um aplicativo carrega imagens nativas durante a execução em um depurador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="03298-106">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03298-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="03298-107">Remarks</span></span>  

 <span data-ttu-id="03298-108">Se a política for definida com êxito, o método retornará `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="03298-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="03298-109">Se `ePolicy` estiver fora do intervalo dos valores enumerados definidos por [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), o método retornará `E_INVALIDARG` e a chamada do método não terá nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="03298-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="03298-110">Se a política do gerador de imagem nativa (Ngen.exe) não puder ser atualizada, o método retornará `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="03298-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="03298-111">O `ICorDebugProcess5::EnableNGenPolicy` método pode ser chamado a qualquer momento durante o tempo de vida do processo.</span><span class="sxs-lookup"><span data-stu-id="03298-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="03298-112">A política está em vigor para todos os módulos que são carregados depois que a política é definida.</span><span class="sxs-lookup"><span data-stu-id="03298-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03298-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03298-113">Requirements</span></span>  

 <span data-ttu-id="03298-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03298-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03298-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03298-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03298-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03298-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03298-117">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03298-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03298-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="03298-118">See also</span></span>

- [<span data-ttu-id="03298-119">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="03298-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="03298-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="03298-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="03298-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="03298-121">Debugging</span></span>](index.md)
