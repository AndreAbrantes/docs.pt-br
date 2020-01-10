---
title: Reduzindo as dependências de pacote com o project.json
description: Reduza as dependências do pacote ao criar bibliotecas com base no project.json.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740832"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="d1073-103">Reduzindo as dependências de pacote com o project.json</span><span class="sxs-lookup"><span data-stu-id="d1073-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="d1073-104">Este artigo aborda o que você precisa saber sobre como reduzir suas dependências de pacote ao criar bibliotecas `project.json`.</span><span class="sxs-lookup"><span data-stu-id="d1073-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="d1073-105">No final deste artigo, você aprenderá como compor sua biblioteca de forma que ela usa apenas as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="d1073-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span>

## <a name="why-its-important"></a><span data-ttu-id="d1073-106">Por que isso é importante</span><span class="sxs-lookup"><span data-stu-id="d1073-106">Why it's Important</span></span>

<span data-ttu-id="d1073-107">O .NET Core é um produto composto por pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="d1073-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="d1073-108">Um pacote essencial é o [metapacote .NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), que é um pacote NuGet composto por outros pacotes.</span><span class="sxs-lookup"><span data-stu-id="d1073-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span> <span data-ttu-id="d1073-109">Ele fornece o conjunto de pacotes que têm garantia de trabalho em várias implementações do .NET, como .NET Framework, .NET Core e Xamarin/mono.</span><span class="sxs-lookup"><span data-stu-id="d1073-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core, and Xamarin/Mono.</span></span>

<span data-ttu-id="d1073-110">No entanto, há uma boa chance de que a biblioteca não use todos os pacotes que ele contém.</span><span class="sxs-lookup"><span data-stu-id="d1073-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="d1073-111">Ao criar uma biblioteca e distribuí-la com o NuGet, é uma melhor prática “cortar” suas dependências para deixar apenas os pacotes que realmente serão usados.</span><span class="sxs-lookup"><span data-stu-id="d1073-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="d1073-112">Isso resulta em uma menor superfície geral de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="d1073-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="d1073-113">Como fazer isso</span><span class="sxs-lookup"><span data-stu-id="d1073-113">How to do it</span></span>

<span data-ttu-id="d1073-114">Atualmente, não há nenhum comando `dotnet` oficial que corte as referências do pacote.</span><span class="sxs-lookup"><span data-stu-id="d1073-114">Currently, there is no official `dotnet` command that trims package references.</span></span>  <span data-ttu-id="d1073-115">Em vez disso, você terá que fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="d1073-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="d1073-116">O processo geral é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="d1073-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="d1073-117">Faça referência à `NETStandard.Library` versão `1.6.0` em uma seção `dependencies` de seu `project.json`.</span><span class="sxs-lookup"><span data-stu-id="d1073-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="d1073-118">Restaure pacotes com `dotnet restore` ([veja observação](#dotnet-restore-note)) por meio da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d1073-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="d1073-119">Inspecione o arquivo `project.lock.json` e localize a seção `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="d1073-119">Inspect the `project.lock.json` file and find the `NETStandard.Library` section.</span></span>  <span data-ttu-id="d1073-120">Ele estará perto do início do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1073-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="d1073-121">Copie todos os pacotes listados em `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="d1073-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="d1073-122">Remova a referência `.NETStandard.Library` e substitua-a pelos pacotes copiados.</span><span class="sxs-lookup"><span data-stu-id="d1073-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="d1073-123">Remova as referências aos pacotes que não são necessários.</span><span class="sxs-lookup"><span data-stu-id="d1073-123">Remove references to packages you don't need.</span></span>

<span data-ttu-id="d1073-124">Você pode descobrir quais pacotes não são necessários das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="d1073-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="d1073-125">Tentativa e erro.</span><span class="sxs-lookup"><span data-stu-id="d1073-125">Trial and error.</span></span> <span data-ttu-id="d1073-126">Isso significa remover um pacote, restaurar, ver se sua biblioteca ainda é compilada e repetir esse processo.</span><span class="sxs-lookup"><span data-stu-id="d1073-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="d1073-127">Usar uma ferramenta como [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) ou [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) para inspecionar as referências e ver o que seu código realmente está usando.</span><span class="sxs-lookup"><span data-stu-id="d1073-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span> <span data-ttu-id="d1073-128">Em seguida, você pode remover pacotes que não correspondem aos tipos que você está usando.</span><span class="sxs-lookup"><span data-stu-id="d1073-128">You can then remove packages that don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="d1073-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1073-129">Example</span></span>

<span data-ttu-id="d1073-130">Imagine que você escreveu uma biblioteca que forneceu funcionalidade adicional para tipos de coleção genéricos.</span><span class="sxs-lookup"><span data-stu-id="d1073-130">Imagine that you wrote a library that provided additional functionality to generic collection types.</span></span> <span data-ttu-id="d1073-131">Uma biblioteca precisaria depender de pacotes como `System.Collections`, mas pode não de pacotes como `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="d1073-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span> <span data-ttu-id="d1073-132">Dessa forma, seria bom cortar as dependências do pacote para reduzir até o que essa biblioteca realmente precisa.</span><span class="sxs-lookup"><span data-stu-id="d1073-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="d1073-133">Para cortar essa biblioteca, você deve começar com o arquivo `project.json` e adicionar uma referência ao `NETStandard.Library` versão `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="d1073-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="d1073-134">Em seguida, restaure pacotes com `dotnet restore` ([veja observação](#dotnet-restore-note)), inspecione o arquivo `project.lock.json` e localize todos os pacotes restaurados para `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="d1073-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETStandard.Library`.</span></span>

<span data-ttu-id="d1073-135">Veja como a seção relevante no arquivo `project.lock.json` se parece ao redirecionar para `netstandard1.0`:</span><span class="sxs-lookup"><span data-stu-id="d1073-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

<span data-ttu-id="d1073-136">Em seguida, copie as referências do pacote para a seção `dependencies` do arquivo `project.json` da biblioteca, substituindo a referência `NETStandard.Library`:</span><span class="sxs-lookup"><span data-stu-id="d1073-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

<span data-ttu-id="d1073-137">Há um grande volume de pacotes, muitos dos quais certamente não são necessários para estender os tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="d1073-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="d1073-138">Você pode remover os pacotes manualmente ou usar uma ferramenta como [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) ou [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) para identificar quais pacotes seu código realmente usa.</span><span class="sxs-lookup"><span data-stu-id="d1073-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="d1073-139">Veja como um pacote cortado pareceria:</span><span class="sxs-lookup"><span data-stu-id="d1073-139">Here's what a trimmed package could look like:</span></span>

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="d1073-140">Agora, ele tem uma superfície menor do que se tivesse dependentes no metapacote `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="d1073-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
