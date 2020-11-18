---
title: Práticas recomendadas de threading gerenciado
description: Conheça as práticas recomendadas de Threading gerenciadas no .NET. Trabalhe com situações difíceis, como a coordenação de vários threads ou a manipulação de threads de bloqueio.
ms.date: 10/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET], design guidelines
- threading [.NET], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
ms.openlocfilehash: b2a3f2efc12392316f6d90242ef0a9224e7d13a4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826307"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="b594a-104">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="b594a-104">Managed threading best practices</span></span>

<span data-ttu-id="b594a-105">O multithreading requer programação cuidadosa.</span><span class="sxs-lookup"><span data-stu-id="b594a-105">Multithreading requires careful programming.</span></span> <span data-ttu-id="b594a-106">Para a maioria das tarefas, você pode reduzir a complexidade ao enfileirar solicitações para a execução por parte de threads de pool.</span><span class="sxs-lookup"><span data-stu-id="b594a-106">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="b594a-107">Este tópico aborda situações mais difíceis, como coordenar o trabalho de vários threads ou manipular threads que bloqueiam.</span><span class="sxs-lookup"><span data-stu-id="b594a-107">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b594a-108">A partir do .NET Framework 4, a biblioteca paralela de tarefas e o PLINQ fornecem APIs que reduzem parte da complexidade e dos riscos da programação multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="b594a-108">Starting with .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="b594a-109">Para saber mais, confira [Programação paralela em .NET](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="b594a-109">For more information, see [Parallel Programming in .NET](../parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="b594a-110">Deadlocks e condições de corrida</span><span class="sxs-lookup"><span data-stu-id="b594a-110">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="b594a-111">O multithreading resolve problemas com taxa de transferência e capacidade de resposta, mas, ao fazer isso, ele introduz novos problemas: deadlocks e condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="b594a-111">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="b594a-112">Deadlocks</span><span class="sxs-lookup"><span data-stu-id="b594a-112">Deadlocks</span></span>  
 <span data-ttu-id="b594a-113">Um deadlock ocorre quando um dos dois threads tenta bloquear um recurso que o outro já bloqueou.</span><span class="sxs-lookup"><span data-stu-id="b594a-113">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="b594a-114">Nenhum dos threads pode fazer progresso adicional.</span><span class="sxs-lookup"><span data-stu-id="b594a-114">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="b594a-115">Muitos métodos das classes de threading gerenciadas fornecem tempos limite para ajudá-lo a detectar deadlocks.</span><span class="sxs-lookup"><span data-stu-id="b594a-115">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="b594a-116">Por exemplo, o código a seguir tenta adquirir um bloqueio em um objeto denominado `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="b594a-116">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="b594a-117">Se o bloqueio não for obtido em 300 milissegundos, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="b594a-117">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="b594a-118">Condições de corrida</span><span class="sxs-lookup"><span data-stu-id="b594a-118">Race conditions</span></span>  
 <span data-ttu-id="b594a-119">Uma condição de corrida é um bug que ocorre quando o resultado de um programa depende de qual dos dois ou mais threads alcança um determinado bloco de código primeiro.</span><span class="sxs-lookup"><span data-stu-id="b594a-119">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="b594a-120">Executar o programa muitas vezes produz resultados diferentes e o resultado de qualquer execução não pode ser previsto.</span><span class="sxs-lookup"><span data-stu-id="b594a-120">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="b594a-121">Um exemplo simples de uma condição de corrida é incrementar um campo.</span><span class="sxs-lookup"><span data-stu-id="b594a-121">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="b594a-122">Suponha que uma classe tem um campo **static** particular (**Shared** no Visual Basic) que é incrementado toda vez que uma instância da classe é criada, usando um código como `objCt++;` (C#) ou `objCt += 1` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b594a-122">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="b594a-123">Esta operação requer o carregamento do valor de `objCt` em um registro, incrementando o valor e o armazenando em `objCt`.</span><span class="sxs-lookup"><span data-stu-id="b594a-123">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="b594a-124">Em um aplicativo com multithreading, um thread que carregou e incrementou o valor pode ser impedido por outro thread que execute todas as três etapas; quando o primeiro thread retomar a execução e armazenar seu valor, ele substituirá `objCt` sem levar em conta o fato de que o valor foi alterado durante o processo.</span><span class="sxs-lookup"><span data-stu-id="b594a-124">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="b594a-125">Essa condição de corrida específica pode ser evitada facilmente usando métodos da classe <xref:System.Threading.Interlocked>, como <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b594a-125">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b594a-126">Para ler sobre outras técnicas para sincronizar dados entre vários threads, confira [Sincronizando dados para multithreading](synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="b594a-126">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="b594a-127">Condições de corrida também podem ocorrer quando você sincroniza as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="b594a-127">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="b594a-128">Sempre que você escreve uma linha de código, é preciso considerar o que poderia acontecer se um thread fosse impedido antes de executar a linha (ou antes de qualquer uma das instruções de máquina individuais que compõem a linha) e outro thread o substituísse.</span><span class="sxs-lookup"><span data-stu-id="b594a-128">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="b594a-129">Membros estáticos e construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="b594a-129">Static members and static constructors</span></span>  
 <span data-ttu-id="b594a-130">Uma classe não é inicializada até que o construtor de classe (construtor `static` em C#, `Shared Sub New` no Visual Basic) tenha terminado de ser executado.</span><span class="sxs-lookup"><span data-stu-id="b594a-130">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="b594a-131">Para impedir a execução de código em um tipo não inicializado, o Common Language Runtime bloqueia todas as chamadas de outros threads para membros `static` da classe (membros `Shared` no Visual Basic) até que o construtor da classe tenha concluído sua execução.</span><span class="sxs-lookup"><span data-stu-id="b594a-131">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="b594a-132">Por exemplo, se um construtor de classe iniciar um novo thread, e o procedimento do thread chamar um membro `static` da classe, o novo thread bloqueia até que o construtor da classe seja concluído.</span><span class="sxs-lookup"><span data-stu-id="b594a-132">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="b594a-133">Isso se aplica a qualquer tipo que possa ter um construtor `static`.</span><span class="sxs-lookup"><span data-stu-id="b594a-133">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="b594a-134">Número de processadores</span><span class="sxs-lookup"><span data-stu-id="b594a-134">Number of processors</span></span>

<span data-ttu-id="b594a-135">A existência de apenas um ou de vários processadores disponíveis em um sistema pode influenciar a arquitetura de vários threads.</span><span class="sxs-lookup"><span data-stu-id="b594a-135">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="b594a-136">Para obter mais informações, veja [Número de processadores](/previous-versions/dotnet/netframework-1.1/1c9txz50(v=vs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="b594a-136">For more information, see [Number of Processors](/previous-versions/dotnet/netframework-1.1/1c9txz50(v=vs.71)#number-of-processors).</span></span>

<span data-ttu-id="b594a-137">Use a <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> propriedade para determinar o número de processadores disponíveis em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b594a-137">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at run time.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="b594a-138">Recomendações gerais</span><span class="sxs-lookup"><span data-stu-id="b594a-138">General recommendations</span></span>  
 <span data-ttu-id="b594a-139">Ao usar vários threads, considere as seguintes diretrizes:</span><span class="sxs-lookup"><span data-stu-id="b594a-139">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="b594a-140">Não use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> para encerrar outros threads.</span><span class="sxs-lookup"><span data-stu-id="b594a-140">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="b594a-141">Chamar **Abort** em outro thread equivale a gerar uma exceção nesse thread sem saber qual ponto ele alcançou nesse processamento.</span><span class="sxs-lookup"><span data-stu-id="b594a-141">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="b594a-142">Não use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> para sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="b594a-142">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="b594a-143">Use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, e <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="b594a-143">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="b594a-144">Não controle a execução de threads de trabalho do seu programa principal (usando eventos, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="b594a-144">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="b594a-145">Em vez disso, projete seu programa de forma que os threads de trabalho sejam responsáveis por esperar até que o trabalho esteja disponível, executá-lo e notificar outras partes do seu programa quando terminar.</span><span class="sxs-lookup"><span data-stu-id="b594a-145">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="b594a-146">Se seus threads de trabalho não bloquearem, considere o uso de threads de pool.</span><span class="sxs-lookup"><span data-stu-id="b594a-146">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="b594a-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> é útil em situações em que os threads de trabalho bloqueiam.</span><span class="sxs-lookup"><span data-stu-id="b594a-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="b594a-148">Não use tipos como objetos de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b594a-148">Don't use types as lock objects.</span></span> <span data-ttu-id="b594a-149">Isto é, evite códigos como `lock(typeof(X))` em C# ou `SyncLock(GetType(X))` no Visual Basic ou o uso de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> com objetos <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="b594a-149">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="b594a-150">Para um determinado tipo, há apenas uma instância de <xref:System.Type?displayProperty=nameWithType> por domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b594a-150">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="b594a-151">Se o tipo no qual você usar um bloqueio for público, o código que não for o seu próprio poderá assumir bloqueios, levando a deadlocks.</span><span class="sxs-lookup"><span data-stu-id="b594a-151">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="b594a-152">Para problemas adicionais, consulte [Práticas recomendadas de confiabilidade](../../framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="b594a-152">For additional issues, see [Reliability Best Practices](../../framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="b594a-153">Tenha cuidado ao bloquear em instâncias, por exemplo `lock(this)` em C# ou `SyncLock(Me)` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b594a-153">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="b594a-154">Se outro código no seu aplicativo, externo ao tipo, assumir um bloqueio no objeto, podem ocorrer deadlocks.</span><span class="sxs-lookup"><span data-stu-id="b594a-154">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="b594a-155">Certifique-se de que um thread que tenha entrado em um monitor sempre o deixe, mesmo que uma exceção ocorra enquanto o thread estiver no monitor.</span><span class="sxs-lookup"><span data-stu-id="b594a-155">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="b594a-156">A instrução [lock](../../csharp/language-reference/keywords/lock-statement.md) do C# e a instrução [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) do Visual Basic oferece esse comportamento automaticamente, empregando um bloco **finally** para garantir que <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> seja chamado.</span><span class="sxs-lookup"><span data-stu-id="b594a-156">The C# [lock](../../csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="b594a-157">Se você não puder garantir que **Exit** seja chamado, considere alterar o design para usar **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="b594a-157">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="b594a-158">Um mutex é liberado automaticamente quando o thread que o possui atualmente for encerrado.</span><span class="sxs-lookup"><span data-stu-id="b594a-158">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="b594a-159">Usar vários threads para tarefas que exigem recursos diferentes e evite atribuir vários threads para um único recurso.</span><span class="sxs-lookup"><span data-stu-id="b594a-159">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="b594a-160">Por exemplo, qualquer tarefa que envolva E/S se beneficia em ter seu próprio thread, porque esse thread bloqueará durante as operações de E/S e, assim, permitirá que outros threads sejam executados.</span><span class="sxs-lookup"><span data-stu-id="b594a-160">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="b594a-161">A entrada do usuário é outro recurso que se beneficia com um thread dedicado.</span><span class="sxs-lookup"><span data-stu-id="b594a-161">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="b594a-162">Em um computador de um processador, uma tarefa que envolve a computação intensiva coexiste com a entrada do usuário e com tarefas que envolvem E/S, mas várias tarefas competem umas com as outras.</span><span class="sxs-lookup"><span data-stu-id="b594a-162">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="b594a-163">Considere o uso de métodos da classe <xref:System.Threading.Interlocked> para alterações de estado simples, em vez de usar a instrução `lock` (`SyncLock` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b594a-163">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="b594a-164">A instrução `lock` é uma boa ferramenta para fins gerais, mas a classe <xref:System.Threading.Interlocked> oferece um melhor desempenho para atualizações que devem ser atômicas.</span><span class="sxs-lookup"><span data-stu-id="b594a-164">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="b594a-165">Internamente, ela executa um único prefixo de bloqueio se não houver nenhuma contenção.</span><span class="sxs-lookup"><span data-stu-id="b594a-165">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="b594a-166">Em revisões de código, atente para códigos semelhantes aos mostrados nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b594a-166">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="b594a-167">No primeiro exemplo, uma variável de estado é incrementada:</span><span class="sxs-lookup"><span data-stu-id="b594a-167">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="b594a-168">Você pode melhorar o desempenho usando o método <xref:System.Threading.Interlocked.Increment%2A> em vez da instrução `lock`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b594a-168">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="b594a-169">Use o <xref:System.Threading.Interlocked.Add%2A> método para incrementos atômicos maiores que 1.</span><span class="sxs-lookup"><span data-stu-id="b594a-169">Use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="b594a-170">No segundo exemplo, uma variável de tipo de referência é atualizada somente se ela for uma referência nula (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b594a-170">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            x ??= y;
        }  
    }  
    ```  
  
     <span data-ttu-id="b594a-171">É possível melhorar o desempenho usando o método <xref:System.Threading.Interlocked.CompareExchange%2A>, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b594a-171">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="b594a-172">A <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> sobrecarga do método fornece uma alternativa de tipo seguro para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="b594a-172">The <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="b594a-173">Recomendações para bibliotecas de classes</span><span class="sxs-lookup"><span data-stu-id="b594a-173">Recommendations for class libraries</span></span>  
 <span data-ttu-id="b594a-174">Considere as seguintes diretrizes ao criar bibliotecas de classes para multithreading:</span><span class="sxs-lookup"><span data-stu-id="b594a-174">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="b594a-175">Evite a necessidade de sincronização, se possível.</span><span class="sxs-lookup"><span data-stu-id="b594a-175">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="b594a-176">Isso é especialmente válido para o código de uso intensivo.</span><span class="sxs-lookup"><span data-stu-id="b594a-176">This is especially true for heavily used code.</span></span> <span data-ttu-id="b594a-177">Por exemplo, um algoritmo pode ser ajustado para tolerar uma condição de corrida em vez de eliminá-la.</span><span class="sxs-lookup"><span data-stu-id="b594a-177">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="b594a-178">Sincronização desnecessária reduz o desempenho e cria a possibilidade de deadlocks e condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="b594a-178">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="b594a-179">Torne os dados estáticos (`Shared` no Visual Basic) thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="b594a-179">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="b594a-180">Não torne dados de instância thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="b594a-180">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="b594a-181">Adicionar bloqueios para criar códigos de thread-safe reduz o desempenho, aumenta a contenção de bloqueios e cria a possibilidade de deadlocks.</span><span class="sxs-lookup"><span data-stu-id="b594a-181">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="b594a-182">Em modelos de aplicativo comuns, somente um thread por vez executa código do usuário, o que minimiza a necessidade de acesso thread-safe.</span><span class="sxs-lookup"><span data-stu-id="b594a-182">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="b594a-183">Por esse motivo, as bibliotecas de classes do .NET não são thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="b594a-183">For this reason, the .NET class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="b594a-184">Evite fornecer métodos estáticos que alteram o estado estático.</span><span class="sxs-lookup"><span data-stu-id="b594a-184">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="b594a-185">Em cenários de servidor comuns, o estado estático é compartilhado entre as solicitações, que significa que vários threads podem executar esse código ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b594a-185">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="b594a-186">Isso abre a possibilidade de bugs de threading.</span><span class="sxs-lookup"><span data-stu-id="b594a-186">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="b594a-187">Considere usar um padrão de design que encapsule dados em instâncias que não sejam compartilhadas entre solicitações.</span><span class="sxs-lookup"><span data-stu-id="b594a-187">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="b594a-188">Além disso, se os dados estáticos forem sincronizados, chamadas entre os métodos estáticos que alteram o estado podem resultar em deadlocks ou em sincronização redundante, afetando negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="b594a-188">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b594a-189">Confira também</span><span class="sxs-lookup"><span data-stu-id="b594a-189">See also</span></span>

- [<span data-ttu-id="b594a-190">Threading</span><span class="sxs-lookup"><span data-stu-id="b594a-190">Threading</span></span>](index.md)
- [<span data-ttu-id="b594a-191">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="b594a-191">Threads and Threading</span></span>](threads-and-threading.md)
