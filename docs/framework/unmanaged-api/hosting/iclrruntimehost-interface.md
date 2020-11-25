---
title: Interface ICLRRuntimeHost
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
ms.openlocfilehash: 8d88222215eb31e1c63f3b26079517c4b088e81b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728830"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="30765-102">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="30765-102">ICLRRuntimeHost Interface</span></span>

<span data-ttu-id="30765-103">Fornece uma funcionalidade semelhante à da interface [ICorRuntimeHost](icorruntimehost-interface.md) fornecida no .NET Framework versão 1, com as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="30765-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="30765-104">A adição do método [SetHostControl](iclrruntimehost-sethostcontrol-method.md) para definir a interface de controle de host.</span><span class="sxs-lookup"><span data-stu-id="30765-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="30765-105">A omissão de alguns métodos fornecidos pelo `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="30765-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30765-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="30765-106">Methods</span></span>  
  
|<span data-ttu-id="30765-107">Método</span><span class="sxs-lookup"><span data-stu-id="30765-107">Method</span></span>|<span data-ttu-id="30765-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="30765-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30765-109">Método ExecuteApplication</span><span class="sxs-lookup"><span data-stu-id="30765-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="30765-110">Usado em cenários de implantação ClickOnce baseados em manifesto para especificar o aplicativo a ser ativado em um novo domínio.</span><span class="sxs-lookup"><span data-stu-id="30765-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="30765-111">Método ExecuteInAppDomain</span><span class="sxs-lookup"><span data-stu-id="30765-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="30765-112">Especifica o <xref:System.AppDomain> no qual executar o código gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="30765-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="30765-113">Método ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="30765-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="30765-114">Invoca o método especificado do tipo especificado no assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="30765-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="30765-115">Método GetCLRControl</span><span class="sxs-lookup"><span data-stu-id="30765-115">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="30765-116">Obtém um ponteiro de interface do tipo [ICLRControl](iclrcontrol-interface.md) que os hosts podem usar para personalizar aspectos do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="30765-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="30765-117">Método GetCurrentAppDomainId</span><span class="sxs-lookup"><span data-stu-id="30765-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="30765-118">Obtém o identificador numérico do <xref:System.AppDomain> que está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="30765-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="30765-119">Método SetHostControl</span><span class="sxs-lookup"><span data-stu-id="30765-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="30765-120">Define a interface de controle de host.</span><span class="sxs-lookup"><span data-stu-id="30765-120">Sets the host control interface.</span></span> <span data-ttu-id="30765-121">Você deve chamar `SetHostControl` antes de chamar `Start` .</span><span class="sxs-lookup"><span data-stu-id="30765-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="30765-122">Método de início</span><span class="sxs-lookup"><span data-stu-id="30765-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="30765-123">Inicializa o CLR em um processo.</span><span class="sxs-lookup"><span data-stu-id="30765-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="30765-124">Método Stop</span><span class="sxs-lookup"><span data-stu-id="30765-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="30765-125">Interrompe a execução do código pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="30765-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="30765-126">Método UnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="30765-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="30765-127">Descarrega o <xref:System.AppDomain> que corresponde ao identificador numérico especificado.</span><span class="sxs-lookup"><span data-stu-id="30765-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30765-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="30765-128">Remarks</span></span>  

 <span data-ttu-id="30765-129">Começando com o .NET Framework 4, use a interface [ICLRMetaHost](iclrmetahost-interface.md) para obter um ponteiro para a interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) e, em seguida, chame o método [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) para obter um ponteiro `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="30765-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="30765-130">Em versões anteriores do .NET Framework, o host obtém um ponteiro para uma `ICLRRuntimeHost` instância chamando [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="30765-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="30765-131">Para fornecer implementações de qualquer uma das tecnologias fornecidas no .NET Framework versão 2,0, você deve usar `ICLRRuntimeHost` em vez de `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="30765-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="30765-132">Não chame o método [Start](iclrruntimehost-start-method.md) antes de chamar o método [ExecuteApplication](iclrruntimehost-executeapplication-method.md) para ativar um aplicativo baseado em manifesto.</span><span class="sxs-lookup"><span data-stu-id="30765-132">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="30765-133">Se o `Start` método for chamado primeiro, a `ExecuteApplication` chamada do método falhará.</span><span class="sxs-lookup"><span data-stu-id="30765-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30765-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30765-134">Requirements</span></span>  

 <span data-ttu-id="30765-135">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30765-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30765-136">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30765-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30765-137">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30765-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30765-138">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30765-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30765-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="30765-139">See also</span></span>

- [<span data-ttu-id="30765-140">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="30765-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="30765-141">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="30765-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="30765-142">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="30765-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="30765-143">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="30765-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="30765-144">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="30765-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="30765-145">Coclass CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="30765-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
