---
title: Evento ETW Exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716062"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="e7c38-102">Evento ETW Exception Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="e7c38-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="e7c38-103">Esse evento captura informações sobre as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="e7c38-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="e7c38-104">A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento.</span><span class="sxs-lookup"><span data-stu-id="e7c38-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="e7c38-105">(Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="e7c38-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e7c38-106">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="e7c38-106">Keyword for raising the event</span></span>|<span data-ttu-id="e7c38-107">Nível</span><span class="sxs-lookup"><span data-stu-id="e7c38-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e7c38-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="e7c38-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="e7c38-109">Aviso (2)</span><span class="sxs-lookup"><span data-stu-id="e7c38-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="e7c38-110">A tabela a seguir mostra as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="e7c38-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="e7c38-111">Event</span><span class="sxs-lookup"><span data-stu-id="e7c38-111">Event</span></span>|<span data-ttu-id="e7c38-112">ID do evento</span><span class="sxs-lookup"><span data-stu-id="e7c38-112">Event ID</span></span>|<span data-ttu-id="e7c38-113">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="e7c38-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="e7c38-114">80</span><span class="sxs-lookup"><span data-stu-id="e7c38-114">80</span></span>|<span data-ttu-id="e7c38-115">Uma exceção gerenciada é gerada.</span><span class="sxs-lookup"><span data-stu-id="e7c38-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="e7c38-116">A tabela a seguir mostra dados do evento.</span><span class="sxs-lookup"><span data-stu-id="e7c38-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="e7c38-117">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="e7c38-117">Field name</span></span>|<span data-ttu-id="e7c38-118">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="e7c38-118">Data type</span></span>|<span data-ttu-id="e7c38-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7c38-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e7c38-120">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="e7c38-120">Exception Type</span></span>|<span data-ttu-id="e7c38-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e7c38-121">win:UnicodeString</span></span>|<span data-ttu-id="e7c38-122">Tipo da exceção; por exemplo, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="e7c38-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="e7c38-123">Mensagem de exceção</span><span class="sxs-lookup"><span data-stu-id="e7c38-123">Exception Message</span></span>|<span data-ttu-id="e7c38-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e7c38-124">win:UnicodeString</span></span>|<span data-ttu-id="e7c38-125">A mensagem de exceção real.</span><span class="sxs-lookup"><span data-stu-id="e7c38-125">Actual exception message.</span></span>|  
|<span data-ttu-id="e7c38-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="e7c38-126">EIPCodeThrow</span></span>|<span data-ttu-id="e7c38-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="e7c38-127">win:Pointer</span></span>|<span data-ttu-id="e7c38-128">Ponteiro de instrução em que ocorreu a exceção.</span><span class="sxs-lookup"><span data-stu-id="e7c38-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="e7c38-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="e7c38-129">ExceptionHR</span></span>|<span data-ttu-id="e7c38-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e7c38-130">win:UInt32</span></span>|<span data-ttu-id="e7c38-131">Exceção [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="e7c38-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="e7c38-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="e7c38-132">ExceptionFlags</span></span>|<span data-ttu-id="e7c38-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e7c38-133">win:UInt16</span></span>|<span data-ttu-id="e7c38-134">0x01: HasInnerException (consulte [Eventos CLR ETW](clr-etw-events.md) na documentação do Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e7c38-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="e7c38-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="e7c38-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="e7c38-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="e7c38-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="e7c38-137">0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [tratamento de exceções de estado corrompido](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="e7c38-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="e7c38-138">0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> está em conformidade com CLS; caso contrário, ela não está em conformidade com CLS).</span><span class="sxs-lookup"><span data-stu-id="e7c38-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="e7c38-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e7c38-139">ClrInstanceID</span></span>|<span data-ttu-id="e7c38-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e7c38-140">win:UInt16</span></span>|<span data-ttu-id="e7c38-141">ID exclusiva da instância do CLR ou do CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e7c38-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7c38-142">Veja também</span><span class="sxs-lookup"><span data-stu-id="e7c38-142">See also</span></span>

- [<span data-ttu-id="e7c38-143">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="e7c38-143">CLR ETW Events</span></span>](clr-etw-events.md)
