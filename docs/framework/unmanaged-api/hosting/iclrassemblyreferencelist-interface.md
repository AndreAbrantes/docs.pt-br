---
title: Interface ICLRAssemblyReferenceList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: a75235cd0ac0e55412f0ba58881796e3ebc801f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679176"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="711f7-102">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="711f7-102">ICLRAssemblyReferenceList Interface</span></span>

<span data-ttu-id="711f7-103">Gerencia uma lista de assemblies que são carregados pelo Common Language Runtime (CLR) e não pelo host.</span><span class="sxs-lookup"><span data-stu-id="711f7-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="711f7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="711f7-104">Methods</span></span>  
  
|<span data-ttu-id="711f7-105">Método</span><span class="sxs-lookup"><span data-stu-id="711f7-105">Method</span></span>|<span data-ttu-id="711f7-106">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="711f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="711f7-107">Método IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="711f7-107">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="711f7-108">Obtém um valor que indica se o ponteiro fornecido faz referência a um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="711f7-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="711f7-109">Método IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="711f7-109">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="711f7-110">Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.</span><span class="sxs-lookup"><span data-stu-id="711f7-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="711f7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="711f7-111">Remarks</span></span>  

 <span data-ttu-id="711f7-112">Chame o método [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) para obter um ponteiro para uma instância do `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="711f7-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="711f7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="711f7-113">Requirements</span></span>  

 <span data-ttu-id="711f7-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="711f7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="711f7-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="711f7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="711f7-116">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="711f7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="711f7-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="711f7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="711f7-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="711f7-118">See also</span></span>

- [<span data-ttu-id="711f7-119">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="711f7-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="711f7-120">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="711f7-120">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="711f7-121">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="711f7-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
