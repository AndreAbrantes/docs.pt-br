---
title: Enumeração EHostBindingPolicyModifyFlags
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: 256c362ae0aea51fea16ce799db243b105dee81a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616236"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="0da79-102">Enumeração EHostBindingPolicyModifyFlags</span><span class="sxs-lookup"><span data-stu-id="0da79-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="0da79-103">Permite que o host especifique o tipo de redirecionamento que o Common Language Runtime (CLR) deve executar ao aplicar as modificações de política de um assembly de origem a um assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="0da79-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da79-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0da79-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="0da79-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0da79-105">Members</span></span>  
  
|<span data-ttu-id="0da79-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0da79-106">Member</span></span>|<span data-ttu-id="0da79-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0da79-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="0da79-108">Especifica que o CLR encadeará os valores de política do assembly de origem para aqueles do assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="0da79-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="0da79-109">Especifica que o CLR executará a ação padrão.</span><span class="sxs-lookup"><span data-stu-id="0da79-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="0da79-110">Especifica que o CLR definirá os valores de política do assembly de destino para os valores máximos.</span><span class="sxs-lookup"><span data-stu-id="0da79-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="0da79-111">Especifica que o CLR substituirá os valores de política do assembly de destino pelos do assembly de origem.</span><span class="sxs-lookup"><span data-stu-id="0da79-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0da79-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="0da79-112">Remarks</span></span>  
 <span data-ttu-id="0da79-113">O método [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) usa um parâmetro do tipo `EHostBindingPolicyModifyFlags` .</span><span class="sxs-lookup"><span data-stu-id="0da79-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0da79-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0da79-114">Requirements</span></span>  
 <span data-ttu-id="0da79-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0da79-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0da79-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0da79-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0da79-117">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0da79-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0da79-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0da79-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da79-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="0da79-119">See also</span></span>

- [<span data-ttu-id="0da79-120">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="0da79-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="0da79-121">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="0da79-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
