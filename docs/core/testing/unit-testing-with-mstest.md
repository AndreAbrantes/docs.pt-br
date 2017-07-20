---
title: Teste de unidade com o MSTest e o .NET Core | Microsoft Docs
description: Como usar o MSTest com o .NET Core
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 5c6382ee0de3cba950b4585b05f10b4682f9a797
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---

# <a name="unit-testing-with-mstest-and-net-core"></a>Teste de unidade com o MSTest e .NET Core

Este tutorial apresenta uma experiência interativa de compilação de uma solução de exemplo passo a passo para aprender os conceitos do teste de unidade. Se você preferir acompanhar o tutorial usando uma solução interna, [veja ou baixe o exemplo de código](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) antes de começar. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="creating-the-source-project"></a>Criando o projeto de origem

Abra uma janela do shell. Crie um diretório chamado *unit-testing-using-dotnet-test* para armazenar a solução. Dentro desse novo diretório, crie um diretório *PrimeService*. A estrutura do diretório até o momento é mostrada abaixo:

```
/unit-testing-using-mstest
    /PrimeService
```

Torne *PrimeService* o diretório atual e execute [`dotnet new classlib`](../tools/dotnet-new.md) para criar o projeto de origem. Renomeie *Class1.cs* como *PrimeService.cs*. Para usar TDD (Desenvolvimento Orientado por Testes), você criará uma implementação com falha da classe `PrimeService`:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate) 
        {
            throw new NotImplementedException("Please create a test first");
        } 
    }
}
```

### <a name="creating-the-test-project"></a>Criando o projeto de teste

Altere o diretório de volta para o diretório *unit-testing-using-mstest* e crie o diretório *PrimeService.Tests*. A estrutura do diretório é mostrada abaixo:

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Torne o diretório *PrimeService.Tests* o diretório atual e crie um novo projeto usando [`dotnet new mstest`](../tools/dotnet-new.md). Isso cria um projeto de teste que usa o MSTest como a biblioteca de teste. O modelo gerado configura o executor de teste no arquivo *PrimeServiceTests.csproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.11" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11" />
</ItemGroup>
```

O projeto de teste requer outros pacotes para criar e executar testes de unidade. `dotnet new` da etapa anterior adicionou o SDK do MSTest, a estrutura de teste do MSTest e o executor do MSTest. Agora, adicione a biblioteca de classes `PrimeService` como outra dependência ao projeto. Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Outra opção é editar o arquivo *PrimeService.Tests.csproj*. Diretamente sob o primeiro nó `<ItemGroup>`, adicione outro nó `<ItemGroup>` com uma referência ao projeto de biblioteca:

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

Você pode ver o arquivo inteiro no [repositório de exemplos](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) no GitHub.

O layout da solução final é mostrada abaixo:

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a>Criando o primeiro teste

Antes de compilar a biblioteca ou os testes, execute [`dotnet restore`](../tools/dotnet-restore.md) no diretório *PrimeService.Tests*. Este comando restaura todos os pacotes NuGet necessários para cada projeto.

A abordagem de TDD pede a criação de um teste com falha para fazê-lo passar e depois a repetição do processo. Remova *UnitTest1.cs* do diretório *PrimeService.Tests* e crie um novo arquivo C# chamado *PrimeService_IsPrimeShould.cs* com o seguinte conteúdo:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, $"1 should not be prime");
        }
    }
}
```

O atributo `[TestClass]` indica uma classe que contém testes de unidade. O atributo `[TestMethod]` indica um método como um único teste. 

Salve esse arquivo e execute [`dotnet test`](../tools/dotnet-test.md) para compilar os testes e a biblioteca de classes e, em seguida, execute os testes. O executor de teste do MSTest contém o ponto de entrada do programa para executar os testes. `dotnet test` inicia o executor de teste e fornece um argumento de linha de comando para o executor de teste, indicando o assembly que contém os testes.

O teste falha. Você ainda não criou a implementação. Escreva o código mais simples na classe `PrimeService` para fazer esse teste ser aprovado:

```csharp
public bool IsPrime(int candidate) 
{
    if (candidate == 1) 
    { 
        return false;
    } 
    throw new NotImplementedException("Please create a test first");
} 
```

No diretório *PrimeService.Tests*, execute `dotnet test` novamente. O comando `dotnet test` executa uma compilação para o projeto `PrimeService` e, depois, para o projeto `PrimeService.Tests`. Depois de compilar os dois projetos, ele executará esse teste único. Ele é aprovado.

## <a name="adding-more-features"></a>Adicionando mais recursos

Agora que você fez um teste ser aprovado, é hora de escrever mais. Existem alguns outros casos simples de números primos: 0, -1. Você pode adicioná-los como novos testes, com o atributo `[TestMethod]`, porém isso se torna entediante rapidamente. Há outros atributos do MSTest que permitem escrever um pacote de testes semelhantes.  Um atributo `[DataTestMethod]` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada. Você pode usar o atributo `[DataRow]` para especificar valores para essas entradas. 
 
Em vez de criar novos testes, aproveite esses dois atributos para criar um único método de teste de dados que testa diversos valores inferiores a dois, que é o menor número primo:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Execute `dotnet test`, e dois desses testes falham. Para fazer todos os testes serem aprovados, altere a cláusula `if` no início do método:

```csharp
if (candidate < 2)
```

Continue iterando adicionando mais testes, mais teorias e mais código na biblioteca principal. Você acabará com a [versão concluída dos testes](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).

Você criou uma pequena biblioteca e um conjunto de testes de unidade para essa biblioteca. Você estruturou a solução para que a adição de novos pacotes e testes seja tranquila, e você possa concentrar mais tempo e esforço na resolução dos objetivos do aplicativo.

