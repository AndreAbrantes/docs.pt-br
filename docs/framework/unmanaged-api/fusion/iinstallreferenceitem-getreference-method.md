---
title: Método IInstallReferenceItem::GetReference
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
ms.openlocfilehash: 14286970a4f7093d72b47b780ea880f5ccb1bca5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721065"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="eae0a-102">Método IInstallReferenceItem::GetReference</span><span class="sxs-lookup"><span data-stu-id="eae0a-102">IInstallReferenceItem::GetReference Method</span></span>

<span data-ttu-id="eae0a-103">Obtém um ponteiro para a estrutura de [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) representada por este objeto [IInstallReferenceItem](iinstallreferenceitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="eae0a-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eae0a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eae0a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eae0a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eae0a-105">Parameters</span></span>  

 `ppRefData`  
 <span data-ttu-id="eae0a-106">fora O `FUSION_INSTALL_REFERENCE` ponteiro retornado.</span><span class="sxs-lookup"><span data-stu-id="eae0a-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="eae0a-107">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="eae0a-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="eae0a-108">`dwFlags` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="eae0a-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="eae0a-109">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="eae0a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="eae0a-110">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="eae0a-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eae0a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eae0a-111">Requirements</span></span>  

 <span data-ttu-id="eae0a-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eae0a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eae0a-113">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="eae0a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eae0a-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eae0a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae0a-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="eae0a-115">See also</span></span>

- [<span data-ttu-id="eae0a-116">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="eae0a-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="eae0a-117">Estrutura FUSION_INSTALL_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="eae0a-117">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)
