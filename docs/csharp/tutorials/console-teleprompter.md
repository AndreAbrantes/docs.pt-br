---
title: Aplicativo do Console
description: Este tutorial ensina vários recursos no .NET Core e da linguagem C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: dbe64fe0a01ddab9e7a3ad0a9118b3fe59fba8aa
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656977"
---
# <a name="console-app"></a><span data-ttu-id="ecdec-103">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="ecdec-103">Console app</span></span>

<span data-ttu-id="ecdec-104">Este tutorial ensina vários recursos no .NET Core e da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="ecdec-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="ecdec-105">O que você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="ecdec-105">You'll learn:</span></span>

- <span data-ttu-id="ecdec-106">As noções básicas do CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ecdec-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="ecdec-107">A estrutura de um aplicativo de console C#</span><span class="sxs-lookup"><span data-stu-id="ecdec-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="ecdec-108">E/S do Console</span><span class="sxs-lookup"><span data-stu-id="ecdec-108">Console I/O</span></span>
- <span data-ttu-id="ecdec-109">Fundamentos das APIs de E/S de arquivo no .NET</span><span class="sxs-lookup"><span data-stu-id="ecdec-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="ecdec-110">Os fundamentos da programação assíncrona controlada por tarefas no .NET Core</span><span class="sxs-lookup"><span data-stu-id="ecdec-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="ecdec-111">Você criará um aplicativo que lê um arquivo de texto e ecoa o conteúdo desse arquivo de texto para o console.</span><span class="sxs-lookup"><span data-stu-id="ecdec-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="ecdec-112">A saída para o console é conduzida a fim de corresponder à leitura em voz alta.</span><span class="sxs-lookup"><span data-stu-id="ecdec-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="ecdec-113">Você pode acelerar ou reduzir o ritmo pressionando as chaves ' < ' (menor que) ou ' > ' (maior que).</span><span class="sxs-lookup"><span data-stu-id="ecdec-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="ecdec-114">Há vários recursos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="ecdec-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="ecdec-115">Vamos compilá-las uma a uma.</span><span class="sxs-lookup"><span data-stu-id="ecdec-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ecdec-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ecdec-116">Prerequisites</span></span>

