---
title: Método ICLRDataTarget::WriteVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: 6a7a7736837f7e6bbf1ad4982e78a75550abbeab
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860509"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="cfe0e-102">Método ICLRDataTarget::WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="cfe0e-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="cfe0e-103">Grava dados do buffer especificado para o endereço de memória virtual especificado.</span><span class="sxs-lookup"><span data-stu-id="cfe0e-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfe0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfe0e-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfe0e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfe0e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="cfe0e-106">no Um CLRDATA_ADDRESS que armazena o endereço de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="cfe0e-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="cfe0e-107">no Um ponteiro para um buffer que armazena os dados a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="cfe0e-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="cfe0e-108">no O número de bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="cfe0e-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="cfe0e-109">fora Um ponteiro para o número real de bytes que foram gravados.</span><span class="sxs-lookup"><span data-stu-id="cfe0e-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfe0e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfe0e-110">Requirements</span></span>  
 <span data-ttu-id="cfe0e-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfe0e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfe0e-112">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="cfe0e-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cfe0e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfe0e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfe0e-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfe0e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfe0e-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfe0e-115">See also</span></span>

- [<span data-ttu-id="cfe0e-116">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="cfe0e-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
