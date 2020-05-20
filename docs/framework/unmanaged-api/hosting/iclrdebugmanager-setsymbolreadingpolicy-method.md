---
title: Método ICLRDebugManager::SetSymbolReadingPolicy
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
ms.openlocfilehash: f037e902a9f573023022c81503ea3b987cf6d424
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615729"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="7b139-102">Método ICLRDebugManager::SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="7b139-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="7b139-103">Define a política para ler arquivos de banco de dados do programa (PDB).</span><span class="sxs-lookup"><span data-stu-id="7b139-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="7b139-104">A política determina se as informações sobre números de linha e arquivos estão incluídas em pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="7b139-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b139-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b139-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b139-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b139-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="7b139-107">no Um membro da enumeração [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7b139-107">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b139-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7b139-108">Return Value</span></span>  
  
|<span data-ttu-id="7b139-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b139-109">HRESULT</span></span>|<span data-ttu-id="7b139-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b139-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b139-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b139-111">S_OK</span></span>|<span data-ttu-id="7b139-112">`SetSymbolReadingPolicy`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7b139-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="7b139-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b139-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b139-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7b139-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b139-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b139-115">E_FAIL</span></span>|<span data-ttu-id="7b139-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7b139-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b139-117">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="7b139-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b139-118">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b139-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b139-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b139-119">Requirements</span></span>  
 <span data-ttu-id="7b139-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b139-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b139-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7b139-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b139-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7b139-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b139-123">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b139-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b139-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b139-124">See also</span></span>

- [<span data-ttu-id="7b139-125">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="7b139-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
