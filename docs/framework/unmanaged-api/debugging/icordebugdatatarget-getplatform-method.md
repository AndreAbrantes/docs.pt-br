---
title: Método ICorDebugDataTarget::GetPlatform
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: e8612b23cbfa506fddb2fad712848b285b9ac28e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679787"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="badfc-102">Método ICorDebugDataTarget::GetPlatform</span><span class="sxs-lookup"><span data-stu-id="badfc-102">ICorDebugDataTarget::GetPlatform Method</span></span>

<span data-ttu-id="badfc-103">Fornece informações sobre a plataforma, incluindo arquitetura do processador e sistema operacional, em que o processo de destino está em execução.</span><span class="sxs-lookup"><span data-stu-id="badfc-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="badfc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="badfc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="badfc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="badfc-105">Parameters</span></span>  

 `pTargetPlatform`  
 <span data-ttu-id="badfc-106">fora Um ponteiro para uma enumeração [CorDebugPlatformEnum](cordebugplatform-enumeration.md) que descreve a plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="badfc-106">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="badfc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="badfc-107">Remarks</span></span>  

 <span data-ttu-id="badfc-108">O `CorDebugPlatformEnum` valor de retorno de enumeração é usado pela interface [ICorDebug](icordebug-interface.md) para determinar os detalhes do processo de destino, como o tamanho do ponteiro, o layout do espaço de endereço, o conjunto de registros, o formato de instrução, o layout do contexto e as convenções de chamada.</span><span class="sxs-lookup"><span data-stu-id="badfc-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="badfc-109">O `pTargetPlatform` valor pode se referir a uma plataforma que está sendo emulada para o destino em vez de especificar o hardware real em uso.</span><span class="sxs-lookup"><span data-stu-id="badfc-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="badfc-110">Por exemplo, um processo em execução no ambiente do Windows no Windows (WOW) em uma edição de 64 bits do sistema operacional Windows deve usar o `CORDB_PLATFORM_WINDOWS_X86` valor da enumeração [CorDebugPlatformEnum](cordebugplatform-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="badfc-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="badfc-111">Esse método deve ter sucesso.</span><span class="sxs-lookup"><span data-stu-id="badfc-111">This method must succeed.</span></span> <span data-ttu-id="badfc-112">Se falhar, a plataforma de destino será inutilizável.</span><span class="sxs-lookup"><span data-stu-id="badfc-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="badfc-113">O método pode falhar pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="badfc-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="badfc-114">A plataforma que está sendo emulada para o destino é inutilizável.</span><span class="sxs-lookup"><span data-stu-id="badfc-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="badfc-115">O hardware real na plataforma de destino é inutilizável.</span><span class="sxs-lookup"><span data-stu-id="badfc-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="badfc-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="badfc-116">Requirements</span></span>  

 <span data-ttu-id="badfc-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="badfc-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="badfc-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="badfc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="badfc-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="badfc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="badfc-120">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="badfc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="badfc-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="badfc-121">See also</span></span>

- [<span data-ttu-id="badfc-122">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="badfc-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="badfc-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="badfc-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="badfc-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="badfc-124">Debugging</span></span>](index.md)
