---
title: Teste de unidade do F# no .NET Core com dotnet test e xUnit
description: Aprenda os conceitos de teste de unidade para F# no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 5fe4a8faddd87334439513368f24d808abc58e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157304"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="6ec1a-103">Bibliotecas do F# de teste de unidade no .NET Core usando dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="6ec1a-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="6ec1a-104">Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="6ec1a-105">Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="6ec1a-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="6ec1a-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="6ec1a-107">Criando o projeto de origem</span><span class="sxs-lookup"><span data-stu-id="6ec1a-107">Creating the source project</span></span>

<span data-ttu-id="6ec1a-108">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-108">Open a shell window.</span></span> <span data-ttu-id="6ec1a-109">Crie um diretório chamado *unit-testing-with-fsharp* para armazenar a solução.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="6ec1a-110">Nesse novo diretório, execute `dotnet new sln` para criar uma nova solução.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="6ec1a-111">Isso facilita o gerenciamento da biblioteca de classes e o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="6ec1a-112">No diretório da solução, crie um diretório *MathService*.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="6ec1a-113">A estrutura de arquivo e diretório até aqui é mostrada abaixo:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="6ec1a-114">Faça *do MathService* o diretório `dotnet new classlib -lang "F#"` atual e execute para criar o projeto de origem.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-114">Make *MathService* the current directory, and run `dotnet new classlib -lang "F#"` to create the source project.</span></span> <span data-ttu-id="6ec1a-115">Você criará uma implementação com falha do serviço de matemática:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="6ec1a-116">Altere o diretório de volta para o diretório *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="6ec1a-117">Execute `dotnet sln add .\MathService\MathService.fsproj` para adicionar o projeto de biblioteca de classes à solução.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="6ec1a-118">Criando o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="6ec1a-118">Creating the test project</span></span>

<span data-ttu-id="6ec1a-119">Em seguida, crie o diretório *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="6ec1a-120">O seguinte esquema mostra a estrutura do diretório:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="6ec1a-121">Torne o diretório *MathService.Tests* o diretório atual e crie um novo projeto usando `dotnet new xunit -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new xunit -lang "F#"`.</span></span> <span data-ttu-id="6ec1a-122">Isso cria um projeto de teste que usa o xUnit como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="6ec1a-123">O modelo gerado configura o executor de teste no *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="6ec1a-124">O projeto de teste requer outros pacotes para criar e executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="6ec1a-125">`dotnet new` na etapa anterior adicionou xUnit e o executor de xUnit.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="6ec1a-126">Agora, adicione a biblioteca de classes `MathService` como outra dependência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="6ec1a-127">Use `dotnet add reference` o comando:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="6ec1a-128">Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="6ec1a-129">Você tem o seguinte layout de solução final:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-129">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="6ec1a-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` no diretório *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="6ec1a-131">Criando o primeiro teste</span><span class="sxs-lookup"><span data-stu-id="6ec1a-131">Creating the first test</span></span>

<span data-ttu-id="6ec1a-132">Escreva um teste com falha, faça-o ser aprovado e, em seguida, repita o processo.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="6ec1a-133">Abra *Tests.fs* e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="6ec1a-134">O atributo `[<Fact>]` indica um método de teste que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="6ec1a-135">Em *unit-testing-with-fsharp*, execute `dotnet test` para criar os testes e a biblioteca de classes e execute os testes.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-135">From the *unit-testing-with-fsharp*, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="6ec1a-136">O executor de teste do xUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="6ec1a-137">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade que você criou.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="6ec1a-138">Esses dois testes mostram testes com aprovação e falha mais básicos.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="6ec1a-139">`My test` é aprovado e `Fail every time` falha.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="6ec1a-140">Agora, crie um teste para o método `squaresOfOdds`.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="6ec1a-141">O método `squaresOfOdds` retorna uma sequência dos quadrados de todos os valores inteiros ímpares que fazem parte da sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="6ec1a-142">Em vez de tentar gravar todas as funções de uma vez, você pode criar testes iterativamente que validam a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="6ec1a-143">Fazer com que cada teste passe significa criar a funcionalidade necessária para o método.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="6ec1a-144">O teste mais simples que podemos escrever é chamar `squaresOfOdds` com todos os números pares, em que o resultado deve ser uma sequência vazia de inteiros.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="6ec1a-145">Este é o teste:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="6ec1a-146">O teste falha.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-146">Your test fails.</span></span> <span data-ttu-id="6ec1a-147">Você ainda não criou a implementação.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="6ec1a-148">Faça esse teste ser aprovado escrevendo o código mais simples na classe `MathService` que funciona:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="6ec1a-149">No diretório *unit-testing-with-fsharp*, execute `dotnet test` novamente.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="6ec1a-150">O comando `dotnet test` executa uma compilação para o projeto `MathService` e, depois, para o projeto `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="6ec1a-151">Depois de compilar os dois projetos, ele executará esse teste único.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="6ec1a-152">Ele é aprovado.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="6ec1a-153">Como atender aos requisitos</span><span class="sxs-lookup"><span data-stu-id="6ec1a-153">Completing the requirements</span></span>

<span data-ttu-id="6ec1a-154">Agora que você fez um teste ser aprovado, é hora de escrever mais.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="6ec1a-155">O próximo caso simples funciona com uma sequência cujo único número ímpar é `1`.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="6ec1a-156">O número 1 é mais fácil, pois o quadrado de 1 é 1.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="6ec1a-157">Este é o próximo teste:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="6ec1a-158">A execução de `dotnet test` executa os testes e mostra que o novo teste falha.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="6ec1a-159">Agora, atualize o método `squaresOfOdds` para lidar com esse novo teste.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="6ec1a-160">Remova todos os números pares da sequência para que esse teste seja aprovado.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="6ec1a-161">Faça isso escrevendo uma pequena função de filtro e usando `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="6ec1a-162">Há mais uma etapa a ser executada: eleve ao quadrado cada um dos números ímpares.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="6ec1a-163">Comece escrevendo um novo teste:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="6ec1a-164">Você pode corrigir o teste redirecionando a sequência filtrada por meio de uma operação de mapa para calcular o quadrado de cada número ímpar:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="6ec1a-165">Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="6ec1a-166">Você estruturou a solução para que a adição de novos pacotes e testes fizesse parte do fluxo de trabalho normal.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="6ec1a-167">Você concentrou grande parte do seu tempo e esforço em resolver as metas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ec1a-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="6ec1a-168">See also</span></span>

- [<span data-ttu-id="6ec1a-169">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6ec1a-169">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="6ec1a-170">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="6ec1a-170">dotnet sln</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="6ec1a-171">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="6ec1a-171">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="6ec1a-172">teste dotnet</span><span class="sxs-lookup"><span data-stu-id="6ec1a-172">dotnet test</span></span>](../tools/dotnet-test.md)
