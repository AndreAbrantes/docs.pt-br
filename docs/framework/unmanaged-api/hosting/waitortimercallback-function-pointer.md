---
title: Ponteiro de função WAITORTIMERCALLBACK
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: 74256f35804ff59f04952a1ac20ac7866e8f5683
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732808"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="fc4c2-102">Ponteiro de função WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="fc4c2-102">WAITORTIMERCALLBACK Function Pointer</span></span>

<span data-ttu-id="fc4c2-103">Aponta para uma função que notifica o host que um identificador de espera ( <xref:System.Threading.WaitHandle> ) foi sinalizado ou esgotou o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="fc4c2-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="fc4c2-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fc4c2-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc4c2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc4c2-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc4c2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc4c2-106">Parameters</span></span>  

 `lpParameter`  
 <span data-ttu-id="fc4c2-107">no Um ponteiro para um objeto que contém informações definidas pelo host.</span><span class="sxs-lookup"><span data-stu-id="fc4c2-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="fc4c2-108">[in] `true` Se o identificador de espera expirou ou `false` se foi sinalizado.</span><span class="sxs-lookup"><span data-stu-id="fc4c2-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc4c2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc4c2-109">Remarks</span></span>  

 <span data-ttu-id="fc4c2-110">A função para a qual os `WAITORTIMERCALLBACK` pontos é uma função de retorno de chamada e deve ser implementada pelo gravador do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="fc4c2-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc4c2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc4c2-111">Requirements</span></span>  

 <span data-ttu-id="fc4c2-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc4c2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc4c2-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc4c2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc4c2-114">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="fc4c2-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="fc4c2-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc4c2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4c2-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="fc4c2-116">See also</span></span>

- [<span data-ttu-id="fc4c2-117">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="fc4c2-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
