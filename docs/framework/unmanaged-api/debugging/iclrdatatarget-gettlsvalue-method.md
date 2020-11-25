---
title: Método ICLRDataTarget::GetTLSValue
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: f6066774961b3fba2c466e156296907efc2e53df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703387"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="fe556-102">Método ICLRDataTarget::GetTLSValue</span><span class="sxs-lookup"><span data-stu-id="fe556-102">ICLRDataTarget::GetTLSValue Method</span></span>

<span data-ttu-id="fe556-103">Obtém um valor do armazenamento local do thread (TLS) do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="fe556-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="fe556-104">Esse método é chamado pelos serviços de acesso a dados do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fe556-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe556-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe556-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe556-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe556-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="fe556-107">no O identificador do sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="fe556-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="fe556-108">no O índice do local.</span><span class="sxs-lookup"><span data-stu-id="fe556-108">[in] The index of the location.</span></span> <span data-ttu-id="fe556-109">Esse valor deve ser um índice válido no repositório local do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="fe556-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="fe556-110">fora Um ponteiro para um `CLRDATA_ADDRESS` valor que especifica o valor retornado do local TLS fornecido.</span><span class="sxs-lookup"><span data-stu-id="fe556-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe556-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe556-111">Remarks</span></span>  

 <span data-ttu-id="fe556-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="fe556-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe556-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe556-113">Requirements</span></span>  

 <span data-ttu-id="fe556-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe556-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe556-115">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="fe556-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fe556-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe556-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe556-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe556-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe556-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe556-118">See also</span></span>

- [<span data-ttu-id="fe556-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="fe556-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