- <span data-ttu-id="ecdec-117">Configure seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ecdec-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="ecdec-118">Você pode encontrar as instruções de instalação na página de [downloads do .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="ecdec-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="ecdec-119">Você pode executar esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="ecdec-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="ecdec-120">Instale seu editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="ecdec-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="ecdec-121">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ecdec-121">Create the app</span></span>

<span data-ttu-id="ecdec-122">A primeira etapa é criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecdec-122">The first step is to create a new application.</span></span> <span data-ttu-id="ecdec-123">Abra um prompt de comando e crie um novo diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecdec-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="ecdec-124">Torne ele o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ecdec-124">Make that the current directory.</span></span> <span data-ttu-id="ecdec-125">Digite o comando `dotnet new console` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ecdec-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="ecdec-126">Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="ecdec-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="ecdec-127">Antes de começar a fazer modificações, vamos percorrer as etapas para executar o aplicativo simples de Olá, Mundo.</span><span class="sxs-lookup"><span data-stu-id="ecdec-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="ecdec-128">Depois de criar o aplicativo, digite `dotnet restore` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ecdec-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="ecdec-129">Esse comando executa o processo de restauração do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ecdec-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="ecdec-130">O NuGet é um gerenciador de pacotes do .NET.</span><span class="sxs-lookup"><span data-stu-id="ecdec-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="ecdec-131">Esse comando baixa qualquer uma das dependências ausentes para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ecdec-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="ecdec-132">Como esse é um novo projeto, nenhuma das dependências foram aplicadas, portanto, a primeira execução baixará a estrutura do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ecdec-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="ecdec-133">Após essa etapa inicial, você só precisará executar o `dotnet restore` ao adicionar novos pacotes dependentes, ou atualizar as versões de qualquer uma de suas dependências.</span><span class="sxs-lookup"><span data-stu-id="ecdec-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="ecdec-134">Depois de restaurar os pacotes, execute `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="ecdec-135">Isso executa o mecanismo de compilação e cria o executável de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecdec-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="ecdec-136">Por fim, execute `dotnet run` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecdec-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="ecdec-137">O código simples do aplicativo Hello World está totalmente em Program.cs.</span><span class="sxs-lookup"><span data-stu-id="ecdec-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="ecdec-138">Abra esse arquivo com o seu editor de texto favorito.</span><span class="sxs-lookup"><span data-stu-id="ecdec-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="ecdec-139">Estamos prestes a fazer nossas primeiras alterações.</span><span class="sxs-lookup"><span data-stu-id="ecdec-139">We're about to make our first changes.</span></span> <span data-ttu-id="ecdec-140">Na parte superior do arquivo, confira uma instrução using:</span><span class="sxs-lookup"><span data-stu-id="ecdec-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="ecdec-141">Essa instrução informa ao compilador que quaisquer tipos do namespace `System` estão dentro do escopo.</span><span class="sxs-lookup"><span data-stu-id="ecdec-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="ecdec-142">Assim como em outras linguagens orientadas a objeto que você pode ter usado, o C# usa namespaces para organizar tipos.</span><span class="sxs-lookup"><span data-stu-id="ecdec-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="ecdec-143">Este programa Olá, Mundo não é diferente.</span><span class="sxs-lookup"><span data-stu-id="ecdec-143">This Hello World program is no different.</span></span> <span data-ttu-id="ecdec-144">Você pode ver que o programa é encerrado no namespace com o nome baseado no nome do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ecdec-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="ecdec-145">Para este tutorial, vamos alterar o nome do namespace para `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="ecdec-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="ecdec-146">Como ler e exibir o arquivo</span><span class="sxs-lookup"><span data-stu-id="ecdec-146">Reading and Echoing the File</span></span>

<span data-ttu-id="ecdec-147">O primeiro recurso a ser adicionado é a capacidade de ler um arquivo de texto e a exibição de todo esse texto para um console.</span><span class="sxs-lookup"><span data-stu-id="ecdec-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="ecdec-148">Primeiro, vamos adicionar um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="ecdec-148">First, let's add a text file.</span></span> <span data-ttu-id="ecdec-149">Copie o arquivo [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) do repositório do GitHub para este [exemplo](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) no diretório de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ecdec-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="ecdec-150">Isso servirá como o script de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecdec-150">This will serve as the script for your application.</span></span> <span data-ttu-id="ecdec-151">Se desejar obter informações sobre como baixar o aplicativo de exemplo para este tópico, consulte as instruções no tópico [Exemplos e Tutoriais](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="ecdec-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples) topic.</span></span>

<span data-ttu-id="ecdec-152">Em seguida, adicione o seguinte método em sua classe `Program` (logo abaixo do método `Main`):</span><span class="sxs-lookup"><span data-stu-id="ecdec-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="ecdec-153">Esse método usa tipos de dois namespaces novos.</span><span class="sxs-lookup"><span data-stu-id="ecdec-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="ecdec-154">Para que isso seja compilado, você precisará adicionar as duas linhas a seguir à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="ecdec-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="ecdec-155">A interface <xref:System.Collections.Generic.IEnumerable%601> é definida no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="ecdec-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="ecdec-156">A classe <xref:System.IO.File> é definida no namespace <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="ecdec-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="ecdec-157">Esse método é um tipo especial de método C# chamado de *Método iterador*.</span><span class="sxs-lookup"><span data-stu-id="ecdec-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="ecdec-158">Os métodos enumeradores retornam sequências que são avaliadas lentamente.</span><span class="sxs-lookup"><span data-stu-id="ecdec-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="ecdec-159">Isso significa que cada item na sequência é gerado conforme a solicitação do código que está consumindo a sequência.</span><span class="sxs-lookup"><span data-stu-id="ecdec-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="ecdec-160">Os métodos enumeradores são métodos que contêm uma ou mais [`yield return`](../language-reference/keywords/yield.md) instruções.</span><span class="sxs-lookup"><span data-stu-id="ecdec-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="ecdec-161">O objeto retornado pelo método `ReadFrom` contém o código para gerar cada item na sequência.</span><span class="sxs-lookup"><span data-stu-id="ecdec-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="ecdec-162">Neste exemplo, isso envolve a leitura da próxima linha de texto do arquivo de origem e o retorno dessa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ecdec-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="ecdec-163">Toda vez que o código de chamada solicita o próximo item da sequência, o código lê a próxima linha de texto do arquivo e a retorna.</span><span class="sxs-lookup"><span data-stu-id="ecdec-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="ecdec-164">Após a leitura completa do arquivo, a sequência indicará que não há mais itens.</span><span class="sxs-lookup"><span data-stu-id="ecdec-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="ecdec-165">Há dois outros elementos da sintaxe em C# que podem ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="ecdec-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="ecdec-166">A [`using`](../language-reference/keywords/using-statement.md) instrução neste método gerencia a limpeza de recursos.</span><span class="sxs-lookup"><span data-stu-id="ecdec-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="ecdec-167">A variável inicializada na instrução `using` (`reader`, neste exemplo) deve implementar a interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="ecdec-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="ecdec-168">Essa interface define um único método, `Dispose`, que deve ser chamado quando o recurso for liberado.</span><span class="sxs-lookup"><span data-stu-id="ecdec-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="ecdec-169">O compilador gera essa chamada quando a execução atingir a chave de fechamento da instrução `using`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="ecdec-170">O código gerado pelo compilador garante que o recurso seja liberado, mesmo se uma exceção for lançada do código no bloco definido pela instrução using.</span><span class="sxs-lookup"><span data-stu-id="ecdec-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="ecdec-171">A variável `reader` é definida usando a palavra-chave `var`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="ecdec-172">[`var`](../language-reference/keywords/var.md) define uma *variável local digitada implicitamente*.</span><span class="sxs-lookup"><span data-stu-id="ecdec-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="ecdec-173">Isso significa que o tipo da variável é determinado pelo tipo de tempo de compilação do objeto atribuído à variável.</span><span class="sxs-lookup"><span data-stu-id="ecdec-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="ecdec-174">Aqui, esse é o valor retornado do método <xref:System.IO.File.OpenText(System.String)>, que é um objeto <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="ecdec-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="ecdec-175">Agora, vamos preencher o código para ler o arquivo no `Main` método:</span><span class="sxs-lookup"><span data-stu-id="ecdec-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="ecdec-176">Execute o programa (usando `dotnet run`, e você poderá ver todas as linhas impressa no console).</span><span class="sxs-lookup"><span data-stu-id="ecdec-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="ecdec-177">Adicionar atrasos e formatar a saída</span><span class="sxs-lookup"><span data-stu-id="ecdec-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="ecdec-178">O que você possui está sendo exibido muito rápido para permitir a leitura em voz alta.</span><span class="sxs-lookup"><span data-stu-id="ecdec-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="ecdec-179">Agora você precisa adicionar os atrasos na saída.</span><span class="sxs-lookup"><span data-stu-id="ecdec-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="ecdec-180">Ao começar, você criará um pouco do código principal que permite o processamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="ecdec-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="ecdec-181">No entanto, essas primeiras etapas seguirão alguns antipadrões.</span><span class="sxs-lookup"><span data-stu-id="ecdec-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="ecdec-182">Os antipadrões são indicados nos comentários durante a adição do código, e o código será atualizado em etapas posteriores.</span><span class="sxs-lookup"><span data-stu-id="ecdec-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="ecdec-183">Há duas etapas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="ecdec-183">There are two steps to this section.</span></span> <span data-ttu-id="ecdec-184">Primeiro, você atualizará o método iterador para retornar palavras únicas em vez de linhas inteiras.</span><span class="sxs-lookup"><span data-stu-id="ecdec-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="ecdec-185">Isso é feito com essas modificações.</span><span class="sxs-lookup"><span data-stu-id="ecdec-185">That's done with these modifications.</span></span> <span data-ttu-id="ecdec-186">Substitua a instrução `yield return line;` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ecdec-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="ecdec-187">Em seguida, será necessário modificar a forma como você consume as linhas do arquivo, e adicionar um atraso depois de escrever cada palavra.</span><span class="sxs-lookup"><span data-stu-id="ecdec-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="ecdec-188">Substitua a instrução `Console.WriteLine(line)` no método `Main` pelo seguinte bloco:</span><span class="sxs-lookup"><span data-stu-id="ecdec-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="ecdec-189">A classe <xref:System.Threading.Tasks.Task> é o namespace <xref:System.Threading.Tasks>, portanto, você precisa adicionar essa instrução `using` na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="ecdec-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="ecdec-190">Execute o exemplo e verifique a saída.</span><span class="sxs-lookup"><span data-stu-id="ecdec-190">Run the sample, and check the output.</span></span> <span data-ttu-id="ecdec-191">Agora, cada palavra única é impressa, seguida por um atraso de 200 ms.</span><span class="sxs-lookup"><span data-stu-id="ecdec-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="ecdec-192">No entanto, a saída exibida mostra alguns problemas, pois o arquivo de texto de origem contém várias linhas com mais de 80 caracteres sem uma quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="ecdec-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="ecdec-193">Isso pode ser difícil de ler durante a rolagem da tela.</span><span class="sxs-lookup"><span data-stu-id="ecdec-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="ecdec-194">Isso é fácil de corrigir.</span><span class="sxs-lookup"><span data-stu-id="ecdec-194">That's easy to fix.</span></span> <span data-ttu-id="ecdec-195">Você só controlará o tamanho de cada linha e gerará uma nova linha sempre que o comprimento da linha atingir um determinado limite.</span><span class="sxs-lookup"><span data-stu-id="ecdec-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="ecdec-196">Declare uma variável local após a declaração de `words` no método `ReadFrom` que contém o comprimento da linha:</span><span class="sxs-lookup"><span data-stu-id="ecdec-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="ecdec-197">Em seguida, adicione o seguinte código após a instrução `yield return word + " ";` (antes da chave de fechamento):</span><span class="sxs-lookup"><span data-stu-id="ecdec-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="ecdec-198">Execute o exemplo e você poderá ler em voz alta em seu ritmo pré-configurado.</span><span class="sxs-lookup"><span data-stu-id="ecdec-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="ecdec-199">Tarefas assíncronas</span><span class="sxs-lookup"><span data-stu-id="ecdec-199">Async Tasks</span></span>

<span data-ttu-id="ecdec-200">Nesta etapa final, você adicionará o código para gravar a saída de forma assíncrona em uma tarefa, enquanto também executa outra tarefa para ler a entrada do usuário se quiser acelerar ou diminuir a exibição do texto, ou parar completamente a exibição do texto.</span><span class="sxs-lookup"><span data-stu-id="ecdec-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="ecdec-201">Isso tem algumas etapas e, no final, você terá todas as atualizações necessárias.</span><span class="sxs-lookup"><span data-stu-id="ecdec-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="ecdec-202">A primeira etapa é criar um método de <xref:System.Threading.Tasks.Task> retorno assíncrono que represente o código que você criou até agora para ler e exibir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="ecdec-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="ecdec-203">Adicione este método à sua `Program` classe (é tirado do corpo do seu `Main` método):</span><span class="sxs-lookup"><span data-stu-id="ecdec-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="ecdec-204">Você observará duas alterações.</span><span class="sxs-lookup"><span data-stu-id="ecdec-204">You'll notice two changes.</span></span> <span data-ttu-id="ecdec-205">Primeiro, no corpo do método, em vez de chamar <xref:System.Threading.Tasks.Task.Wait> para aguardar de forma síncrona a conclusão de uma tarefa, essa versão usa a palavra-chave `await`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="ecdec-206">Para fazer isso, você precisa adicionar o modificador `async` à assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="ecdec-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="ecdec-207">Esse método retorna `Task`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-207">This method returns a `Task`.</span></span> <span data-ttu-id="ecdec-208">Observe que não há instruções return que retornam um objeto `Task`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="ecdec-209">Em vez disso, esse objeto `Task` é criado pelo código gerado pelo compilador quando você usa o operador `await`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="ecdec-210">Você pode imaginar que esse método retorna quando atinge um `await`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="ecdec-211">A `Task` retornada indica que o trabalho não foi concluído.</span><span class="sxs-lookup"><span data-stu-id="ecdec-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="ecdec-212">O método será retomado quando a tarefa em espera for concluída.</span><span class="sxs-lookup"><span data-stu-id="ecdec-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="ecdec-213">Após a execução completa, a `Task` retornada indicará a conclusão.</span><span class="sxs-lookup"><span data-stu-id="ecdec-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="ecdec-214">O código de chamada pode monitorar essa `Task` retornada para determinar quando ela foi concluída.</span><span class="sxs-lookup"><span data-stu-id="ecdec-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="ecdec-215">Chame esse novo método em seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="ecdec-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="ecdec-216">Aqui, em `Main`, o código aguarda de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="ecdec-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="ecdec-217">Use o operador `await` em vez de esperar de forma síncrona sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="ecdec-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="ecdec-218">Mas, em um método de aplicativo de console `Main` , você não pode usar o `await` operador.</span><span class="sxs-lookup"><span data-stu-id="ecdec-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="ecdec-219">Isso resultaria no encerramento do aplicativo antes da conclusão de todas as tarefas.</span><span class="sxs-lookup"><span data-stu-id="ecdec-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="ecdec-220">Caso use o C# 7.1 ou posterior, você poderá criar aplicativos de console com o método [`async` `Main`](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="ecdec-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="ecdec-221">Em seguida, você precisa escrever o segundo método assíncrono para ler no console e observar as chaves ' < ' (menor que), ' > ' (maior que) e ' X ' ou ' x '.</span><span class="sxs-lookup"><span data-stu-id="ecdec-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="ecdec-222">Este é o método que você adiciona para essa tarefa:</span><span class="sxs-lookup"><span data-stu-id="ecdec-222">Here's the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="ecdec-223">Isso cria uma expressão lambda para representar um <xref:System.Action> delegado que lê uma chave do console e modifica uma variável local que representa o atraso quando o usuário pressiona as chaves ' < ' (menor que) ou ' > ' (maior que).</span><span class="sxs-lookup"><span data-stu-id="ecdec-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="ecdec-224">O método delegate é concluído quando o usuário pressiona as teclas ' X ' ou ' x ', o que permite ao usuário parar a exibição do texto a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="ecdec-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="ecdec-225">Esse método usa <xref:System.Console.ReadKey> para bloquear e aguardar até que o usuário pressione uma tecla.</span><span class="sxs-lookup"><span data-stu-id="ecdec-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="ecdec-226">Para concluir esse recurso, você precisa criar um novo método de retorno `async Task` que inicia essas duas tarefas (`GetInput` e `ShowTeleprompter`) e também gerencia os dados compartilhados entre essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="ecdec-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="ecdec-227">É hora de criar uma classe que possa manipular os dados compartilhados entre essas duas tarefas.</span><span class="sxs-lookup"><span data-stu-id="ecdec-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="ecdec-228">Essa classe contém duas propriedades públicas: o atraso e um sinalizador `Done` para indicar que o arquivo foi lido completamente:</span><span class="sxs-lookup"><span data-stu-id="ecdec-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="ecdec-229">Coloque essa classe em um novo arquivo e cerque-a pelo namespace `TeleprompterConsole`, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="ecdec-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="ecdec-230">Você também precisará adicionar uma `using static` instrução para que possa referenciar os `Min` métodos e `Max` sem os nomes de classe ou namespace de circunscrição.</span><span class="sxs-lookup"><span data-stu-id="ecdec-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="ecdec-231">Uma [`using static`](../language-reference/keywords/using-static.md) instrução importa os métodos de uma classe.</span><span class="sxs-lookup"><span data-stu-id="ecdec-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="ecdec-232">Isso é o oposto das instruções `using` usadas até este ponto, as quais importaram todas as classes de um namespace.</span><span class="sxs-lookup"><span data-stu-id="ecdec-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="ecdec-233">Em seguida, atualize os métodos `ShowTeleprompter` e `GetInput` para usar o novo objeto `config`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="ecdec-234">Escreva um método final `async` de retorno de `Task` para iniciar as duas tarefas e sair quando a primeira tarefa for concluída:</span><span class="sxs-lookup"><span data-stu-id="ecdec-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="ecdec-235">O novo método aqui é a chamada <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])>.</span><span class="sxs-lookup"><span data-stu-id="ecdec-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="ecdec-236">Isso cria uma `Task` que termina assim que qualquer uma das tarefas na lista de argumentos for concluída.</span><span class="sxs-lookup"><span data-stu-id="ecdec-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="ecdec-237">Depois, atualize os métodos `ShowTeleprompter` e `GetInput` para usar o objeto `config` para o atraso:</span><span class="sxs-lookup"><span data-stu-id="ecdec-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="ecdec-238">Essa nova versão de `ShowTeleprompter` chama um novo método na classe `TeleprompterConfig`.</span><span class="sxs-lookup"><span data-stu-id="ecdec-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="ecdec-239">Agora, você precisa atualizar `Main` para chamar `RunTeleprompter` em vez de `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="ecdec-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="ecdec-240">Conclusão</span><span class="sxs-lookup"><span data-stu-id="ecdec-240">Conclusion</span></span>

<span data-ttu-id="ecdec-241">Este tutorial mostrou a você alguns recursos da linguagem C# e as bibliotecas .NET Core relacionadas ao trabalho em aplicativos de Console.</span><span class="sxs-lookup"><span data-stu-id="ecdec-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="ecdec-242">Use esse conhecimento como base para explorar mais sobre a linguagem e sobre as classes apresentadas aqui.</span><span class="sxs-lookup"><span data-stu-id="ecdec-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="ecdec-243">Você viu as noções básicas de e/s de arquivo e console, bloqueio e uso sem bloqueio da programação assíncrona baseada em tarefas, um tour pela linguagem C# e como os programas C# são organizados e o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ecdec-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="ecdec-244">Para obter mais informações sobre E/S de arquivo, consulte o tópico [E/S de arquivo e de fluxo](../../standard/io/index.md).</span><span class="sxs-lookup"><span data-stu-id="ecdec-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="ecdec-245">Para obter mais informações sobre o modelo de programação assíncrona usado neste tutorial, consulte os tópicos [Programação assíncrona controlada por tarefas](../../standard/parallel-programming/task-based-asynchronous-programming.md) e [Programação assíncrona](../async.md).</span><span class="sxs-lookup"><span data-stu-id="ecdec-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../../standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
