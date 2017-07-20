---
title: "Introdução ao .NET Core usando a CLI | Microsoft Docs"
description: "Um tutorial passo a passo que mostra como começar a usar o .NET Core no Windows, Linux ou macOS com a CLI (interface de linha de comando) do .NET Core."
keywords: .NET Core, CLI
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 41632e63-d5c6-4427-a09e-51dc1116d45f
ms.translationtype: Human Translation
ms.sourcegitcommit: deb760878391856cf07bab04563d0ec19a1511e7
ms.openlocfilehash: b1ff9218932d5ef49941ca427d9ee38503a9c103
ms.contentlocale: pt-br
ms.lasthandoff: 04/30/2017

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Introdução ao .NET Core no Windows/Linux/macOS usando a linha de comando

Este tópico mostra como começar a desenvolver aplicativos de plataforma cruzada no computador usando as ferramentas da CLI do .NET Core.

Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).

## <a name="prerequisites"></a>Pré-requisitos

- [SDK 1.0 do .NET Core](https://www.microsoft.com/net/download/core).
- Um editor de texto ou de código de sua escolha.

## <a name="hello-console-app"></a>Olá, Aplicativo de Console.

Você pode [exibir ou baixar o código de exemplo](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild) do repositório dotnet/docs do GitHub. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Abra um prompt de comando e crie uma pasta chamada *Hello*. Navegue até a pasta que você criou e digite o seguinte:

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

Vejamos um breve passo a passo:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) cria um arquivo de projeto `Hello.csproj` atualizado com as dependências necessárias para criar um aplicativo de console.  Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.
   
   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.

   * A marca `OutputType` especifica que estamos copilando um executável, em outras palavras, um aplicativo de console.
   * A marca `TargetFramework` especifica o tempo de execução do .NET que estamos direcionando. Em um cenário avançado, você pode especificar várias estruturas de destino e compilar todos eles em uma única operação. Neste tutorial, veremos apenas a compilação para .NET Core 1.0.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   O programa é iniciado pelo `using System`, que significa "colocar tudo no namespace `System` no escopo para este arquivo". O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.

   Em seguida, definimos um namespace chamado `Hello`. Você pode alterar isso de acordo com a sua vontade. Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento. Essa matriz contém a lista de argumentos passados quando o programa compilado é chamado. Assim, essa matriz não será usada: o que o programa faz é gravar: "Hello World!" no console. Posteriormente, faremos alterações no código que usará esse argumento.

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) chama o [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET) para restaurar a árvore de dependências. O NuGet analisa o arquivo *Hello.csproj*, baixa as dependências declaradas no arquivo (ou captura-as de um cache no computador) e grava o arquivo *obj/project.assets.json*.  O arquivo *project.assets.json* é necessário para compilar e executar.
   
   O arquivo *project.assets.json* é um conjunto completo e persistente do gráfico de dependências do NuGet e de outras informações que descrevem um aplicativo.  Esse arquivo é lido por outras ferramentas, como [`dotnet build`](../tools/dotnet-build.md) e [`dotnet run`](../tools/dotnet-run.md), permitindo que elas processem o código-fonte com um conjunto correto das dependências do NuGet e das resoluções de associação.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) chama [`dotnet build`](../tools/dotnet-build.md) para garantir que os destinos de build foram criados e então chama `dotnet <assembly.dll>` para executar o aplicativo de destino.
   
    ```
    $ dotnet run
    Hello World!
    ```

    Como alternativa, também é possível pode executar [`dotnet build`](../tools/dotnet-build.md) para compilar o código sem executar os aplicativos de console de compilação. Isso resulta em um aplicativo compilado como um arquivo DLL que pode ser executado com `dotnet bin\Debug\netcoreapp1.0\Hello.dll` no Windows (use `/` para sistemas não Windows). Também é possível especificar argumentos para o aplicativo, como você verá adiante no tópico.

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    Como um cenário avançado, é possível compilar o aplicativo como um conjunto independente de arquivos específicos de plataforma que pode ser implantado e executado em um computador que não tem necessariamente o .NET Core instalado. Consulte [Implantação do .NET Core Application](../deploying/index.md) para obter mais informações.

### <a name="augmenting-the-program"></a>Ampliando o programa

Vamos alterar o programa um pouco. Números de Fibonacci são divertidos; portanto, vamos adicionar isso, além de usar o argumento para saudar a pessoa que executa o aplicativo.

1. Substitua o conteúdo do arquivo *Program.cs* pelo seguinte código:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. Execute [`dotnet build`](../tools/dotnet-build.md) para compilar as alterações.

3. Execute o programa passando um parâmetro para o aplicativo:

   ```
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

E pronto.  Você pode ampliar `Program.cs` como desejar.

## <a name="working-with-multiple-files"></a>Trabalhando com vários arquivos

Arquivos individuais são adequados para programas avulsos simples, mas se você estiver compilando um aplicativo mais complexo, provavelmente terá vários arquivos de origem no projeto. Vamos compilar com base no exemplo anterior de Fibonacci armazenando em cache alguns valores de Fibonacci e adicionar alguns recursos recursivos. 

1. Adicione um novo arquivo no diretório *Hello* chamado *FibonacciGenerator.cs* com o seguinte código:

   [!code-csharp[Gerador de Fibonacci](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. Altere o método `Main` no arquivo *Program.cs* para criar uma instância da nova classe e chame seu método como no seguinte exemplo:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Execute [`dotnet build`](../tools/dotnet-build.md) para compilar as alterações.

4. Execute o aplicativo executando [`dotnet run`](../tools/dotnet-run.md). O seguinte código mostra a saída do programa:

   ```
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

E pronto. Agora, é possível começar a usar os conceitos básicos aprendidos aqui para criar seus próprios programas.

Observe que os comandos e as etapas mostradas neste tutorial para executar o aplicativo são usadas somente durante o tempo de desenvolvimento. Quando estiver pronto para implantar o aplicativo, você desejará dar uma olhada nas diferentes [estratégias de implantação](../deploying/index.md) para aplicativos .NET Core e no comando [`dotnet publish`](../tools/dotnet-publish.md).

## <a name="see-also"></a>Consulte também

[Organizando e testando projetos com as ferramentas da CLI do .NET Core](testing-with-cli.md)

