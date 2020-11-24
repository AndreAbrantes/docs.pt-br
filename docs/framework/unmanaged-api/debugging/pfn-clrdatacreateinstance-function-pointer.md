---
title: Ponteiro de função PFN_CLRDataCreateInstance
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: 68a5b8bb1568f10699653479357b02b2e847cc02
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671958"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="0bcd2-102">Ponteiro de função PFN_CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="0bcd2-102">PFN_CLRDataCreateInstance Function Pointer</span></span>

<span data-ttu-id="0bcd2-103">Aponta para uma função que cria um objeto de interface para o item de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="0bcd2-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bcd2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bcd2-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bcd2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0bcd2-105">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="0bcd2-106">no O identificador da interface a ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="0bcd2-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="0bcd2-107">no Um ponteiro para um objeto [ICLRDataTarget](iclrdatatarget-interface.md) implementado pelo usuário que representa o item de destino para o qual criar o objeto de interface.</span><span class="sxs-lookup"><span data-stu-id="0bcd2-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="0bcd2-108">fora Um ponteiro para o endereço do objeto de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="0bcd2-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bcd2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0bcd2-109">Remarks</span></span>  

 <span data-ttu-id="0bcd2-110">O `ICLRDataTarget` objeto é implementado pelo gravador do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="0bcd2-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="0bcd2-111">A implementação depende do tipo de item de destino que está sendo representado.</span><span class="sxs-lookup"><span data-stu-id="0bcd2-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="0bcd2-112">O item de destino pode ser um processo, despejo de memória, computador remoto e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="0bcd2-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bcd2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0bcd2-113">Requirements</span></span>  

 <span data-ttu-id="0bcd2-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bcd2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bcd2-115">**Cabeçalho:** ClrData. idl</span><span class="sxs-lookup"><span data-stu-id="0bcd2-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="0bcd2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bcd2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bcd2-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bcd2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bcd2-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="0bcd2-118">See also</span></span>

- [<span data-ttu-id="0bcd2-119">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="0bcd2-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
