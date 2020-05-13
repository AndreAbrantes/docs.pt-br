---
title: Interface ICorDebugObjectEnum
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: 0594caf53a889d51ea78e2ee9d6fff4d30f7cff2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205286"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="caa94-102">Interface ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="caa94-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="caa94-103">Implementa métodos ICorDebugEnum e enumera matrizes de objetos por seus endereços virtuais relativos (RVAs).</span><span class="sxs-lookup"><span data-stu-id="caa94-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="caa94-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="caa94-104">Methods</span></span>  
  
|<span data-ttu-id="caa94-105">Método</span><span class="sxs-lookup"><span data-stu-id="caa94-105">Method</span></span>|<span data-ttu-id="caa94-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="caa94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="caa94-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="caa94-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="caa94-108">Obtém o RVAs do número especificado de objetos da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="caa94-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caa94-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="caa94-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="caa94-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="caa94-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caa94-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="caa94-111">Requirements</span></span>  
 <span data-ttu-id="caa94-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caa94-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa94-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="caa94-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="caa94-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="caa94-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caa94-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa94-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa94-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="caa94-116">See also</span></span>

- [<span data-ttu-id="caa94-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="caa94-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
