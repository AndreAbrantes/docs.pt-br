---
title: Estrutura COR_SEGMENT
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: 738e29fa15340c76b055b608140f3c3bfbd29611
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726347"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="fc4e8-102">Estrutura COR_SEGMENT</span><span class="sxs-lookup"><span data-stu-id="fc4e8-102">COR_SEGMENT Structure</span></span>

<span data-ttu-id="fc4e8-103">Contém informações sobre uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc4e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc4e8-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="fc4e8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fc4e8-105">Members</span></span>  
  
|<span data-ttu-id="fc4e8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fc4e8-106">Member</span></span>|<span data-ttu-id="fc4e8-107">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="fc4e8-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="fc4e8-108">O endereço inicial da região de memória.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="fc4e8-109">O endereço final da região de memória.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="fc4e8-110">Um membro de enumeração [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) que indica a geração da região de memória.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="fc4e8-111">O número de heap no qual reside a região de memória.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="fc4e8-112">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc4e8-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc4e8-113">Remarks</span></span>  

 <span data-ttu-id="fc4e8-114">A estrutura `COR_SEGMENTS` representa uma região da memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="fc4e8-115">Objetos `COR_SEGMENTS` são membros do objeto da coleção [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md), que é preenchido chamando o método [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md).</span><span class="sxs-lookup"><span data-stu-id="fc4e8-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="fc4e8-116">O campo `heap` é o número de processadores, que corresponde ao heap que está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="fc4e8-117">Para os coletores de lixo de estação de trabalho, seu valor é sempre zero, uma vez que estações de trabalho têm apenas um heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="fc4e8-118">Para os coletores de lixo do servidor, seu valor corresponde ao processador ao qual o heap está anexado.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="fc4e8-119">Observe que pode haver mais ou menos heaps de coleta de lixo que o número real de processadores devido a detalhes de implementação do coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="fc4e8-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc4e8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc4e8-120">Requirements</span></span>  

 <span data-ttu-id="fc4e8-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc4e8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc4e8-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc4e8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc4e8-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc4e8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc4e8-124">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc4e8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4e8-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="fc4e8-125">See also</span></span>

- [<span data-ttu-id="fc4e8-126">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="fc4e8-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fc4e8-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="fc4e8-127">Debugging</span></span>](index.md)
