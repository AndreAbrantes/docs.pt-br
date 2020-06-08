---
title: Método ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
ms.openlocfilehash: 21ebd0c64d6c8bbdac327258ad4c7ffec83a1ce9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504310"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="8159b-102">Método ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="8159b-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="8159b-103">Obtém um enumerador [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) para as identidades de assembly referenciadas pelo assembly com o tipo de identidade especificado.</span><span class="sxs-lookup"><span data-stu-id="8159b-103">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8159b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8159b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8159b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8159b-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="8159b-106">no Um valor válido que especifica a arquitetura do processador, conforme definido em WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="8159b-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8159b-107">no Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="8159b-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="8159b-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor para o qual a versão atual do Common Language Runtime (CLR) dá suporte.</span><span class="sxs-lookup"><span data-stu-id="8159b-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="8159b-109">no Uma identidade de associação de assembly opaca, normalmente retornada de uma chamada para o método [ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) ou [ICLRAssemblyIdentityManager:: GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8159b-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="8159b-110">fora Um ponteiro de interface para um `ICLRProbingAssemblyEnum` enumerador que contém referências aos assemblies referenciados pelo assembly identificado pelo `pwzReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="8159b-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8159b-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="8159b-111">Return Value</span></span>  
  
|<span data-ttu-id="8159b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8159b-112">HRESULT</span></span>|<span data-ttu-id="8159b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8159b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8159b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8159b-114">S_OK</span></span>|<span data-ttu-id="8159b-115">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8159b-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="8159b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8159b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8159b-117">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8159b-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8159b-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8159b-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8159b-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8159b-119">The call timed out.</span></span>|  
|<span data-ttu-id="8159b-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8159b-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8159b-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8159b-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8159b-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8159b-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8159b-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="8159b-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8159b-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8159b-124">E_FAIL</span></span>|<span data-ttu-id="8159b-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8159b-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8159b-126">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="8159b-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8159b-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8159b-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8159b-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8159b-128">Requirements</span></span>  
 <span data-ttu-id="8159b-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8159b-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8159b-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8159b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8159b-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8159b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8159b-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8159b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8159b-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="8159b-133">See also</span></span>

- [<span data-ttu-id="8159b-134">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="8159b-134">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8159b-135">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="8159b-135">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8159b-136">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="8159b-136">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
