---
title: Interface ICLROnEventManager
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 1948075d87b5a44397a1eaab3adb4edbc96d7143
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725621"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="8c800-102">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="8c800-102">ICLROnEventManager Interface</span></span>

<span data-ttu-id="8c800-103">Fornece métodos que permitem ao host registrar e cancelar o registro de retornos de chamada para eventos de Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8c800-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c800-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8c800-104">Methods</span></span>  
  
|<span data-ttu-id="8c800-105">Método</span><span class="sxs-lookup"><span data-stu-id="8c800-105">Method</span></span>|<span data-ttu-id="8c800-106">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="8c800-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c800-107">Método RegisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="8c800-107">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="8c800-108">Registra um ponteiro de retorno de chamada para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="8c800-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="8c800-109">Método UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="8c800-109">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="8c800-110">Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="8c800-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c800-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c800-111">Remarks</span></span>  

 <span data-ttu-id="8c800-112">Para registrar e cancelar o registro de retornos de chamada de evento, o host obtém uma referência ao `ICLROnEventManager` chamando o método [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8c800-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c800-113">Os eventos descritos por [EClrEvent](eclrevent-enumeration.md) podem ser acionados mais de uma vez e de threads diferentes para sinalizar um descarregamento ou desabilitar o CLR.</span><span class="sxs-lookup"><span data-stu-id="8c800-113">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c800-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c800-114">Requirements</span></span>  

 <span data-ttu-id="8c800-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c800-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c800-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c800-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c800-117">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c800-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c800-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c800-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c800-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c800-119">See also</span></span>

- [<span data-ttu-id="8c800-120">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="8c800-120">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="8c800-121">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="8c800-121">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="8c800-122">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="8c800-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="8c800-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="8c800-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
