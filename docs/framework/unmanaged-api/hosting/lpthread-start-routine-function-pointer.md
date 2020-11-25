---
title: Ponteiro de função LPTHREAD_START_ROUTINE
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
ms.openlocfilehash: c86b65e136869603f93253678108b2ffa9d388e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730052"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="8b469-102">Ponteiro de função LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="8b469-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>

<span data-ttu-id="8b469-103">Aponta para uma função que notifica o host que um thread começou a ser executado.</span><span class="sxs-lookup"><span data-stu-id="8b469-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="8b469-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8b469-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b469-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b469-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b469-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b469-106">Parameters</span></span>  

 `lpThreadParameter`  
 <span data-ttu-id="8b469-107">no Um ponteiro para o código que iniciou a execução.</span><span class="sxs-lookup"><span data-stu-id="8b469-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b469-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b469-108">Remarks</span></span>  

 <span data-ttu-id="8b469-109">A função para a qual os `LPTHREAD_START_ROUTINE` pontos é uma função de retorno de chamada e deve ser implementada pelo gravador do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="8b469-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b469-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b469-110">Requirements</span></span>  

 <span data-ttu-id="8b469-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b469-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b469-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b469-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b469-113">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="8b469-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="8b469-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b469-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b469-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b469-115">See also</span></span>

- [<span data-ttu-id="8b469-116">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="8b469-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
