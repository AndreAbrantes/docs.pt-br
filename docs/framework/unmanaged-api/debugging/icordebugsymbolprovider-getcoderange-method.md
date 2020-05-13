---
title: 'Método ICorDebugSymbolProvider:: GetCodeRange'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: a9c1a4a625196d7430e365916cc7c2b67bf94127
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376088"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="69b02-102">Método ICorDebugSymbolProvider:: GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="69b02-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="69b02-103">Obtém o endereço inicial e o tamanho do método de acordo com um endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="69b02-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69b02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69b02-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69b02-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="69b02-106">no O endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="69b02-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="69b02-107">fora Um ponteiro para o endereço inicial do método.</span><span class="sxs-lookup"><span data-stu-id="69b02-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="69b02-108">Um ponteiro para o tamanho do código do método (o número de bytes do código do método).</span><span class="sxs-lookup"><span data-stu-id="69b02-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69b02-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="69b02-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69b02-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="69b02-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69b02-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69b02-111">Requirements</span></span>  
 <span data-ttu-id="69b02-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69b02-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69b02-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69b02-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69b02-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69b02-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69b02-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69b02-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b02-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="69b02-116">See also</span></span>

- [<span data-ttu-id="69b02-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="69b02-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="69b02-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="69b02-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
