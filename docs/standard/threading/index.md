---
title: Threading gerenciado
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: d6b8a0a4e16aa3169888958fa1376bfa61526dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137937"
---
# <a name="managed-threading"></a><span data-ttu-id="52922-102">Threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="52922-102">Managed Threading</span></span>
<span data-ttu-id="52922-103">Quer você esteja desenvolvendo para computadores com um processador, quer para com vários, é conveniente que seu aplicativo forneça uma interação mais dinâmica com o usuário, mesmo se o aplicativo, no momento, estiver realizando outro trabalho.</span><span class="sxs-lookup"><span data-stu-id="52922-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="52922-104">Usar vários threads de execução é uma das maneiras mais eficazes de manter seu aplicativo responsivo ao usuário e, ao mesmo tempo, usar o processador entre ou, até mesmo, durante os eventos do usuário.</span><span class="sxs-lookup"><span data-stu-id="52922-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="52922-105">Embora esta seção introduza os conceitos básicos de threading, ele se concentra nos conceitos de threading gerenciado e em como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="52922-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52922-106">Começando no .NET Framework 4, a programação multi-threaded ficou bastante simplificada com as classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, o [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), as novas classes de coleção simultânea no namespace <xref:System.Collections.Concurrent?displayProperty=nameWithType> e um novo modelo de programação que se baseia no conceito de tarefas e não em threads.</span><span class="sxs-lookup"><span data-stu-id="52922-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="52922-107">Para obter mais informações, consulte [Programação Paralela](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="52922-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52922-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="52922-108">In This Section</span></span>  
 [<span data-ttu-id="52922-109">Noções básicas de rosca gerenciadas</span><span class="sxs-lookup"><span data-stu-id="52922-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="52922-110">Fornece uma visão geral de threading gerenciado e descreve quando usar vários threads.</span><span class="sxs-lookup"><span data-stu-id="52922-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="52922-111">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="52922-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="52922-112">Explica como criar, iniciar, pausar, retomar e abortar threads.</span><span class="sxs-lookup"><span data-stu-id="52922-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="52922-113">Práticas recomendadas de rosca gerenciadas</span><span class="sxs-lookup"><span data-stu-id="52922-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="52922-114">Aborda os níveis de sincronização, como evitar deadlocks e condições de corrida, além de outros problemas de threading.</span><span class="sxs-lookup"><span data-stu-id="52922-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="52922-115">Objetos e recursos de rosca</span><span class="sxs-lookup"><span data-stu-id="52922-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="52922-116">Descreve as classes gerenciadas que você pode usar para sincronizar as atividades de threads e os dados de objetos acessados em threads diferentes, bem como fornece uma visão geral dos threads de pool do thread.</span><span class="sxs-lookup"><span data-stu-id="52922-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="52922-117">Referência</span><span class="sxs-lookup"><span data-stu-id="52922-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="52922-118">Contém classes para uso e sincronização de threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="52922-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="52922-119">Contém classes de coleção que são seguras para uso com vários threads.</span><span class="sxs-lookup"><span data-stu-id="52922-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="52922-120">Contém classes para criação e agendamento de tarefas de processamento simultâneo.</span><span class="sxs-lookup"><span data-stu-id="52922-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52922-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="52922-121">Related Sections</span></span>  
 [<span data-ttu-id="52922-122">Domínios de aplicativo</span><span class="sxs-lookup"><span data-stu-id="52922-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="52922-123">Fornece uma visão geral de domínios do aplicativo e seu uso pelo Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="52922-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="52922-124">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="52922-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="52922-125">Descreve as vantagens de desempenho e a operação básica da E/S assíncrona.</span><span class="sxs-lookup"><span data-stu-id="52922-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="52922-126">TAP (Padrão Assíncrono Baseado em Tarefa)</span><span class="sxs-lookup"><span data-stu-id="52922-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="52922-127">Fornece uma visão geral do padrão recomendado para programação assíncrona no .NET.</span><span class="sxs-lookup"><span data-stu-id="52922-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="52922-128">Chamar métodos síncronos de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="52922-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="52922-129">Explica como chamar métodos nos threads de pool do thread usando recursos internos de representantes.</span><span class="sxs-lookup"><span data-stu-id="52922-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="52922-130">Programação Paralela</span><span class="sxs-lookup"><span data-stu-id="52922-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="52922-131">Descreve as bibliotecas de programação paralela, que simplificam o uso de vários threads em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="52922-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="52922-132">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="52922-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="52922-133">Descreve um sistema para executar consultas paralelamente, de modo a aproveitar vários processadores.</span><span class="sxs-lookup"><span data-stu-id="52922-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
