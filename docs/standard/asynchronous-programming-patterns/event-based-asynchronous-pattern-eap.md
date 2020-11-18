---
title: Padrão assíncrono baseado em evento (EAP)
description: Consulte links para artigos sobre o padrão assíncrono baseado em evento (EAP) no .NET, como implementação, práticas recomendadas, implementação de um cliente EAP e muito mais.
ms.date: 07/23/2018
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: c15bb6c9ec6ea737e6f240376e12bf8de3aa61bc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830396"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="37214-103">Padrão assíncrono baseado em evento (EAP)</span><span class="sxs-lookup"><span data-stu-id="37214-103">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="37214-104">Há várias maneiras de expor recursos assíncronos para o código cliente.</span><span class="sxs-lookup"><span data-stu-id="37214-104">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="37214-105">O Padrão Assíncrono baseado em evento prescreve uma maneira de as classes apresentarem comportamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="37214-105">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37214-106">A partir do .NET Framework 4, a biblioteca de tarefas paralelas fornece um novo modelo para programação assíncrona e paralela.</span><span class="sxs-lookup"><span data-stu-id="37214-106">Starting with .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="37214-107">Para obter mais informações, veja [Biblioteca de tarefas paralelas (TPL)](../parallel-programming/task-parallel-library-tpl.md) e [Padrão assíncrono baseado em tarefa (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="37214-107">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="37214-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="37214-108">In This Section</span></span>

 [<span data-ttu-id="37214-109">Visão geral do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="37214-109">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="37214-110">Descreve como o Padrão Assíncrono Baseado em Evento disponibiliza as vantagens de aplicativos de vários threads enquanto oculta muitos problemas complexos inerentes ao design com vários threads.</span><span class="sxs-lookup"><span data-stu-id="37214-110">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="37214-111">Implementando o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="37214-111">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="37214-112">Descreve a maneira padronizada de empacotar uma classe com recursos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="37214-112">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="37214-113">Práticas recomendadas para a implementação do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="37214-113">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="37214-114">Descreve as exigências para expor recursos assíncronos de acordo com o Padrão Assíncrono Baseado em Evento.</span><span class="sxs-lookup"><span data-stu-id="37214-114">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="37214-115">Decidindo quando implementar o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="37214-115">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="37214-116">Descreve como determinar quando você deve optar por implementar o Padrão assíncrono baseado em evento, em vez do padrão <xref:System.IAsyncResult> representado pelo [APM (Modelo de programação assíncrona)](asynchronous-programming-model-apm.md)</span><span class="sxs-lookup"><span data-stu-id="37214-116">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="37214-117">Como: Implementar um componente compatível com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="37214-117">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="37214-118">Descreve como criar um componente que implemente o Padrão assíncrono baseado em evento.</span><span class="sxs-lookup"><span data-stu-id="37214-118">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="37214-119">É implementado usando classes do auxiliar do namespace <xref:System.ComponentModel?displayProperty=nameWithType>, o que garante que o componente funcione corretamente em qualquer modelo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37214-119">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="37214-120">Como: Implementar um cliente do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="37214-120">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="37214-121">Descreve como criar um cliente que usa um componente que implemente o Padrão assíncrono baseado em evento.</span><span class="sxs-lookup"><span data-stu-id="37214-121">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="37214-122">Como: Usar componentes compatíveis com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="37214-122">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="37214-123">Descreve como usar um componente com suporte ao Padrão Assíncrono Baseado em Evento.</span><span class="sxs-lookup"><span data-stu-id="37214-123">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="37214-124">Referência</span><span class="sxs-lookup"><span data-stu-id="37214-124">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="37214-125">Descreve a classe <xref:System.ComponentModel.AsyncOperation> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="37214-125">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="37214-126">Descreve a classe <xref:System.ComponentModel.AsyncOperationManager> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="37214-126">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="37214-127">Descreve o componente <xref:System.ComponentModel.BackgroundWorker> e tem links a todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="37214-127">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="37214-128">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="37214-128">Related Sections</span></span>

 [<span data-ttu-id="37214-129">Biblioteca de tarefas paralelas (TPL)</span><span class="sxs-lookup"><span data-stu-id="37214-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="37214-130">Descreve um modelo de programação para operações paralelas e assíncronas.</span><span class="sxs-lookup"><span data-stu-id="37214-130">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="37214-131">Threading</span><span class="sxs-lookup"><span data-stu-id="37214-131">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="37214-132">Descreve recursos de multithreading no .NET.</span><span class="sxs-lookup"><span data-stu-id="37214-132">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37214-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="37214-133">See also</span></span>

- [<span data-ttu-id="37214-134">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="37214-134">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="37214-135">Eventos</span><span class="sxs-lookup"><span data-stu-id="37214-135">Events</span></span>](../events/index.md)
- [<span data-ttu-id="37214-136">Padrões de design de programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="37214-136">Asynchronous Programming Design Patterns</span></span>](index.md)
