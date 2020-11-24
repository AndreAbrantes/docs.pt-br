---
title: Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
ms.openlocfilehash: 6b67ba9d022d94f51d7cc6a4645855f6b6ac3e19
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679306"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="b5de8-102">Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="b5de8-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>

<span data-ttu-id="b5de8-103">Obtém uma instância de [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) que contém uma lista de assemblies referenciados pelo assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="b5de8-103">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5de8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5de8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5de8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5de8-105">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="b5de8-106">no O caminho para o assembly a ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="b5de8-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b5de8-107">no Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="b5de8-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="b5de8-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor para o qual a versão atual do Common Language Runtime (CLR) dá suporte.</span><span class="sxs-lookup"><span data-stu-id="b5de8-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="b5de8-109">no Um ponteiro para um objeto [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) que representa assemblies que devem ser excluídos do `ppReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="b5de8-109">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="b5de8-110">fora Um ponteiro para o endereço de um `ICLRReferenceAssemblyEnum` objeto que contém dados de identidade de assembly para os assemblies referenciados pelo assembly em `pwzFilePath` , excluindo os assemblies representados por `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="b5de8-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5de8-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="b5de8-111">Return Value</span></span>  
  
|<span data-ttu-id="b5de8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5de8-112">HRESULT</span></span>|<span data-ttu-id="b5de8-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5de8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5de8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5de8-114">S_OK</span></span>|<span data-ttu-id="b5de8-115">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b5de8-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="b5de8-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5de8-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5de8-117">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b5de8-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b5de8-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5de8-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5de8-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b5de8-119">The call timed out.</span></span>|  
|<span data-ttu-id="b5de8-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5de8-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5de8-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b5de8-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5de8-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5de8-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5de8-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b5de8-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5de8-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5de8-124">E_FAIL</span></span>|<span data-ttu-id="b5de8-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b5de8-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5de8-126">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="b5de8-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5de8-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b5de8-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5de8-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5de8-128">Remarks</span></span>  

 <span data-ttu-id="b5de8-129">O chamador pode optar por excluir um conjunto de referências de assembly conhecidas da lista retornada.</span><span class="sxs-lookup"><span data-stu-id="b5de8-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="b5de8-130">Esse conjunto é definido pelo `pExcludeAssembliesList` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b5de8-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5de8-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5de8-131">Requirements</span></span>  

 <span data-ttu-id="b5de8-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5de8-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5de8-133">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b5de8-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5de8-134">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5de8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5de8-135">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5de8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5de8-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5de8-136">See also</span></span>

- [<span data-ttu-id="b5de8-137">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="b5de8-137">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b5de8-138">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="b5de8-138">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b5de8-139">Interface ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="b5de8-139">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
