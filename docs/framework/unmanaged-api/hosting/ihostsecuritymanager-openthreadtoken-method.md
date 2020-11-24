---
title: Método IHostSecurityManager::OpenThreadToken
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 30ec8cc8bbbd6d49f89cd67371c3326c0cb0df9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680606"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="5008a-102">Método IHostSecurityManager::OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="5008a-102">IHostSecurityManager::OpenThreadToken Method</span></span>

<span data-ttu-id="5008a-103">Abre o token de acesso discricionário associado ao thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="5008a-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5008a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5008a-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5008a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5008a-105">Parameters</span></span>  

 `dwDesiredAccess`  
 <span data-ttu-id="5008a-106">no Uma máscara de valores de acesso que especificam os tipos de acesso solicitados ao token de thread.</span><span class="sxs-lookup"><span data-stu-id="5008a-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="5008a-107">Esses valores são definidos na função do Win32 `OpenThreadToken` .</span><span class="sxs-lookup"><span data-stu-id="5008a-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="5008a-108">Os tipos de acesso solicitados são reconciliados com a DACL (lista de controle de acesso discricionário) do token para determinar quais tipos de acesso conceder ou negar.</span><span class="sxs-lookup"><span data-stu-id="5008a-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="5008a-109">[in] `true` para especificar que a verificação de acesso deve ser feita usando o contexto de segurança do processo para o thread de chamada; `false` para especificar que a verificação de acesso deve ser executada usando o contexto de segurança para o próprio thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="5008a-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="5008a-110">Se o thread estiver representando um cliente, o contexto de segurança poderá ser o de um processo de cliente.</span><span class="sxs-lookup"><span data-stu-id="5008a-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="5008a-111">fora Um ponteiro para o token de acesso aberto recentemente.</span><span class="sxs-lookup"><span data-stu-id="5008a-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5008a-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="5008a-112">Return Value</span></span>  
  
|<span data-ttu-id="5008a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5008a-113">HRESULT</span></span>|<span data-ttu-id="5008a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5008a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5008a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5008a-115">S_OK</span></span>|<span data-ttu-id="5008a-116">`OpenThreadToken` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5008a-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="5008a-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5008a-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5008a-118">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5008a-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5008a-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5008a-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5008a-120">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5008a-120">The call timed out.</span></span>|  
|<span data-ttu-id="5008a-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5008a-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5008a-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5008a-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5008a-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5008a-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5008a-124">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="5008a-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5008a-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5008a-125">E_FAIL</span></span>|<span data-ttu-id="5008a-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5008a-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5008a-127">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="5008a-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5008a-128">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5008a-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5008a-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="5008a-129">Remarks</span></span>  

 <span data-ttu-id="5008a-130">`IHostSecurityManager::OpenThreadToken` comporta-se da mesma forma que a função Win32 correspondente do mesmo nome, exceto que a função do Win32 permite que o chamador transmita um identificador para um thread arbitrário, enquanto `IHostSecurityManager::OpenThreadToken` abre somente o token associado ao thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="5008a-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="5008a-131">O `HANDLE` tipo não é compatível COM com, ou seja, seu tamanho é específico para o sistema operacional e requer marshaling personalizado.</span><span class="sxs-lookup"><span data-stu-id="5008a-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="5008a-132">Portanto, esse token é para uso apenas dentro do processo, entre o CLR e o host.</span><span class="sxs-lookup"><span data-stu-id="5008a-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5008a-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5008a-133">Requirements</span></span>  

 <span data-ttu-id="5008a-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5008a-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5008a-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5008a-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5008a-136">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5008a-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5008a-137">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5008a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5008a-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="5008a-138">See also</span></span>

- [<span data-ttu-id="5008a-139">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="5008a-139">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="5008a-140">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="5008a-140">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
