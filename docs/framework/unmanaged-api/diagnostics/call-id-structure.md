---
title: Estrutura CALL_ID
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 3f41dd969e25f7a42308ff0b7b2d617344284b38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725242"
---
# <a name="call_id-structure"></a><span data-ttu-id="0acc1-102">Estrutura CALL_ID</span><span class="sxs-lookup"><span data-stu-id="0acc1-102">CALL_ID Structure</span></span>

<span data-ttu-id="0acc1-103">Fornece informações para um depurador sobre uma função que está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="0acc1-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="0acc1-104">Consulte a interface [INotifySink2](inotifysink2-interface.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0acc1-104">See the [INotifySink2](inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0acc1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0acc1-105">Syntax</span></span>  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="0acc1-106">Membros</span><span class="sxs-lookup"><span data-stu-id="0acc1-106">Members</span></span>  
  
|<span data-ttu-id="0acc1-107">Membro</span><span class="sxs-lookup"><span data-stu-id="0acc1-107">Member</span></span>|<span data-ttu-id="0acc1-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="0acc1-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="0acc1-109">Identifica o computador que está fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="0acc1-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="0acc1-110">Identifica o processador do computador.</span><span class="sxs-lookup"><span data-stu-id="0acc1-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="0acc1-111">Identifica o thread que está executando a chamada.</span><span class="sxs-lookup"><span data-stu-id="0acc1-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="0acc1-112">Especifica o endereço da pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="0acc1-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="0acc1-113">Especifica o endereço da chamada.</span><span class="sxs-lookup"><span data-stu-id="0acc1-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="0acc1-114">Identifica o computador que executará a chamada.</span><span class="sxs-lookup"><span data-stu-id="0acc1-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0acc1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0acc1-115">Requirements</span></span>  

 <span data-ttu-id="0acc1-116">**Cabeçalho:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="0acc1-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acc1-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="0acc1-117">See also</span></span>

- [<span data-ttu-id="0acc1-118">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="0acc1-118">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="0acc1-119">Estruturas de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="0acc1-119">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
