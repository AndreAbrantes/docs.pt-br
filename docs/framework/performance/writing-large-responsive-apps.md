---
title: Escrevendo aplicativos .NET Framework grandes e dinâmicos
description: Grave aplicativos .NET responsivos ou grandes, ou aplicativos que processam uma grande quantidade de dados, como arquivos ou bancos de dado.
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b1c9ab25299fcbafca6aba7b13217713a941ce8
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475184"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="03957-103">Escrevendo aplicativos .NET Framework grandes e dinâmicos</span><span class="sxs-lookup"><span data-stu-id="03957-103">Writing Large, Responsive .NET Framework Apps</span></span>

<span data-ttu-id="03957-104">Este artigo apresenta dicas para melhorar o desempenho de grandes aplicativos do .NET Framework ou aplicativos que processam um grande volume de dados, como arquivos ou bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="03957-104">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="03957-105">Essas dicas vêm da nova gravação de compiladores do C# e do Visual Basic em código gerenciado, e este artigo inclui diversos exemplos reais do compilador do C#.</span><span class="sxs-lookup"><span data-stu-id="03957-105">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>
  
<span data-ttu-id="03957-106">O .NET Framework é altamente produtivo para compilar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="03957-106">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="03957-107">Linguagens eficientes e seguras e uma coleção sofisticada de bibliotecas tornam a compilação de aplicativos altamente produtiva.</span><span class="sxs-lookup"><span data-stu-id="03957-107">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="03957-108">Porém, grande produtividade traz muita responsabilidade.</span><span class="sxs-lookup"><span data-stu-id="03957-108">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="03957-109">Você deve usar toda a potência do .NET Framework, mas esteja preparado para ajustar o desempenho do código quando necessário.</span><span class="sxs-lookup"><span data-stu-id="03957-109">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="03957-110">Por que o desempenho do novo compilador se aplica ao seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="03957-110">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="03957-111">A equipe do .NET Compiler Platform ("Roslyn") reescreveu os compiladores do C# e do Visual Basic em código gerenciado para fornecer novas APIs para modelar e analisar códigos, compilar ferramentas e possibilitar experiências de código mais sofisticadas no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03957-111">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="03957-112">A nova gravação de compiladores e a criação de experiências do Visual Studio para os novos compiladores revelaram informações úteis sobre o desempenho, aplicáveis a qualquer aplicativo grande do .NET Framework ou qualquer aplicativo que processe muitos dados.</span><span class="sxs-lookup"><span data-stu-id="03957-112">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="03957-113">Não é preciso ter conhecimento de compiladores para aproveitar as informações e os exemplos do compilador do C#.</span><span class="sxs-lookup"><span data-stu-id="03957-113">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>
  
 <span data-ttu-id="03957-114">O Visual Studio usa as APIs do compilador para compilar todos os recursos do IntelliSense adorados pelos usuários, como colorização de identificadores e palavras-chave, listas de conclusão de sintaxe, soluções para erros, dicas de parâmetro, problemas de código e ações de código.</span><span class="sxs-lookup"><span data-stu-id="03957-114">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="03957-115">O Visual Studio oferece essa ajuda enquanto os desenvolvedores estão digitando e alterando seus códigos e ele deve continuar respondendo enquanto o compilador modela continuamente a edição do desenvolvedor do código.</span><span class="sxs-lookup"><span data-stu-id="03957-115">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>
  
 <span data-ttu-id="03957-116">Ao interagir com o aplicativo, os usuários finais esperam que ele seja ágil na resposta.</span><span class="sxs-lookup"><span data-stu-id="03957-116">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="03957-117">A digitação ou a manipulação de comandos jamais deve ser bloqueada.</span><span class="sxs-lookup"><span data-stu-id="03957-117">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="03957-118">A Ajuda deverá ser exibida rapidamente ou fechada se o usuário continuar digitando.</span><span class="sxs-lookup"><span data-stu-id="03957-118">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="03957-119">O aplicativo deve evitar o bloqueio do thread da interface do usuário com computações longas, que aparentemente deixam o aplicativo lento.</span><span class="sxs-lookup"><span data-stu-id="03957-119">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>
  
 <span data-ttu-id="03957-120">Para obter mais informações sobre compiladores do Roslyn, consulte [o SDK do .net Compiler Platform](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="03957-120">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="03957-121">Aos fatos</span><span class="sxs-lookup"><span data-stu-id="03957-121">Just the Facts</span></span>  
 <span data-ttu-id="03957-122">Considere estes fatos ao ajustar o desempenho e criar aplicativos do .NET Framework ágeis na resposta.</span><span class="sxs-lookup"><span data-stu-id="03957-122">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="03957-123">Fato 1: não otimize de forma prematura</span><span class="sxs-lookup"><span data-stu-id="03957-123">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="03957-124">Gravar um código mais complexo do que o necessário acarreta custos de manutenção, depuração e acabamento.</span><span class="sxs-lookup"><span data-stu-id="03957-124">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="03957-125">Os programadores experientes têm uma compreensão intuitiva de como resolver problemas de codificação e gravar um código mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="03957-125">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="03957-126">Porém, às vezes, eles otimizam o código antes.</span><span class="sxs-lookup"><span data-stu-id="03957-126">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="03957-127">Por exemplo, eles usam uma tabela hash quando uma simples matriz bastaria ou usam um cache complicado que pode causar perda de memória, em vez de simplesmente recalcular os valores.</span><span class="sxs-lookup"><span data-stu-id="03957-127">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="03957-128">Mesmo que não seja um programador experiente, você deve testar o desempenho e analisar o código quando encontrar problemas.</span><span class="sxs-lookup"><span data-stu-id="03957-128">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="03957-129">Fato 2: se você não está medindo, está adivinhando</span><span class="sxs-lookup"><span data-stu-id="03957-129">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="03957-130">Os perfis e as medidas não mentem.</span><span class="sxs-lookup"><span data-stu-id="03957-130">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="03957-131">Os perfis mostram se a CPU está totalmente carregada ou se há um bloqueio na E/S do disco.</span><span class="sxs-lookup"><span data-stu-id="03957-131">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="03957-132">Os perfis informam o tipo e a quantidade de memória que está sendo alocada e se a CPU está gastando muito tempo no [GC](../../standard/garbage-collection/index.md) (coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="03957-132">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span>
  
 <span data-ttu-id="03957-133">Estabeleça metas de desempenho para experiências ou cenários importantes do cliente no aplicativo e gravar testes para avaliar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="03957-133">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="03957-134">Investigue testes com falha aplicando o método científico: use perfis para orientá-lo, crie hipóteses sobre qual seria o problema e teste as hipóteses com um experimento ou uma alteração feita no código.</span><span class="sxs-lookup"><span data-stu-id="03957-134">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="03957-135">Estabeleça medidas de desempenho de linha de base com o passar do tempo, usando testes regulares para que seja possível isolar as alterações que causam regressões no desempenho.</span><span class="sxs-lookup"><span data-stu-id="03957-135">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="03957-136">Abordando o trabalho de desempenho de maneira rigorosa, você evitará a perda de tempo com atualizações desnecessárias de código.</span><span class="sxs-lookup"><span data-stu-id="03957-136">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="03957-137">Fato 3: boas ferramentas fazem toda a diferença</span><span class="sxs-lookup"><span data-stu-id="03957-137">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="03957-138">As boas ferramentas permitem chegar rapidamente aos maiores problemas de desempenho (CPU, memória ou disco) e ajudam a alocar o código que causa esses gargalos.</span><span class="sxs-lookup"><span data-stu-id="03957-138">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="03957-139">A Microsoft fornece uma variedade de ferramentas de desempenho, como o [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) e o [Perfview](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="03957-139">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span>
  
 <span data-ttu-id="03957-140">PerfView é uma ferramenta gratuita e incrivelmente eficiente que ajuda você a se concentrar em problemas intensos, como E/S de disco, eventos de GC e memória.</span><span class="sxs-lookup"><span data-stu-id="03957-140">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="03957-141">Capture eventos [ETW](../wcf/samples/etw-tracing.md) (Rastreamento de Eventos para Windows) relacionados ao desempenho e exiba informações por aplicativo, processo, pilha e thread com facilidade.</span><span class="sxs-lookup"><span data-stu-id="03957-141">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="03957-142">O PerfView mostra quanto e que tipo de memória o aplicativo aloca, além de quais funções ou pilhas de chamadas contribuem para a quantidade de alocações da memória.</span><span class="sxs-lookup"><span data-stu-id="03957-142">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="03957-143">Para obter detalhes, consulte os tópicos avançados da ajuda, as demonstrações e os vídeos incluídos com a ferramenta (como os [tutoriais do PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) no Channel 9).</span><span class="sxs-lookup"><span data-stu-id="03957-143">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="03957-144">Fato 4: é tudo uma questão de alocação</span><span class="sxs-lookup"><span data-stu-id="03957-144">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="03957-145">Convém pensar que compilar um aplicativo do .NET Framework ágil na resposta é uma questão de algoritmos, como usar a classificação rápida em vez da classificação de bolhas, mas não é esse o caso.</span><span class="sxs-lookup"><span data-stu-id="03957-145">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="03957-146">O maior fator na compilação de um aplicativo ágil na resposta é alocar memória, especialmente quando o aplicativo é muito grande ou processa grandes volumes de dados.</span><span class="sxs-lookup"><span data-stu-id="03957-146">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>
  
 <span data-ttu-id="03957-147">Praticamente todo o trabalho de compilação de experiências IDE ágeis na resposta com as APIs do novo compilador envolveu evitar alocações e gerenciar estratégias de cache.</span><span class="sxs-lookup"><span data-stu-id="03957-147">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="03957-148">Os rastreamentos do PerfView mostram que o desempenho dos novos compiladores do C# e do Visual Basic raramente está associado à CPU.</span><span class="sxs-lookup"><span data-stu-id="03957-148">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="03957-149">Os compiladores podem estar associados à E/S na leitura de milhares ou milhões de linhas de código, de metadados ou na emissão de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="03957-149">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="03957-150">Os atrasos do thread da interface do usuário são praticamente todos por conta da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="03957-150">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="03957-151">A GC do .NET Framework está totalmente ajustada para o desempenho e faz boa parte de seu trabalho junto com a execução do código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="03957-151">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="03957-152">Porém, uma única alocação pode disparar uma coleta [gen2](../../standard/garbage-collection/fundamentals.md) cara, interrompendo todos os threads.</span><span class="sxs-lookup"><span data-stu-id="03957-152">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="03957-153">Alocações e exemplos comuns</span><span class="sxs-lookup"><span data-stu-id="03957-153">Common allocations and examples</span></span>  
 <span data-ttu-id="03957-154">As expressões de exemplo nesta seção têm alocações ocultas aparentemente pequenas.</span><span class="sxs-lookup"><span data-stu-id="03957-154">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="03957-155">Porém, se um aplicativo grande executar as expressões o número de vezes suficiente, elas poderão causar centenas de megabytes, até mesmo gigabytes, de alocações.</span><span class="sxs-lookup"><span data-stu-id="03957-155">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="03957-156">Por exemplo, testes de um minuto que simulavam a digitação de um desenvolvedor no editor alocaram gigabytes de memória e permitiram que a equipe de desenvolvimento se concentrasse nos cenários de digitação.</span><span class="sxs-lookup"><span data-stu-id="03957-156">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>
  
### <a name="boxing"></a><span data-ttu-id="03957-157">Conversão boxing</span><span class="sxs-lookup"><span data-stu-id="03957-157">Boxing</span></span>  
 <span data-ttu-id="03957-158">A [conversão boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) ocorre quando tipos de valor, que normalmente residem na pilha ou nas estruturas de dados, são encapsulados em um objeto.</span><span class="sxs-lookup"><span data-stu-id="03957-158">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="03957-159">Ou seja, você aloca um objeto para manter os dados e retorna um ponteiro para o objeto.</span><span class="sxs-lookup"><span data-stu-id="03957-159">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="03957-160">Às vezes, o .NET Framework realiza a conversão boxing de valores por conta da assinatura de um método ou do tipo de local de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="03957-160">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="03957-161">A disposição de um tipo de valor em um objeto causa alocação da memória.</span><span class="sxs-lookup"><span data-stu-id="03957-161">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="03957-162">Muitas operações de conversão boxing podem proporcionar megabytes ou gigabytes de alocações no aplicativo, o que significa que o aplicativo causará mais GCs.</span><span class="sxs-lookup"><span data-stu-id="03957-162">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="03957-163">O .NET Framework e os compiladores de linguagem evitam a conversão boxing sempre que possível, mas às vezes ela acontece quando você menos espera.</span><span class="sxs-lookup"><span data-stu-id="03957-163">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>
  
 <span data-ttu-id="03957-164">Para ver a conversão boxing no PerfView, abra um rastreamento e observe GC Heap Alloc Stacks abaixo do nome de processo do aplicativo (lembre-se de que o PerfView relata todos os processos).</span><span class="sxs-lookup"><span data-stu-id="03957-164">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="03957-165">Caso veja tipos como <xref:System.Int32?displayProperty=nameWithType> e <xref:System.Char?displayProperty=nameWithType> sob as alocações, você está realizando a conversão boxing dos tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="03957-165">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="03957-166">A escolha de um desses tipos mostrará as pilhas e as funções nas quais a conversão boxing é realizada.</span><span class="sxs-lookup"><span data-stu-id="03957-166">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>
  
 <span data-ttu-id="03957-167">**Exemplo 1: métodos de cadeia de caracteres e argumentos de tipo de valor**</span><span class="sxs-lookup"><span data-stu-id="03957-167">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="03957-168">Este código de exemplo ilustra a conversão boxing excessiva e possivelmente desnecessária:</span><span class="sxs-lookup"><span data-stu-id="03957-168">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 <span data-ttu-id="03957-169">Como esse código oferece funcionalidade de registro em log, um aplicativo pode chamar a função `Log` com frequência, talvez milhões de vezes.</span><span class="sxs-lookup"><span data-stu-id="03957-169">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="03957-170">O problema é que a chamada para o `string.Format` é resolvida para a sobrecarga <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="03957-170">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>
  
 <span data-ttu-id="03957-171">Essa sobrecarga exige que o .NET Framework realize a conversão boxing dos valores `int` em objetos a fim de passá-los para essa chamada de método.</span><span class="sxs-lookup"><span data-stu-id="03957-171">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="03957-172">Uma correção parcial é chamar `id.ToString()` e `size.ToString()` e passar todas as cadeias de caracteres (que são objetos) para a chamada `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="03957-172">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="03957-173">A chamada de `ToString()` não aloca uma cadeia de caracteres, mas essa alocação ainda acontecerá em `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="03957-173">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>
  
 <span data-ttu-id="03957-174">Talvez você ache que essa chamada básica para `string.Format` seja apenas uma concatenação da cadeia de caracteres, dessa forma, será possível gravar esse código em seu lugar:</span><span class="sxs-lookup"><span data-stu-id="03957-174">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="03957-175">Porém, essa linha de código introduz uma alocação de conversão boxing porque ela é compilada para <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="03957-175">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="03957-176">O .NET Framework deve realizar a conversão boxing do literal de caractere para invocar `Concat`</span><span class="sxs-lookup"><span data-stu-id="03957-176">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="03957-177">**Correção para o exemplo 1**</span><span class="sxs-lookup"><span data-stu-id="03957-177">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="03957-178">A correção completa é simples.</span><span class="sxs-lookup"><span data-stu-id="03957-178">The complete fix is simple.</span></span> <span data-ttu-id="03957-179">Basta substituir o literal de caractere por um literal da cadeia de caracteres, que não acarreta conversão boxing porque as cadeias de caracteres já são objetos:</span><span class="sxs-lookup"><span data-stu-id="03957-179">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="03957-180">**Exemplo 2: conversão boxing de enum**</span><span class="sxs-lookup"><span data-stu-id="03957-180">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="03957-181">Esse exemplo foi responsável por um grande volume de alocação nos novos compiladores do C# e do Visual Basic por conta do uso frequente de tipos de enumeração, especialmente em operações de pesquisa de dicionário.</span><span class="sxs-lookup"><span data-stu-id="03957-181">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 <span data-ttu-id="03957-182">Esse problema é muito sutil.</span><span class="sxs-lookup"><span data-stu-id="03957-182">This problem is very subtle.</span></span> <span data-ttu-id="03957-183">O PerfView relataria isso como conversão boxing de <xref:System.Enum.GetHashCode> porque o método realiza a conversão boxing da representação subjacente do tipo de enumeração por motivos de implementação.</span><span class="sxs-lookup"><span data-stu-id="03957-183">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="03957-184">Se observar atentamente o PerfView, você poderá ver duas alocações de conversão boxing para cada chamada para <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="03957-184">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="03957-185">O compilador insere uma e o .NET Framework insere a outra.</span><span class="sxs-lookup"><span data-stu-id="03957-185">The compiler inserts one, and the .NET Framework inserts the other.</span></span>
  
 <span data-ttu-id="03957-186">**Correção para o exemplo 2**</span><span class="sxs-lookup"><span data-stu-id="03957-186">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="03957-187">É possível evitar facilmente as duas alocações com a transmissão da representação subjacente antes de chamar <xref:System.Enum.GetHashCode>:</span><span class="sxs-lookup"><span data-stu-id="03957-187">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="03957-188">Outra fonte comum de conversão boxing em tipos de enumeração é o método <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="03957-188">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="03957-189">O argumento passado para <xref:System.Enum.HasFlag%28System.Enum%29> precisa passar pela conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="03957-189">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="03957-190">Na maioria dos casos, a substituição das chamadas <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> por um teste bit a bit é mais simples e sem alocação.</span><span class="sxs-lookup"><span data-stu-id="03957-190">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>
  
 <span data-ttu-id="03957-191">Mantenha o fator do primeiro desempenho em mente (ou seja, não otimize antes) e não comece a gravar novamente todo o código dessa forma.</span><span class="sxs-lookup"><span data-stu-id="03957-191">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="03957-192">Esteja atento aos custos da conversão boxing, mas só altere o código depois de criar o perfil do aplicativo e encontrar os pontos de acesso.</span><span class="sxs-lookup"><span data-stu-id="03957-192">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>
  
### <a name="strings"></a><span data-ttu-id="03957-193">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="03957-193">Strings</span></span>  
 <span data-ttu-id="03957-194">As manipulações da cadeia de caracteres são as maiores responsáveis pelas alocações e costumam aparecer no PerfView entre as cinco primeiras alocações.</span><span class="sxs-lookup"><span data-stu-id="03957-194">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="03957-195">Os programas usam cadeias de caracteres na serialização, em JSON e nas APIs REST.</span><span class="sxs-lookup"><span data-stu-id="03957-195">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="03957-196">É possível usar cadeias de caracteres como constantes programáticas na interoperação com sistemas quando não é possível usar tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="03957-196">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="03957-197">Quando a criação de perfis mostrar que as cadeias de caracteres estão afetando muito o desempenho, procure chamadas para métodos <xref:System.String> como <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A> e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="03957-197">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="03957-198">O uso de <xref:System.Text.StringBuilder> para evitar o custo com a criação de uma cadeia de caracteres com base em muitas peças ajuda, mas mesmo a alocação do objeto <xref:System.Text.StringBuilder> pode se tornar um gargalo que precisa ser gerenciado.</span><span class="sxs-lookup"><span data-stu-id="03957-198">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>
  
 <span data-ttu-id="03957-199">**Exemplo 3: operações da cadeia de caracteres**</span><span class="sxs-lookup"><span data-stu-id="03957-199">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="03957-200">O compilador do C# tinha este código que grava o texto de um comentário em documento formatado em XML:</span><span class="sxs-lookup"><span data-stu-id="03957-200">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 <span data-ttu-id="03957-201">É possível ver que esse código faz muita manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="03957-201">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="03957-202">O código usa métodos de biblioteca para dividir linhas em cadeias de caracteres separadas, cortar espaços em branco, verificar se o argumento `text` é um comentário de documentação em XML e extrair subcadeias de caracteres das linhas.</span><span class="sxs-lookup"><span data-stu-id="03957-202">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>
  
 <span data-ttu-id="03957-203">Na primeira linha do `WriteFormattedDocComment`, sempre que ocorre a chamada `text.Split`, ela aloca uma nova matriz de três elementos como o argumento.</span><span class="sxs-lookup"><span data-stu-id="03957-203">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="03957-204">O compilador sempre precisa emitir o código para alocar essa matriz.</span><span class="sxs-lookup"><span data-stu-id="03957-204">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="03957-205">Isso porque o compilador não sabe se <xref:System.String.Split%2A> armazena a matriz em um lugar onde a matriz pode ser modificada por outro código, o que afetaria chamadas posteriores para `WriteFormattedDocComment`.</span><span class="sxs-lookup"><span data-stu-id="03957-205">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="03957-206">A chamada para <xref:System.String.Split%2A> também aloca uma cadeia de caracteres para cada linha em `text` e aloca outra memória para realizar a operação.</span><span class="sxs-lookup"><span data-stu-id="03957-206">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>
  
 <span data-ttu-id="03957-207">`WriteFormattedDocComment` tem três chamadas ao método <xref:System.String.TrimStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="03957-207">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="03957-208">Duas estão em loops internos que duplicam o trabalho e as alocações.</span><span class="sxs-lookup"><span data-stu-id="03957-208">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="03957-209">Para piorar as coisas, a chamada do método <xref:System.String.TrimStart%2A> sem argumentos aloca uma matriz vazia (para o parâmetro `params`) além do resultado da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="03957-209">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>
  
 <span data-ttu-id="03957-210">Por fim, existe uma chamada para o método <xref:System.String.Substring%2A>, que normalmente aloca uma nova cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="03957-210">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>
  
 <span data-ttu-id="03957-211">**Correção para o exemplo 3**</span><span class="sxs-lookup"><span data-stu-id="03957-211">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="03957-212">Diferentemente dos exemplos anteriores, pequenas edições não podem corrigir essas alocações.</span><span class="sxs-lookup"><span data-stu-id="03957-212">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="03957-213">É preciso voltar, observar o problema e abordá-lo de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="03957-213">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="03957-214">Por exemplo, você verá que o argumento para `WriteFormattedDocComment()` é uma cadeia de caracteres com todas as informações de que o método precisa, para que o código pudesse fazer mais indexação em vez de alocar muitas cadeias de caracteres parciais.</span><span class="sxs-lookup"><span data-stu-id="03957-214">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>
  
 <span data-ttu-id="03957-215">A equipe de desempenho do compilador resolveu todas essas alocações com códigos como este:</span><span class="sxs-lookup"><span data-stu-id="03957-215">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...
```  
  
 <span data-ttu-id="03957-216">A primeira versão de `WriteFormattedDocComment()` alocava uma matriz, diversas subcadeias de caracteres e uma subcadeia de caracteres cortada com uma matriz `params` vazia.</span><span class="sxs-lookup"><span data-stu-id="03957-216">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="03957-217">Ele também verificou "///".</span><span class="sxs-lookup"><span data-stu-id="03957-217">It also checked for "///".</span></span> <span data-ttu-id="03957-218">O código revisado usa apenas a indexação e não aloca nada.</span><span class="sxs-lookup"><span data-stu-id="03957-218">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="03957-219">Ele localiza o primeiro caractere que não é espaço em branco e, em seguida, verifica o caractere por caractere para ver se a cadeia de caracteres começa com "///".</span><span class="sxs-lookup"><span data-stu-id="03957-219">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="03957-220">O novo código usa `IndexOfFirstNonWhiteSpaceChar` em vez de <xref:System.String.TrimStart%2A> para retornar o primeiro índice (após um índice inicial especificado) em que um caractere que não seja espaço em branco ocorre.</span><span class="sxs-lookup"><span data-stu-id="03957-220">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="03957-221">A correção não está completa, mas é possível ver como aplicar correções semelhantes para uma solução completa.</span><span class="sxs-lookup"><span data-stu-id="03957-221">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="03957-222">Aplicando essa abordagem em todo o código, é possível remover todas as alocações em `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="03957-222">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>
  
 <span data-ttu-id="03957-223">**Exemplo 4: StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="03957-223">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="03957-224">Este exemplo usa um objeto <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="03957-224">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="03957-225">A função a seguir gera um nome de tipo completo para tipos genéricos:</span><span class="sxs-lookup"><span data-stu-id="03957-225">The following function generates a full type name for generic types:</span></span>  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 <span data-ttu-id="03957-226">O foco está na linha que cria uma nova instância <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="03957-226">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="03957-227">O código causa uma alocação para `sb.ToString()` e alocações internas dentro da implementação <xref:System.Text.StringBuilder>, mas não será possível controlar essas alocações se você quiser o resultado da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="03957-227">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>
  
 <span data-ttu-id="03957-228">**Correção para o exemplo 4**</span><span class="sxs-lookup"><span data-stu-id="03957-228">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="03957-229">Para corrigir a alocação do objeto `StringBuilder`, armazene o objeto em cache.</span><span class="sxs-lookup"><span data-stu-id="03957-229">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="03957-230">Mesmo o armazenamento em cache de uma única instância que pode ser descartada pode melhorar significativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="03957-230">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="03957-231">Essa é a nova implementação da função, omitindo todo o código, exceto as primeiras e as últimas linhas novas:</span><span class="sxs-lookup"><span data-stu-id="03957-231">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="03957-232">As partes-chave são as novas funções `AcquireBuilder()` e `GetStringAndReleaseBuilder()`:</span><span class="sxs-lookup"><span data-stu-id="03957-232">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 <span data-ttu-id="03957-233">Como os novos compiladores usam o threading, essas implementações usam um campo com thread estático (atributo <xref:System.ThreadStaticAttribute>) para armazenar em cache o <xref:System.Text.StringBuilder> e você certamente pode esquecer a declaração `ThreadStatic`.</span><span class="sxs-lookup"><span data-stu-id="03957-233">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="03957-234">O campo com thread estático mantém um valor exclusivo para cada thread que executa esse código.</span><span class="sxs-lookup"><span data-stu-id="03957-234">The thread-static field holds a unique value for each thread that executes this code.</span></span>
  
 <span data-ttu-id="03957-235">`AcquireBuilder()` retornará a instância de <xref:System.Text.StringBuilder> armazenada em cache se houver uma, depois de limpá-la e definir o campo ou o cache como nulo.</span><span class="sxs-lookup"><span data-stu-id="03957-235">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="03957-236">Do contrário, `AcquireBuilder()` cria uma nova instância e a retorna, deixando o campo ou o cache definido com nulo.</span><span class="sxs-lookup"><span data-stu-id="03957-236">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>
  
 <span data-ttu-id="03957-237">Quando concluir o <xref:System.Text.StringBuilder>, você poderá chamar `GetStringAndReleaseBuilder()` para obter o resultado da cadeia de caracteres, salvar a instância de <xref:System.Text.StringBuilder> no campo ou no cache e retornar o resultado.</span><span class="sxs-lookup"><span data-stu-id="03957-237">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="03957-238">Para a execução, é possível reinserir esse código e criar vários objetos <xref:System.Text.StringBuilder> (embora isso raramente aconteça).</span><span class="sxs-lookup"><span data-stu-id="03957-238">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="03957-239">O código salva apenas a última instância de <xref:System.Text.StringBuilder> lançada para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="03957-239">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="03957-240">Essa estratégia de cache simples reduziu significativamente as alocações nos novos compiladores.</span><span class="sxs-lookup"><span data-stu-id="03957-240">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="03957-241">Partes do .NET Framework e do MSBuild (“MSBuild”) usam uma técnica semelhante para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="03957-241">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>
  
 <span data-ttu-id="03957-242">Essa estratégia de cache simples respeita o bom design de cache porque tem um limite de tamanho.</span><span class="sxs-lookup"><span data-stu-id="03957-242">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="03957-243">Porém, há mais código agora do que havia originalmente, o que significa mais custos com manutenção.</span><span class="sxs-lookup"><span data-stu-id="03957-243">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="03957-244">Você só deverá adotar a estratégia de cache se tiver encontrado um problema de desempenho e o PerfView tiver mostrado que as alocações de <xref:System.Text.StringBuilder> são um fator significativo.</span><span class="sxs-lookup"><span data-stu-id="03957-244">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="03957-245">LINQ e lambdas</span><span class="sxs-lookup"><span data-stu-id="03957-245">LINQ and lambdas</span></span>  
<span data-ttu-id="03957-246">A consulta integrada à linguagem (LINQ), em conjunto com expressões lambda, é um exemplo de um recurso de produtividade.</span><span class="sxs-lookup"><span data-stu-id="03957-246">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="03957-247">No entanto, seu uso pode ter um impacto significativo no desempenho ao longo do tempo e talvez você ache necessário reescrever seu código.</span><span class="sxs-lookup"><span data-stu-id="03957-247">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="03957-248">**Exemplo 5: lambdas, lista \<T> e IEnumerable\<T>**</span><span class="sxs-lookup"><span data-stu-id="03957-248">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="03957-249">Esse exemplo usa [o LINQ e um código de estilo funcional](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) para localizar um símbolo no modelo do compilador, considerando uma cadeia de caracteres de nome:</span><span class="sxs-lookup"><span data-stu-id="03957-249">This example uses [LINQ and functional style code](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 <span data-ttu-id="03957-250">O novo compilador e as experiências de IDE com base nele chamam `FindMatchingSymbol()` com muita frequência, além de haver diversas alocações ocultas nessa única linha de código da função.</span><span class="sxs-lookup"><span data-stu-id="03957-250">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="03957-251">Para examinar essas alocações, primeiro divida a única linha de código da função em duas linhas:</span><span class="sxs-lookup"><span data-stu-id="03957-251">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="03957-252">Na primeira linha, a [expressão lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [fecha](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) a variável local `name`.</span><span class="sxs-lookup"><span data-stu-id="03957-252">In the first line, the [lambda expression](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) the local variable `name`.</span></span> <span data-ttu-id="03957-253">Isso significa que, além de alocar um objeto para o [representante](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) que `predicate` mantém, o código aloca uma classe estática para manter o ambiente que captura o valor `name`.</span><span class="sxs-lookup"><span data-stu-id="03957-253">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="03957-254">O compilador gera um código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="03957-254">The compiler generates code like the following:</span></span>  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 <span data-ttu-id="03957-255">Agora, as duas alocações `new` (uma para a classe de ambiente e uma para o representante) estão explícitas.</span><span class="sxs-lookup"><span data-stu-id="03957-255">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>
  
 <span data-ttu-id="03957-256">Agora observe a chamada para `FirstOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="03957-256">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="03957-257">Esse método de extensão no tipo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> também acarreta uma alocação.</span><span class="sxs-lookup"><span data-stu-id="03957-257">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="03957-258">Como `FirstOrDefault` utiliza um objeto <xref:System.Collections.Generic.IEnumerable%601> como seu primeiro argumento, é possível expandir a chamada para o seguinte código (um pouco simplificado para discussão):</span><span class="sxs-lookup"><span data-stu-id="03957-258">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 <span data-ttu-id="03957-259">A variável `symbols` tem o tipo <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="03957-259">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="03957-260">O tipo de coleção <xref:System.Collections.Generic.List%601> implementa <xref:System.Collections.Generic.IEnumerable%601> e define de maneira inteligente um enumerador (interface <xref:System.Collections.Generic.IEnumerator%601>) que <xref:System.Collections.Generic.List%601> implementa com um `struct`.</span><span class="sxs-lookup"><span data-stu-id="03957-260">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="03957-261">O uso de uma estrutura em vez de uma classe significa que você normalmente evita alocações de heap, o que, por sua vez, pode afetar o desempenho da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="03957-261">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="03957-262">Os enumeradores costumam ser usados com o loop `foreach` da linguagem, que usa a estrutura do enumerador conforme ela retorna à pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="03957-262">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="03957-263">O incremento do ponteiro do heap de chamadas para abrir espaço a um objeto não afeta a GC, como faz uma alocação de heap.</span><span class="sxs-lookup"><span data-stu-id="03957-263">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>
  
 <span data-ttu-id="03957-264">No caso da chamada `FirstOrDefault` expandida, o código precisa chamar `GetEnumerator()` em um <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="03957-264">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="03957-265">A atribuição de `symbols` à variável `enumerable` do tipo `IEnumerable<Symbol>` perde as informações de que o objeto real é um <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="03957-265">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="03957-266">Isso significa que, quando o código busca o enumerador com `enumerable.GetEnumerator()`, o .NET Framework precisa realizar a conversão boxing da estrutura retornada para atribuí-la à variável `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="03957-266">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>
  
 <span data-ttu-id="03957-267">**Correção para o exemplo 5**</span><span class="sxs-lookup"><span data-stu-id="03957-267">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="03957-268">A correção é para gravar novamente `FindMatchingSymbol` da seguinte forma, substituindo sua linha de código única por seis linhas de código que continuam concisas, fáceis de ler, compreender e manter:</span><span class="sxs-lookup"><span data-stu-id="03957-268">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 <span data-ttu-id="03957-269">Esse código não usa métodos de extensão LINQ, lambdas ou enumeradores, e não acarreta alocações.</span><span class="sxs-lookup"><span data-stu-id="03957-269">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="03957-270">Não há alocações porque o compilador pode ver que a coleção `symbols` é um <xref:System.Collections.Generic.List%601> e pode associar o enumerador resultante (uma estrutura) a uma variável local com o tipo certo para evitar a conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="03957-270">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="03957-271">A versão original dessa função era um ótimo exemplo da potência expressiva do C# e da produtividade do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03957-271">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="03957-272">Essa versão nova e mais eficiente preserva essas qualidades sem adicionar nenhum código complexo de manutenção.</span><span class="sxs-lookup"><span data-stu-id="03957-272">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>
  
### <a name="async-method-caching"></a><span data-ttu-id="03957-273">Cache de método assíncrono</span><span class="sxs-lookup"><span data-stu-id="03957-273">Async method caching</span></span>  

<span data-ttu-id="03957-274">O próximo exemplo mostra um problema comum quando você tenta usar os resultados armazenados em cache em um método [async](../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="03957-274">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="03957-275">**Exemplo 6: cache em métodos assíncronos**</span><span class="sxs-lookup"><span data-stu-id="03957-275">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="03957-276">Os recursos de IDE do Visual Studio internos nos novos compiladores do C# e do Visual Basic normalmente buscam árvores de sintaxe, e os compiladores usam métodos assíncronos para isso, a fim de manter o Visual Studio ágil na resposta.</span><span class="sxs-lookup"><span data-stu-id="03957-276">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="03957-277">Aqui está a primeira versão do código que pode ser gravado para obter uma árvore de sintaxe:</span><span class="sxs-lookup"><span data-stu-id="03957-277">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="03957-278">É possível ver que a chamada de `GetSyntaxTreeAsync()` cria uma instância de `Parser`, analisa o código e retorna um objeto <xref:System.Threading.Tasks.Task>, `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="03957-278">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="03957-279">A parte adversa é alocar a instância de `Parser` e analisar o código.</span><span class="sxs-lookup"><span data-stu-id="03957-279">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="03957-280">A função retorna um <xref:System.Threading.Tasks.Task>, para que os chamadores possam aguardar o trabalho de análise e liberar o thread da interface do usuário para responder à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="03957-280">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>
  
 <span data-ttu-id="03957-281">Como diversos recursos do Visual Studio podem tentar obter a mesma árvore de sintaxe, convém gravar o código a seguir para armazenar em cache o resultado da análise a fim de economizar tempo e alocações.</span><span class="sxs-lookup"><span data-stu-id="03957-281">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="03957-282">Porém, esse código acarreta uma alocação:</span><span class="sxs-lookup"><span data-stu-id="03957-282">However, this code incurs an allocation:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 <span data-ttu-id="03957-283">Você vê que o novo código com cache tem um arquivo `SyntaxTree` chamado `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="03957-283">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="03957-284">Quando esse campo é nulo, `GetSyntaxTreeAsync()` faz o trabalho e salva o resultado no cache.</span><span class="sxs-lookup"><span data-stu-id="03957-284">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="03957-285">`GetSyntaxTreeAsync()` retorna o objeto `SyntaxTree`.</span><span class="sxs-lookup"><span data-stu-id="03957-285">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="03957-286">O problema é que quando você tem uma função `async` do tipo `Task<SyntaxTree>` e retorna um valor do tipo `SyntaxTree`, o compilador emite um código para alocar uma Tarefa e manter o resultado (usando `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="03957-286">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="03957-287">A Tarefa é marcada como concluída, e o resultado é disponibilizado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="03957-287">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="03957-288">No código dos novos compiladores, os objetos <xref:System.Threading.Tasks.Task> que já estavam concluídos ocorriam com tanta frequência que a correção dessas alocações melhorou claramente a capacidade de resposta.</span><span class="sxs-lookup"><span data-stu-id="03957-288">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>
  
 <span data-ttu-id="03957-289">**Correção para o exemplo 6**</span><span class="sxs-lookup"><span data-stu-id="03957-289">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="03957-290">Para remover a <xref:System.Threading.Tasks.Task> alocação concluída, você pode armazenar em cache o objeto de tarefa com o resultado concluído:</span><span class="sxs-lookup"><span data-stu-id="03957-290">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="03957-291">Esse código altera o tipo de `cachedResult` para `Task<SyntaxTree>` e emprega uma função auxiliar `async` que mantém o código original de `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="03957-291">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="03957-292">`GetSyntaxTreeAsync()` agora usa o [operador de união nula](../../csharp/language-reference/operators/null-coalescing-operator.md) para retornar `cachedResult`, caso ele não seja nulo.</span><span class="sxs-lookup"><span data-stu-id="03957-292">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="03957-293">Se `cachedResult` for nulo, `GetSyntaxTreeAsync()` chamará `GetSyntaxTreeUncachedAsync()` e armazenará o resultado em cache.</span><span class="sxs-lookup"><span data-stu-id="03957-293">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="03957-294">`GetSyntaxTreeAsync()` não aguarda a chamada para `GetSyntaxTreeUncachedAsync()` como o código faria normalmente.</span><span class="sxs-lookup"><span data-stu-id="03957-294">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="03957-295">Não usar a espera significa que, quando `GetSyntaxTreeUncachedAsync()` retorna seu objeto <xref:System.Threading.Tasks.Task>, `GetSyntaxTreeAsync()` retorna imediatamente o <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="03957-295">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="03957-296">Agora, o resultado armazenado em cache é um <xref:System.Threading.Tasks.Task>. Assim, não há alocações para retornar o resultado armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="03957-296">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>
  
### <a name="additional-considerations"></a><span data-ttu-id="03957-297">Considerações adicionais</span><span class="sxs-lookup"><span data-stu-id="03957-297">Additional considerations</span></span>  
 <span data-ttu-id="03957-298">Aqui estão mais alguns pontos sobre possíveis problemas em aplicativos grandes ou em aplicativos que processam muitos dados.</span><span class="sxs-lookup"><span data-stu-id="03957-298">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>
  
 <span data-ttu-id="03957-299">**OldValues**</span><span class="sxs-lookup"><span data-stu-id="03957-299">**Dictionaries**</span></span>  
  
 <span data-ttu-id="03957-300">Os dicionários são amplamente usados em muitos programas, e bons dicionários são muito práticos e naturalmente eficientes.</span><span class="sxs-lookup"><span data-stu-id="03957-300">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="03957-301">Porém, eles costumam ser usados incorretamente.</span><span class="sxs-lookup"><span data-stu-id="03957-301">However, they’re often used inappropriately.</span></span> <span data-ttu-id="03957-302">No Visual Studio e nos novos compiladores, a análise mostra que muitos dos dicionários apresentavam um único elemento ou estavam vazios.</span><span class="sxs-lookup"><span data-stu-id="03957-302">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="03957-303">Um <xref:System.Collections.Generic.Dictionary%602> vazio tem dez campos e ocupa 48 bytes no heap em um computador x86.</span><span class="sxs-lookup"><span data-stu-id="03957-303">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="03957-304">Os dicionários são ótimos quando você precisa de um mapeamento ou de uma estrutura de dados associativa com pesquisa constante.</span><span class="sxs-lookup"><span data-stu-id="03957-304">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="03957-305">No entanto, quando tem apenas alguns elementos, você perde muito espaço usando um dicionário.</span><span class="sxs-lookup"><span data-stu-id="03957-305">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="03957-306">Em vez disso, por exemplo, você pode analisar iterativamente um `List<KeyValuePair\<K,V>>` com a mesma rapidez.</span><span class="sxs-lookup"><span data-stu-id="03957-306">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="03957-307">Se você usa um dicionário apenas para carregá-lo com dados e, em seguida, lê-lo (um padrão muito comum), o uso de uma matriz classificada com uma pesquisa N(log(N)) pode ter praticamente a mesma velocidade, dependendo do número de elementos que você estiver usando.</span><span class="sxs-lookup"><span data-stu-id="03957-307">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>
  
 <span data-ttu-id="03957-308">**Classes vs. estruturas**</span><span class="sxs-lookup"><span data-stu-id="03957-308">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="03957-309">De certa forma, classes e estruturas oferecem uma contrapartida de espaço/tempo clássica para ajustar os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="03957-309">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="03957-310">As classes acarretam 12 bytes de sobrecarga em um computador x86, mesmo que não tenham campos, mas são fáceis de passar porque só utilizam um ponteiro para consultar uma instância de classe.</span><span class="sxs-lookup"><span data-stu-id="03957-310">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="03957-311">As estruturas não acarretam alocações de heap em caso de não conversão boxing, mas, quando você passa estruturas grandes como argumentos de função ou valores de retorno, elas utilizam tempo de CPU para copiar atomicamente todos os membros de dados das estruturas.</span><span class="sxs-lookup"><span data-stu-id="03957-311">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="03957-312">Cuidado com chamadas repetidas para propriedades que retornem estruturas, e armazene em cache o valor da propriedade em uma variável local para evitar a cópia excessiva de dados.</span><span class="sxs-lookup"><span data-stu-id="03957-312">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>
  
 <span data-ttu-id="03957-313">**Caches**</span><span class="sxs-lookup"><span data-stu-id="03957-313">**Caches**</span></span>  
  
 <span data-ttu-id="03957-314">Um truque de desempenho comum é armazenar resultados em cache.</span><span class="sxs-lookup"><span data-stu-id="03957-314">A common performance trick is to cache results.</span></span> <span data-ttu-id="03957-315">Porém, um cache sem um limite de tamanho ou uma política de alienação pode causar perda de memória.</span><span class="sxs-lookup"><span data-stu-id="03957-315">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="03957-316">Ao processar grandes volumes de dados, se mantiver muita memória em caches, você poderá fazer a coleta de lixo substituir os benefícios das pesquisas armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="03957-316">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>
  
 <span data-ttu-id="03957-317">Neste artigo, abordamos como você deve dar atenção a sintomas de gargalo de desempenho que possam afetar a capacidade de resposta do aplicativo, especialmente para sistemas grandes ou sistemas que processem um grande volume de dados.</span><span class="sxs-lookup"><span data-stu-id="03957-317">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="03957-318">Entre os responsáveis mais comuns estão conversão boxing, manipulações da cadeia de caracteres, LINQ e lambda, cache em métodos assíncronos, cache sem um limite de tamanho ou uma política de alienação, uso incorreto de dicionários e passagem de estruturas.</span><span class="sxs-lookup"><span data-stu-id="03957-318">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="03957-319">Lembre-se dos quatro fatos para ajustar os aplicativos:</span><span class="sxs-lookup"><span data-stu-id="03957-319">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="03957-320">Não otimize antes – seja produtivo e ajuste o aplicativo quando identificar problemas.</span><span class="sxs-lookup"><span data-stu-id="03957-320">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>
  
- <span data-ttu-id="03957-321">Os perfis não mentem – você está adivinhando se não está medindo.</span><span class="sxs-lookup"><span data-stu-id="03957-321">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>
  
- <span data-ttu-id="03957-322">As boas ferramentas fazem toda a diferença – baixe o PerfView e faça um teste.</span><span class="sxs-lookup"><span data-stu-id="03957-322">Good tools make all the difference – download PerfView and try it out.</span></span>
  
- <span data-ttu-id="03957-323">É tudo uma questão de alocação – é onde a equipe da plataforma do compilador passa boa parte do tempo melhorando o desempenho dos novos compiladores.</span><span class="sxs-lookup"><span data-stu-id="03957-323">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="03957-324">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03957-324">See also</span></span>

- [<span data-ttu-id="03957-325">Vídeo de apresentação deste tópico</span><span class="sxs-lookup"><span data-stu-id="03957-325">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="03957-326">Guia do iniciante à criação de perfil do desempenho</span><span class="sxs-lookup"><span data-stu-id="03957-326">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="03957-327">Desempenho</span><span class="sxs-lookup"><span data-stu-id="03957-327">Performance</span></span>](index.md)
- <span data-ttu-id="03957-328">[Dicas de desempenho do .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="03957-328">[.NET Performance Tips](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span></span>
- [<span data-ttu-id="03957-329">Tutoriais do PerfView no Channel 9</span><span class="sxs-lookup"><span data-stu-id="03957-329">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="03957-330">O SDK do .NET Compiler Platform</span><span class="sxs-lookup"><span data-stu-id="03957-330">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="03957-331">repositório dotnet/Roslyn no GitHub</span><span class="sxs-lookup"><span data-stu-id="03957-331">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
