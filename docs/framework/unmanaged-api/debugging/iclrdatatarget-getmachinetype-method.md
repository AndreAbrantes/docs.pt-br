---
title: Método ICLRDataTarget::GetMachineType
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
ms.openlocfilehash: 00601e0bc722c0dc5e972324eddc0ab073d04586
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703532"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="6b284-102">Método ICLRDataTarget::GetMachineType</span><span class="sxs-lookup"><span data-stu-id="6b284-102">ICLRDataTarget::GetMachineType Method</span></span>

<span data-ttu-id="6b284-103">Obtém o identificador da espécie de conjunto de instruções que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="6b284-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b284-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b284-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b284-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b284-105">Parameters</span></span>  

 `machineType`  
 <span data-ttu-id="6b284-106">fora Um ponteiro para um valor que indica o conjunto de instruções que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="6b284-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="6b284-107">O retornado `machineType` é uma das constantes IMAGE_FILE_MACHINE, que são definidas no arquivo de cabeçalho WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="6b284-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b284-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b284-108">Requirements</span></span>  

 <span data-ttu-id="6b284-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b284-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b284-110">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="6b284-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6b284-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b284-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b284-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b284-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b284-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b284-113">See also</span></span>

- [<span data-ttu-id="6b284-114">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="6b284-114">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
