---
title: Desenvolver bibliotecas com o CLI do .NET Core
description: Saiba como criar bibliotecas do .NET Core usando o CLI do .NET Core. Você criará uma biblioteca que dá suporte a várias estruturas.
author: cartermp
ms.topic: how-to
ms.date: 05/01/2017
ms.openlocfilehash: 7aadaf7bf7819d52a57c3a137beff46d924d8cb0
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396207"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="948ce-104">Desenvolver bibliotecas com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="948ce-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="948ce-105">Este artigo aborda como gravar bibliotecas para .NET usando o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="948ce-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="948ce-106">A CLI fornece uma experiência eficiente e de baixo nível que funciona em qualquer sistema operacional com suporte.</span><span class="sxs-lookup"><span data-stu-id="948ce-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="948ce-107">Você ainda pode criar bibliotecas com o Visual Studio e, se essa for sua experiência preferida, [consultar o guia do Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="948ce-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="948ce-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="948ce-108">Prerequisites</span></span>

<span data-ttu-id="948ce-109">Você precisa da [CLI e do SDK do .NET Core](https://dotnet.microsoft.com/download) instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="948ce-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="948ce-110">Para as seções deste documento que tratam de versões do .NET Framework, é necessário ter o [.NET Framework](https://dotnet.microsoft.com) instalado em um computador Windows.</span><span class="sxs-lookup"><span data-stu-id="948ce-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="948ce-111">Além disso, se você quiser dar suporte a destinos de .NET Framework mais antigos, será necessário instalar pacotes de direcionamento ou pacotes de desenvolvedor na [página de arquivos de download do .net](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="948ce-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="948ce-112">Consulte esta tabela:</span><span class="sxs-lookup"><span data-stu-id="948ce-112">Refer to this table:</span></span>

| <span data-ttu-id="948ce-113">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="948ce-113">.NET Framework version</span></span> | <span data-ttu-id="948ce-114">O que baixar</span><span class="sxs-lookup"><span data-stu-id="948ce-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="948ce-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="948ce-115">4.6.1</span></span>                  | <span data-ttu-id="948ce-116">Pacote de Direcionamento do .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="948ce-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="948ce-117">4.6</span><span class="sxs-lookup"><span data-stu-id="948ce-117">4.6</span></span>                    | <span data-ttu-id="948ce-118">Pacote de Direcionamento do .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="948ce-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="948ce-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="948ce-119">4.5.2</span></span>                  | <span data-ttu-id="948ce-120">Pacote de Desenvolvedor do .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="948ce-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="948ce-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="948ce-121">4.5.1</span></span>                  | <span data-ttu-id="948ce-122">Pacote de Desenvolvedor do .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="948ce-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="948ce-123">4.5</span><span class="sxs-lookup"><span data-stu-id="948ce-123">4.5</span></span>                    | <span data-ttu-id="948ce-124">Software Development Kit do Windows (SDK do Windows) para Windows 8</span><span class="sxs-lookup"><span data-stu-id="948ce-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="948ce-125">4,0</span><span class="sxs-lookup"><span data-stu-id="948ce-125">4.0</span></span>                    | <span data-ttu-id="948ce-126">SDK do Windows para Windows 7 e .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="948ce-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="948ce-127">2.0, 3.0 e 3.5</span><span class="sxs-lookup"><span data-stu-id="948ce-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="948ce-128">Runtime do .NET Framework 3.5 SP1 (ou versão do Windows 8 ou superior)</span><span class="sxs-lookup"><span data-stu-id="948ce-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="948ce-129">Como direcionar para o .NET Standard</span><span class="sxs-lookup"><span data-stu-id="948ce-129">How to target the .NET Standard</span></span>

<span data-ttu-id="948ce-130">Se você não estiver familiarizado com .NET Standard, consulte [.net Standard](../../standard/net-standard.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="948ce-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="948ce-131">Neste artigo, há uma tabela que mapeia .NET Standard versões para várias implementações:</span><span class="sxs-lookup"><span data-stu-id="948ce-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="948ce-132">Veja aqui o que essa tabela significa para fins de criação de uma biblioteca:</span><span class="sxs-lookup"><span data-stu-id="948ce-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="948ce-133">A versão do .NET Standard que você escolher será uma compensação entre o acesso às APIs mais recentes e a capacidade de direcionar mais implementações e .NET Standard versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="948ce-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="948ce-134">Você controla o intervalo de plataformas e versões de destino escolhendo uma versão de `netstandardX.X` (onde `X.X` é um número de versão) e adicionando-a ao arquivo de projeto ( `.csproj` ou `.fsproj` ).</span><span class="sxs-lookup"><span data-stu-id="948ce-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="948ce-135">Você tem três opções principais ao direcionar .NET Standard, dependendo de suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="948ce-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="948ce-136">Você pode usar a versão padrão do .NET Standard fornecida por modelos, `netstandard1.4` , que fornece acesso à maioria das APIs no .net Standard enquanto ainda é compatível com UWP, .NET Framework 4.6.1 e .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="948ce-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="948ce-137">Você pode usar uma versão inferior ou superior do .NET Standard modificando o valor no `TargetFramework` nó do seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="948ce-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="948ce-138">Versões do .NET Standard são compatíveis com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="948ce-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="948ce-139">Isso significa que as bibliotecas `netstandard1.0` são executadas em plataformas `netstandard1.1` e superior.</span><span class="sxs-lookup"><span data-stu-id="948ce-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="948ce-140">No entanto, não há compatibilidade com o encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="948ce-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="948ce-141">As plataformas de .NET Standard inferiores não podem fazer referência a mais altas.</span><span class="sxs-lookup"><span data-stu-id="948ce-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="948ce-142">Isso significa que as bibliotecas `netstandard1.0` não podem fazer de referência a bibliotecas direcionadas a `netstandard1.1` ou superior.</span><span class="sxs-lookup"><span data-stu-id="948ce-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="948ce-143">Selecione a versão Standard com a combinação de suporte a APIs e plataformas ideal para suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="948ce-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="948ce-144">É recomendável `netstandard1.4` por enquanto.</span><span class="sxs-lookup"><span data-stu-id="948ce-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="948ce-145">Se você quiser direcionar .NET Framework versões 4,0 ou inferior, ou se desejar usar uma API disponível em .NET Framework, mas não em .NET Standard (por exemplo, `System.Drawing` ), leia as seções a seguir e saiba como usar multidirecionar.</span><span class="sxs-lookup"><span data-stu-id="948ce-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="948ce-146">Como direcionar .NET Framework</span><span class="sxs-lookup"><span data-stu-id="948ce-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="948ce-147">Estas instruções pressupõem que você tenha .NET Framework instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="948ce-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="948ce-148">Consulte os [Pré-requisitos](#prerequisites) para obter as dependências instaladas.</span><span class="sxs-lookup"><span data-stu-id="948ce-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="948ce-149">Tenha em mente que algumas das versões .NET Framework usadas aqui não são mais suportadas.</span><span class="sxs-lookup"><span data-stu-id="948ce-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="948ce-150">Consulte as [Perguntas Frequentes de Política do Ciclo de Vida de Suporte do .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) sobre versões sem suporte.</span><span class="sxs-lookup"><span data-stu-id="948ce-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="948ce-151">Se você quiser alcançar o número máximo de desenvolvedores e projetos, use .NET Framework 4,0 como seu destino de linha de base.</span><span class="sxs-lookup"><span data-stu-id="948ce-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="948ce-152">Para direcionar .NET Framework, comece usando o moniker (TFM) da estrutura de destino correto que corresponde à versão do .NET Framework que você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="948ce-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="948ce-153">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="948ce-153">.NET Framework version</span></span> | <span data-ttu-id="948ce-154">TFM</span><span class="sxs-lookup"><span data-stu-id="948ce-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="948ce-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="948ce-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="948ce-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="948ce-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="948ce-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="948ce-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="948ce-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="948ce-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="948ce-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="948ce-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="948ce-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="948ce-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="948ce-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="948ce-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="948ce-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="948ce-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="948ce-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="948ce-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="948ce-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="948ce-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="948ce-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="948ce-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="948ce-166">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="948ce-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="948ce-167">Em seguida, insira esse TFM na seção `TargetFramework` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="948ce-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="948ce-168">Por exemplo, veja como você escreveria uma biblioteca que tem como alvo .NET Framework 4,0:</span><span class="sxs-lookup"><span data-stu-id="948ce-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="948ce-169">Pronto!</span><span class="sxs-lookup"><span data-stu-id="948ce-169">And that's it!</span></span> <span data-ttu-id="948ce-170">Embora isso seja compilado apenas para .NET Framework 4, você pode usar a biblioteca em versões mais recentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="948ce-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="948ce-171">Como multidirecionar</span><span class="sxs-lookup"><span data-stu-id="948ce-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="948ce-172">As instruções a seguir pressupõem que você tenha o .NET Framework instalado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="948ce-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="948ce-173">Consulte a seção [Pré-requisitos](#prerequisites) para saber quais dependências você precisa instalar e de onde baixá-las.</span><span class="sxs-lookup"><span data-stu-id="948ce-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="948ce-174">Talvez seja necessário direcionar para versões mais antigas do .NET Framework quando seu projeto dá suporte a ambos o .NET Framework e o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="948ce-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="948ce-175">Nesse cenário, se você quiser usar construções de linguagem e APIs mais recentes para os destinos, use as diretivas `#if` no seu código.</span><span class="sxs-lookup"><span data-stu-id="948ce-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="948ce-176">Você também pode precisar adicionar diferentes pacotes e dependências para cada plataforma de destino para incluir as diferentes APIs necessárias para cada caso.</span><span class="sxs-lookup"><span data-stu-id="948ce-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="948ce-177">Por exemplo, digamos que você tem uma biblioteca que executa operações de rede por meio de HTTP.</span><span class="sxs-lookup"><span data-stu-id="948ce-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="948ce-178">Para .NET Standard e .NET Framework versões 4.5 ou posterior, você pode usar a classe `HttpClient` do namespace `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="948ce-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="948ce-179">No entanto, versões anteriores do .NET Framework não tem a classe `HttpClient`, portanto, você pode usar a classe `WebClient` do namespace `System.Net` para elas.</span><span class="sxs-lookup"><span data-stu-id="948ce-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="948ce-180">O arquivo de projeto seria semelhante a:</span><span class="sxs-lookup"><span data-stu-id="948ce-180">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="948ce-181">Você notará três alterações importantes aqui:</span><span class="sxs-lookup"><span data-stu-id="948ce-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="948ce-182">O nó `TargetFramework` foi substituído pelo `TargetFrameworks` e três TFMs são expressas dentro.</span><span class="sxs-lookup"><span data-stu-id="948ce-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="948ce-183">Há um nó `<ItemGroup>` para o destino `net40` extraindo um que o .NET Framework referencia.</span><span class="sxs-lookup"><span data-stu-id="948ce-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="948ce-184">Há um nó `<ItemGroup>` para o destino `net45` extraindo dois que o .NET Framework referencia.</span><span class="sxs-lookup"><span data-stu-id="948ce-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="948ce-185">O sistema de build reconhece os seguintes símbolos do pré-processador usados nas diretivas `#if`:</span><span class="sxs-lookup"><span data-stu-id="948ce-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="948ce-186">Aqui está um exemplo fazendo uso de compilação condicional por destino:</span><span class="sxs-lookup"><span data-stu-id="948ce-186">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="948ce-187">Se você compilar esse projeto com `dotnet build`, notará três diretórios sob a pasta `bin/`:</span><span class="sxs-lookup"><span data-stu-id="948ce-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="948ce-188">Cada um deles contém arquivos `.dll` para cada destino.</span><span class="sxs-lookup"><span data-stu-id="948ce-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="948ce-189">Como testar bibliotecas .NET Core</span><span class="sxs-lookup"><span data-stu-id="948ce-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="948ce-190">É importante ser capaz de testar em várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="948ce-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="948ce-191">Você pode usar o [xUnit](https://xunit.github.io/) ou MSTest pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="948ce-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="948ce-192">Ambos são perfeitamente adequados para realizar o teste da unidade de biblioteca no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="948ce-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="948ce-193">A maneira de configurar sua solução com projetos de teste dependerá da [estrutura da sua solução](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="948ce-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="948ce-194">O exemplo a seguir pressupõe que os diretórios de origem e de teste estão no mesmo diretório de nível superior.</span><span class="sxs-lookup"><span data-stu-id="948ce-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="948ce-195">Isso usa alguns comandos [CLI do .NET Core](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="948ce-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="948ce-196">Consulte [dotnet new](../tools/dotnet-new.md) e [dotnet sln](../tools/dotnet-sln.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="948ce-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="948ce-197">Configure sua solução.</span><span class="sxs-lookup"><span data-stu-id="948ce-197">Set up your solution.</span></span> <span data-ttu-id="948ce-198">Você pode fazer isso usando os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="948ce-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="948ce-199">Isso criará projetos e os conectará em uma solução.</span><span class="sxs-lookup"><span data-stu-id="948ce-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="948ce-200">O diretório para `SolutionWithSrcAndTest` deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="948ce-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="948ce-201">Navegue até o diretório do projeto de teste e adicione uma referência a `MyProject.Test` de `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="948ce-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="948ce-202">Restaure os pacotes e compile projetos:</span><span class="sxs-lookup"><span data-stu-id="948ce-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="948ce-203">Verifique se o xUnit é executado por meio da execução do comando `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="948ce-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="948ce-204">Se você optar por usar o MSTest, o executor de console do MSTest deverá ser executado.</span><span class="sxs-lookup"><span data-stu-id="948ce-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="948ce-205">Pronto!</span><span class="sxs-lookup"><span data-stu-id="948ce-205">And that's it!</span></span> <span data-ttu-id="948ce-206">Agora você pode testar sua biblioteca em todas as plataformas usando ferramentas de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="948ce-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="948ce-207">É muito simples testar sua biblioteca agora que está tudo configurado:</span><span class="sxs-lookup"><span data-stu-id="948ce-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="948ce-208">Faça alterações na sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="948ce-208">Make changes to your library.</span></span>
1. <span data-ttu-id="948ce-209">Execute os testes de linha de comando no diretório de teste com o comando `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="948ce-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="948ce-210">Seu código será recriado automaticamente quando você invoca o comando `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="948ce-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="948ce-211">Como usar vários projetos</span><span class="sxs-lookup"><span data-stu-id="948ce-211">How to use multiple projects</span></span>

<span data-ttu-id="948ce-212">Uma necessidade comum das bibliotecas grandes é alocar funcionalidades em diferentes projetos.</span><span class="sxs-lookup"><span data-stu-id="948ce-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="948ce-213">Imagine que você deseja criar uma biblioteca que poderia ser consumida em idiomática C# e F #.</span><span class="sxs-lookup"><span data-stu-id="948ce-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="948ce-214">Isso significaria que os consumidores da sua biblioteca o consomem de formas naturais para C# ou F #.</span><span class="sxs-lookup"><span data-stu-id="948ce-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="948ce-215">Por exemplo, você poderia consumir a biblioteca em C# dessa forma:</span><span class="sxs-lookup"><span data-stu-id="948ce-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="948ce-216">No F#, ela poderia assemelhar-se a:</span><span class="sxs-lookup"><span data-stu-id="948ce-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="948ce-217">Cenários de consumo como esse significam que as APIs que estão sendo acessadas devem ter uma estrutura diferente para C# e F#.</span><span class="sxs-lookup"><span data-stu-id="948ce-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="948ce-218">Uma abordagem comum para realizar isso é fatorar toda a lógica de uma biblioteca em um projeto principal, com projetos C# e F# definindo as camadas de API que chamam esse projeto principal.</span><span class="sxs-lookup"><span data-stu-id="948ce-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="948ce-219">O restante da seção usará os nomes a seguir:</span><span class="sxs-lookup"><span data-stu-id="948ce-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="948ce-220">**AwesomeLibrary. Core** – um projeto principal que contém toda a lógica da biblioteca</span><span class="sxs-lookup"><span data-stu-id="948ce-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="948ce-221">**AwesomeLibrary.CSharp** – Um projeto com APIs públicas destinadas ao consumo em C#</span><span class="sxs-lookup"><span data-stu-id="948ce-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="948ce-222">**AwesomeLibrary.FSharp** – Um projeto com APIs públicas destinadas ao consumo em F#</span><span class="sxs-lookup"><span data-stu-id="948ce-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="948ce-223">Você pode executar os comandos a seguir no seu terminal para produzir a mesma estrutura que este guia:</span><span class="sxs-lookup"><span data-stu-id="948ce-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="948ce-224">Isso adicionará os três projetos acima e um arquivo de solução que os vinculará juntos.</span><span class="sxs-lookup"><span data-stu-id="948ce-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="948ce-225">Criar o arquivo de solução e vincular projetos permitirá que você restaure e crie projetos de um nível superior.</span><span class="sxs-lookup"><span data-stu-id="948ce-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="948ce-226">Referência projeto a projeto</span><span class="sxs-lookup"><span data-stu-id="948ce-226">Project-to-project referencing</span></span>

<span data-ttu-id="948ce-227">A melhor maneira de fazer referência a um projeto é usar a CLI do .NET Core para adicionar uma referência de projeto.</span><span class="sxs-lookup"><span data-stu-id="948ce-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="948ce-228">Dos diretórios dos projetos **AwesomeLibrary.CSharp** e **AwesomeLibrary.FSharp**, você pode executar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="948ce-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="948ce-229">Os arquivos de projeto para **AwesomeLibrary.CSharp** e **AwesomeLibrary.FSharp** agora farão referência a **AwesomeLibrary.Core** como um destino `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="948ce-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="948ce-230">Você pode verificar isso inspecionando os arquivos de projeto e vendo o seguinte neles:</span><span class="sxs-lookup"><span data-stu-id="948ce-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="948ce-231">Você pode adicionar esta seção a cada arquivo de projeto manualmente se preferir não usar a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="948ce-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="948ce-232">Estruturar uma solução</span><span class="sxs-lookup"><span data-stu-id="948ce-232">Structuring a solution</span></span>

<span data-ttu-id="948ce-233">Outro aspecto importante das soluções multiprojetos é estabelecer uma boa estrutura de projeto geral.</span><span class="sxs-lookup"><span data-stu-id="948ce-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="948ce-234">Você pode organizar o código da maneira que desejar, e desde que vincule cada projeto ao arquivo de solução com `dotnet sln add`, você poderá executar `dotnet restore` e `dotnet build` no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="948ce-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
