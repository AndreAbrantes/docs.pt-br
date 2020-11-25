---
title: Enumeração ESymbolReadingPolicy
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 42ce1f02294db98c5c593a5f16de5226703d5f9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733705"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="9bba2-102">Enumeração ESymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="9bba2-102">ESymbolReadingPolicy Enumeration</span></span>

<span data-ttu-id="9bba2-103">Contém valores que definem a política para ler arquivos de banco de dados do programa (PDB).</span><span class="sxs-lookup"><span data-stu-id="9bba2-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bba2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bba2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="9bba2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9bba2-105">Members</span></span>  
  
|<span data-ttu-id="9bba2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9bba2-106">Member</span></span>|<span data-ttu-id="9bba2-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="9bba2-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="9bba2-108">Especifica que o depurador sempre deve ler arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="9bba2-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="9bba2-109">Especifica que o depurador deve ler somente arquivos PDB associados a assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="9bba2-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="9bba2-110">Especifica que o depurador nunca deve ler arquivos PDB.</span><span class="sxs-lookup"><span data-stu-id="9bba2-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bba2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bba2-111">Remarks</span></span>  

 <span data-ttu-id="9bba2-112">A `ESymbolReadingPolicy` enumeração é usada com o método [ICLRDebugManager:: SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9bba2-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bba2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bba2-113">Requirements</span></span>  

 <span data-ttu-id="9bba2-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bba2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bba2-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9bba2-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9bba2-116">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bba2-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bba2-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bba2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bba2-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="9bba2-118">See also</span></span>

- [<span data-ttu-id="9bba2-119">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="9bba2-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
