---
title: Método ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: b5ca524d223fad7ded0d56def3293eb40be69fa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703714"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="0563d-102">Método ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="0563d-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>

<span data-ttu-id="0563d-103">Chamado por [ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) para relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="0563d-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0563d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0563d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0563d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0563d-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="0563d-106">no O endereço inicial da região de memória que deve ser enumerada.</span><span class="sxs-lookup"><span data-stu-id="0563d-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="0563d-107">no O tamanho, em bytes, da região de memória.</span><span class="sxs-lookup"><span data-stu-id="0563d-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0563d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0563d-108">Remarks</span></span>  

 <span data-ttu-id="0563d-109">O `ICLRDataEnumMemoryRegions::EnumMemoryRegions` método chamará esse método de retorno de chamada após cada tentativa de enumerar uma região de memória.</span><span class="sxs-lookup"><span data-stu-id="0563d-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="0563d-110">A enumeração continuará mesmo se esse método retornar um HRESULT indicando falha.</span><span class="sxs-lookup"><span data-stu-id="0563d-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="0563d-111">As regiões relatadas por esse retorno de chamada podem ser duplicatas ou sobrepostas regiões.</span><span class="sxs-lookup"><span data-stu-id="0563d-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0563d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0563d-112">Requirements</span></span>  

 <span data-ttu-id="0563d-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0563d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0563d-114">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0563d-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0563d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0563d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0563d-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0563d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0563d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="0563d-117">See also</span></span>

- [<span data-ttu-id="0563d-118">Interface ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="0563d-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
