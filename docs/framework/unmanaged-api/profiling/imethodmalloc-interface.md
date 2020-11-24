---
title: Interface IMethodMalloc
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 8eccdba75b59df505ae72d74cfcd2bc83de2b45a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688166"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="794c8-102">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="794c8-102">IMethodMalloc Interface</span></span>

<span data-ttu-id="794c8-103">Fornece um método para alocar memória para um novo corpo de função da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="794c8-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="794c8-104">A `IMethodMalloc` interface é um alocador de memória simples.</span><span class="sxs-lookup"><span data-stu-id="794c8-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="794c8-105">Ele permite que você aloque memória, mas não a libere.</span><span class="sxs-lookup"><span data-stu-id="794c8-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="794c8-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="794c8-106">Methods</span></span>  
  
|<span data-ttu-id="794c8-107">Método</span><span class="sxs-lookup"><span data-stu-id="794c8-107">Method</span></span>|<span data-ttu-id="794c8-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="794c8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="794c8-109">Método Alloc</span><span class="sxs-lookup"><span data-stu-id="794c8-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="794c8-110">Tenta alocar uma quantidade especificada de memória para um novo corpo de função MSIL.</span><span class="sxs-lookup"><span data-stu-id="794c8-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="794c8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="794c8-111">Remarks</span></span>  

 <span data-ttu-id="794c8-112">Cada alocador é específico do módulo e garante que o corpo da função estará em um deslocamento positivo da base do módulo.</span><span class="sxs-lookup"><span data-stu-id="794c8-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="794c8-113">A memória acima da base de um módulo pode ser preciosa, portanto, o alocador deve ser usado para alocar memória apenas para um corpo de função.</span><span class="sxs-lookup"><span data-stu-id="794c8-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="794c8-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="794c8-114">Requirements</span></span>  

 <span data-ttu-id="794c8-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="794c8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="794c8-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="794c8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="794c8-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="794c8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="794c8-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="794c8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794c8-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="794c8-119">See also</span></span>

- [<span data-ttu-id="794c8-120">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="794c8-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
