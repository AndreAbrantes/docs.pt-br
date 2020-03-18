---
title: O padrão de eventos atualizado do .NET Core Event
description: Saiba como o padrão de evento do .NET Core permite flexibilidade com compatibilidade com versões anteriores e como implementar processamento de eventos seguro com assinantes assíncronos.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: c8858158ede761db8a3002beb26e521880f77feb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170430"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="c5d9d-103">O padrão de eventos atualizado do .NET Core Event</span><span class="sxs-lookup"><span data-stu-id="c5d9d-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="c5d9d-104">Anterior</span><span class="sxs-lookup"><span data-stu-id="c5d9d-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="c5d9d-105">O artigo anterior abordou os padrões de eventos mais comuns.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="c5d9d-106">O .NET Core tem um padrão mais flexível.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="c5d9d-107">Nesta versão, a definição `EventHandler<TEventArgs>` não tem a restrição de que `TEventArgs` deve ser uma classe derivada de `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="c5d9d-108">Isso aumenta a flexibilidade para você e é compatível com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="c5d9d-109">Vamos começar com a flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-109">Let's start with the flexibility.</span></span> <span data-ttu-id="c5d9d-110">A classe System.EventArgs introduz um método: `MemberwiseClone()`, que cria uma cópia superficial do objeto.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="c5d9d-111">Esse método deve usar a reflexão para implementar sua funcionalidade para qualquer classe derivada de `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="c5d9d-112">Essa funcionalidade é mais fácil de criar em uma classe derivada específica.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="c5d9d-113">Na prática, isso significa que a derivação de System.EventArgs é uma restrição que limita seus designs, mas não oferece nenhum benefício adicional.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="c5d9d-114">Na verdade, você pode alterar as definições de `FileFoundArgs` e `SearchDirectoryArgs` para que eles não derivem de `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="c5d9d-115">O programa funcionará exatamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-115">The program will work exactly the same.</span></span>

<span data-ttu-id="c5d9d-116">Você também pode alterar o `SearchDirectoryArgs` para um struct, se você fizer mais uma alteração:</span><span class="sxs-lookup"><span data-stu-id="c5d9d-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

<span data-ttu-id="c5d9d-117">A alteração adicional é chamar o construtor sem parâmetro antes de inserir o construtor que inicializa todos os campos.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="c5d9d-118">Sem esse acréscimo, as regras de C# informariam que as propriedades estão sendo acessadas antes de terem sido atribuídas.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="c5d9d-119">Você não deve alterar o `FileFoundArgs` de uma classe (tipo de referência) para um struct (tipo de valor).</span><span class="sxs-lookup"><span data-stu-id="c5d9d-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="c5d9d-120">Isso ocorre porque o protocolo para manipular cancelamentos exige que os argumentos do evento sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="c5d9d-121">Se você fizesse a mesma alteração, a classe de pesquisa de arquivo nunca observaria as alterações feitas por qualquer um dos assinantes do evento.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="c5d9d-122">Uma nova cópia da estrutura seria usada para cada assinante e essa cópia seria uma cópia diferente daquela vista pelo objeto de pesquisa de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="c5d9d-123">Em seguida, vamos considerar como essa alteração pode ser compatível com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="c5d9d-124">A remoção da restrição não afeta nenhum código existente.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="c5d9d-125">Qualquer tipo de argumento de evento existente ainda deriva de `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="c5d9d-126">A compatibilidade com versões anteriores é um dos principais motivos pelos quais eles vão continuar derivando de `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="c5d9d-127">Assinantes de eventos existentes serão assinantes de um evento que seguiu o padrão clássico.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="c5d9d-128">Seguindo uma lógica semelhante, qualquer tipo de argumento de evento criado agora não teria assinantes nas bases de código existentes.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="c5d9d-129">Novos tipos de evento que não derivam de `System.EventArgs` não quebram essas bases de código.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="c5d9d-130">Eventos com assinantes assíncronos</span><span class="sxs-lookup"><span data-stu-id="c5d9d-130">Events with Async subscribers</span></span>

<span data-ttu-id="c5d9d-131">Você tem um último padrão para aprender: como escrever corretamente os assinantes do evento que chamam o código assíncrono.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="c5d9d-132">O desafio é descrito no artigo em [async e await](async.md).</span><span class="sxs-lookup"><span data-stu-id="c5d9d-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="c5d9d-133">Métodos assíncronos podem ter um tipo de retorno nulo, mas isso não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="c5d9d-134">Quando seu código de assinante de evento chama um método assíncrono, você não terá outra escolha além de criar um método `async void`.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="c5d9d-135">A assinatura do manipulador de eventos o exige.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-135">The event handler signature requires it.</span></span>

<span data-ttu-id="c5d9d-136">Você precisa conciliar essas diretrizes opostas.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="c5d9d-137">De alguma forma, você precisa criar um método `async void` seguro.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="c5d9d-138">As noções básicas do padrão que você precisa implementar estão abaixo:</span><span class="sxs-lookup"><span data-stu-id="c5d9d-138">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="c5d9d-139">Primeiro, observe que o manipulador está marcado como um manipulador assíncrono.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="c5d9d-140">Como está sendo atribuído a um tipo de delegado de manipulador de eventos, ele terá um tipo de retorno nulo.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="c5d9d-141">Isso significa que você deve seguir o padrão mostrado no manipulador e não permitir que qualquer exceção seja gerada fora do contexto do manipulador assíncrono.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="c5d9d-142">Como ele não retorna uma tarefa, não há nenhuma tarefa que pode relatar o erro entrando no estado de falha.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="c5d9d-143">Como o método é assíncrono, ele não pode simplesmente gerar a exceção.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="c5d9d-144">(O método de chamada continuou `async`a execução porque é .) O comportamento de tempo de execução real será definido de forma diferente para diferentes ambientes.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="c5d9d-145">Ele pode encerrar o segmento ou o processo que possui o segmento, ou deixar o processo em um estado indeterminado.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-145">It may terminate the thread or the process that owns the thread, or leave the process in an indeterminate state.</span></span> <span data-ttu-id="c5d9d-146">Todos esses resultados potenciais são altamente indesejáveis.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-146">All of these potential outcomes are highly undesirable.</span></span>

<span data-ttu-id="c5d9d-147">É por isso que você deve encapsular a instrução await para a tarefa assíncrona em seu próprio bloco de teste.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="c5d9d-148">Se isso causar uma tarefa com falha, você pode registrar o erro em log.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="c5d9d-149">Se for um erro do qual não é possível recuperar o aplicativo, você pode sair do programa rápida e normalmente</span><span class="sxs-lookup"><span data-stu-id="c5d9d-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="c5d9d-150">Essas são as principais atualizações do padrão de eventos do .NET.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="c5d9d-151">Você verá muitos exemplos das versões anteriores nas bibliotecas com que trabalhar.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="c5d9d-152">No entanto, você também precisa compreender quais são os padrões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="c5d9d-153">O próximo artigo desta série ajuda a distinguir entre o uso de `delegates` e de `events` em seus designs.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="c5d9d-154">Eles são conceitos similares e artigo o ajudará a tomar a melhor decisão para seus programas.</span><span class="sxs-lookup"><span data-stu-id="c5d9d-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="c5d9d-155">Avançar</span><span class="sxs-lookup"><span data-stu-id="c5d9d-155">Next</span></span>](distinguish-delegates-events.md)
