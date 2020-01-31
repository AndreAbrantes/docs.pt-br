---
title: Enumeração COR_PRF_SNAPSHOT_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867016"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="f5cc7-102">Enumeração COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="f5cc7-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="f5cc7-103">Especifica a quantidade de dados a serem passados com um instantâneo de pilha em cada chamada para a função [StackSnapshotCallback](stacksnapshotcallback-function.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5cc7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5cc7-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f5cc7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f5cc7-105">Members</span></span>  
  
|<span data-ttu-id="f5cc7-106">Membros</span><span class="sxs-lookup"><span data-stu-id="f5cc7-106">Members</span></span>|<span data-ttu-id="f5cc7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5cc7-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="f5cc7-108">Indica que os valores devem ser passados para todos os parâmetros de `StackSnapshotCallback`, exceto o parâmetro `context`.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="f5cc7-109">Indica que os valores devem ser passados para todos os parâmetros de `StackSnapshotCallback`, incluindo o parâmetro `context`.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="f5cc7-110">Indica que um algoritmo de movimentação de pilha mais simples e alternativo será usado.</span><span class="sxs-lookup"><span data-stu-id="f5cc7-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5cc7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5cc7-111">Remarks</span></span>  
 <span data-ttu-id="f5cc7-112">Os valores fornecidos pela enumeração de `COR_PRF_SNAPSHOT_INFO` são passados como parâmetros para o método [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f5cc7-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5cc7-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="f5cc7-113">Requirements</span></span>  
 <span data-ttu-id="f5cc7-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5cc7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5cc7-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f5cc7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5cc7-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5cc7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5cc7-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5cc7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cc7-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="f5cc7-118">See also</span></span>

- [<span data-ttu-id="f5cc7-119">Método DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="f5cc7-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="f5cc7-120">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="f5cc7-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
