---
title: Função ForwardTranslateAccelerator - Referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186628"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="2be34-102">Função ForwardTranslateAccelerator (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="2be34-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="2be34-103">Esta API suporta a infra-estrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="2be34-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="2be34-104">Usado pela infra-estrutura do Windows Presentation Foundation (WPF) para gerenciamento de janelas.</span><span class="sxs-lookup"><span data-stu-id="2be34-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be34-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2be34-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="2be34-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2be34-106">Parameters</span></span>  
 <span data-ttu-id="2be34-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="2be34-107">pMsg</span></span>  
 <span data-ttu-id="2be34-108">Um ponteiro para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="2be34-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="2be34-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="2be34-109">appUnhandled</span></span>  
 <span data-ttu-id="2be34-110">`true`quando o aplicativo já teve a chance de lidar com a mensagem de entrada, mas não a lidou com ela; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="2be34-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2be34-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2be34-111">Requirements</span></span>  
 <span data-ttu-id="2be34-112">**Plataformas:** Consulte [os requisitos do sistema de estrutura .NET](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2be34-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2be34-113">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="2be34-113">**DLL:**</span></span>  
  
 <span data-ttu-id="2be34-114">No quadro .NET 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="2be34-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="2be34-115">No Quadro .NET 4 e posteriores: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="2be34-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="2be34-116">**.NET Framework Version:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2be34-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be34-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="2be34-117">See also</span></span>

- [<span data-ttu-id="2be34-118">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="2be34-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
