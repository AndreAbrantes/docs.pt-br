---
title: Novidades do .NET Core 3.0
description: Conheça os novos recursos encontrados no .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 10/22/2019
ms.openlocfilehash: 4bf1c4826273535bfe824828f0fad96998b29483
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742596"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="87d96-103">Novidades do .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87d96-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="87d96-104">Este artigo descreve o que há de novo no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="87d96-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="87d96-105">Um dos maiores avanços é o suporte para aplicativos Windows de área de trabalho (somente Windows).</span><span class="sxs-lookup"><span data-stu-id="87d96-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="87d96-106">Usando a Área de Trabalho do Windows do componente de SDK do .NET Core 3.0, você pode portar seus aplicativos Windows Forms e WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="87d96-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="87d96-107">Para deixar claro, o componente Windows Desktop só é compatível com o Windows e só é incluído nele.</span><span class="sxs-lookup"><span data-stu-id="87d96-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="87d96-108">Para obter mais informações, consulte a seção [Área de Trabalho do Windows](#windows-desktop) mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="87d96-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="87d96-109">O .NET Core 3.0 adiciona suporte para C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="87d96-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="87d96-110">É altamente recomendável que você use o [Visual Studio 2019 versão 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou mais recente, [Visual Studio para Mac 8,3](/visualstudio/mac/install-preview) ou mais recente ou [Visual Studio Code](https://code.visualstudio.com/) com a  **C# extensão**mais recente.</span><span class="sxs-lookup"><span data-stu-id="87d96-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="87d96-111">[Baixe e comece a usar o .NET Core 3.0](https://aka.ms/netcore3download) agora no Windows, no MacOS ou no Linux.</span><span class="sxs-lookup"><span data-stu-id="87d96-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="87d96-112">Para obter mais informações sobre a versão, consulte o [anúncio do .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="87d96-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="87d96-113">O .NET Core RC1 foi considerado pronto para produção pela Microsoft e foi totalmente suportado.</span><span class="sxs-lookup"><span data-stu-id="87d96-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="87d96-114">Se você estiver usando uma versão de visualização, deverá mover para a versão RTM para obter suporte contínuo.</span><span class="sxs-lookup"><span data-stu-id="87d96-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="87d96-115">Melhorias na C# linguagem 8,0</span><span class="sxs-lookup"><span data-stu-id="87d96-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="87d96-116">C#8,0 também faz parte desta versão, que inclui o recurso de [tipos de referência anulável](../../csharp/tutorials/nullable-reference-types.md) , [fluxos assíncronos](../../csharp/tutorials/generate-consume-asynchronous-stream.md)e [mais padrões](../../csharp/tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="87d96-117">Para obter mais informações sobre recursos do C# 8.0, consulte [Novidades do C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="87d96-118">Foram adicionados aprimoramentos de linguagem para dar suporte aos seguintes recursos de API detalhados abaixo:</span><span class="sxs-lookup"><span data-stu-id="87d96-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="87d96-119">Intervalos e índices</span><span class="sxs-lookup"><span data-stu-id="87d96-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="87d96-120">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="87d96-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="87d96-121">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="87d96-121">.NET Standard 2.1</span></span>

<span data-ttu-id="87d96-122">O .NET Core 3,0 implementa **.NET Standard 2,1**.</span><span class="sxs-lookup"><span data-stu-id="87d96-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="87d96-123">No entanto, o modelo de `dotnet new classlib` padrão gera um projeto que ainda tem como alvo **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="87d96-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="87d96-124">Para direcionar ao **.NET Standard 2.1**, edite seu arquivo de projeto e altere a propriedade `TargetFramework` para `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="87d96-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="87d96-125">Se você estiver usando o Visual Studio, precisará do [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), já que o Visual Studio 2017 não dá suporte ao **.NET Standard 2.1** nem ao **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="87d96-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="87d96-126">Compilar/implantar</span><span class="sxs-lookup"><span data-stu-id="87d96-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="87d96-127">Executáveis por padrão</span><span class="sxs-lookup"><span data-stu-id="87d96-127">Default executables</span></span>

<span data-ttu-id="87d96-128">O .NET Core agora compila [executáveis dependentes de estrutura](../deploying/index.md#framework-dependent-executables-fde) por padrão.</span><span class="sxs-lookup"><span data-stu-id="87d96-128">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="87d96-129">Esse comportamento é novo para aplicativos que usam uma versão do .NET Core instalada globalmente.</span><span class="sxs-lookup"><span data-stu-id="87d96-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="87d96-130">Anteriormente, apenas [implantações autocontidas](../deploying/index.md#self-contained-deployments-scd) produziam um executável.</span><span class="sxs-lookup"><span data-stu-id="87d96-130">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="87d96-131">Durante `dotnet build` ou `dotnet publish`, é criado um executável que corresponde ao ambiente e à plataforma do SDK que você está usando.</span><span class="sxs-lookup"><span data-stu-id="87d96-131">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="87d96-132">Você pode esperar desses executáveis o mesmo que de outros executáveis nativos, como:</span><span class="sxs-lookup"><span data-stu-id="87d96-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="87d96-133">Você pode clicar duas vezes no arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="87d96-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="87d96-134">Você pode iniciar o aplicativo diretamente de um prompt de comando, como `myapp.exe` no Windows e `./myapp` no Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="87d96-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="87d96-135">Executáveis de arquivo único</span><span class="sxs-lookup"><span data-stu-id="87d96-135">Single-file executables</span></span>

<span data-ttu-id="87d96-136">O comando `dotnet publish` dá suporte ao empacotamento de seu aplicativo em um executável de arquivo único específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="87d96-136">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="87d96-137">O executável é autoextraível e contém todas as dependências (incluindo nativas) necessárias para a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87d96-137">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="87d96-138">Quando o aplicativo é executado pela primeira vez, o aplicativo é extraído para um diretório com base no nome do aplicativo e no identificador do build.</span><span class="sxs-lookup"><span data-stu-id="87d96-138">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="87d96-139">A inicialização é mais rápida quando o aplicativo é executado novamente.</span><span class="sxs-lookup"><span data-stu-id="87d96-139">Startup is faster when the application is run again.</span></span> <span data-ttu-id="87d96-140">O aplicativo não precisará autoextrair uma segunda vez, a menos que uma versão nova tenha sido usada.</span><span class="sxs-lookup"><span data-stu-id="87d96-140">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="87d96-141">Para publicar um único arquivo executável, defina o `PublishSingleFile` em seu projeto ou na linha de comando com o comando `dotnet publish`:</span><span class="sxs-lookup"><span data-stu-id="87d96-141">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="87d96-142">- ou -</span><span class="sxs-lookup"><span data-stu-id="87d96-142">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="87d96-143">Para obter mais informações sobre a publicação de arquivo único, consulte o [documento de design de empacotador de arquivo único](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-143">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="87d96-144">Vinculação de assembly</span><span class="sxs-lookup"><span data-stu-id="87d96-144">Assembly linking</span></span>

<span data-ttu-id="87d96-145">O SDK do .NET Core 3.0 vem com uma ferramenta que pode reduzir o tamanho dos aplicativos analisando a IL e cortando assemblies não utilizados.</span><span class="sxs-lookup"><span data-stu-id="87d96-145">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="87d96-146">Os aplicativos autossuficientes incluem todos os componentes necessários para executar seu código, sem exigir que o .NET seja instalado no computador host.</span><span class="sxs-lookup"><span data-stu-id="87d96-146">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="87d96-147">No entanto, muitas vezes o aplicativo requer apenas um pequeno subconjunto da estrutura para funcionar, e outras bibliotecas não utilizadas podem ser removidas.</span><span class="sxs-lookup"><span data-stu-id="87d96-147">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="87d96-148">O .NET Core agora inclui uma configuração que usará a ferramenta[Vinculador de IL](https://github.com/mono/linker) para verificar a IL do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87d96-148">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="87d96-149">Essa ferramenta detecta o código necessário e, em seguida, corta as bibliotecas não utilizadas.</span><span class="sxs-lookup"><span data-stu-id="87d96-149">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="87d96-150">Ela pode reduzir significativamente o tamanho da implantação de alguns aplicativos.</span><span class="sxs-lookup"><span data-stu-id="87d96-150">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="87d96-151">Para habilitá-la, adicione a configuração `<PublishTrimmed>` ao seu projeto e publique um aplicativo autossuficiente:</span><span class="sxs-lookup"><span data-stu-id="87d96-151">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="87d96-152">Por exemplo, o modelo básico de novo projeto de console "hello world" incluído, quando publicado, atinge cerca de 70 MB de tamanho.</span><span class="sxs-lookup"><span data-stu-id="87d96-152">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="87d96-153">Usando `<PublishTrimmed>`, esse tamanho é reduzido para cerca de 30 MB.</span><span class="sxs-lookup"><span data-stu-id="87d96-153">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="87d96-154">É importante considerar que os aplicativos ou estruturas (incluindo ASP.NET Core e WPF) que usam reflexão ou recursos dinâmicos relacionados, geralmente são interrompidos quando cortados.</span><span class="sxs-lookup"><span data-stu-id="87d96-154">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="87d96-155">Essa interrupção ocorre porque o vinculador não tem ciência desse comportamento dinâmico e não pode determinar quais tipos de estrutura são necessários para reflexão.</span><span class="sxs-lookup"><span data-stu-id="87d96-155">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="87d96-156">A ferramenta Vinculador de IL pode ser configurada para estar ciente deste cenário.</span><span class="sxs-lookup"><span data-stu-id="87d96-156">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="87d96-157">Antes de mais nada, teste seu aplicativo depois de cortar.</span><span class="sxs-lookup"><span data-stu-id="87d96-157">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="87d96-158">Para saber mais sobre a ferramenta Vinculador de IL, confira a [documentação](https://aka.ms/dotnet-illink) ou visite o repositório [mono/linker]( https://github.com/mono/linker).</span><span class="sxs-lookup"><span data-stu-id="87d96-158">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="87d96-159">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="87d96-159">Tiered compilation</span></span>

<span data-ttu-id="87d96-160">A TC ([compilação em camadas](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)) está ativa por padrão com o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="87d96-160">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="87d96-161">Esse recurso permite que o tempo de execução use de forma mais adaptável o compilador JIT (just-in-time) para obter um melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="87d96-161">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="87d96-162">O principal benefício da compilação em camadas é fornecer duas maneiras de métodos de jitting: em uma camada de qualidade inferior, mas mais rápida, ou em uma camada de qualidade superior, mas mais lenta.</span><span class="sxs-lookup"><span data-stu-id="87d96-162">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="87d96-163">A qualidade refere-se ao quão bem o método é otimizado.</span><span class="sxs-lookup"><span data-stu-id="87d96-163">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="87d96-164">O TC ajuda a melhorar o desempenho de um aplicativo à medida que passa por vários estágios de execução, desde a inicialização até o estado estável.</span><span class="sxs-lookup"><span data-stu-id="87d96-164">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="87d96-165">Quando a compilação em camadas é desabilitada, cada método é compilado de uma única maneira que é ajustada ao desempenho de estado estável no desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="87d96-165">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="87d96-166">Quando TC está habilitado, o comportamento a seguir se aplica à compilação do método quando um aplicativo é inicializado:</span><span class="sxs-lookup"><span data-stu-id="87d96-166">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="87d96-167">Se o método tiver código com compilação antecipada de tempo ou [ReadyToRun](#readytorun-images), o código gerado previamente será usado.</span><span class="sxs-lookup"><span data-stu-id="87d96-167">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="87d96-168">Caso contrário, o método é JIT.</span><span class="sxs-lookup"><span data-stu-id="87d96-168">Otherwise, the method is jitted.</span></span> <span data-ttu-id="87d96-169">Normalmente, esses métodos são genéricos sobre tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="87d96-169">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="87d96-170">O *Quick JIT* produz código mais rápido (ou menos otimizado) com mais rapidez.</span><span class="sxs-lookup"><span data-stu-id="87d96-170">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="87d96-171">No .NET Core 3,0, o JIT rápido é habilitado por padrão para métodos que não contêm loops e são preferenciais durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="87d96-171">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="87d96-172">O JIT totalmente otimizado produz um código de qualidade mais alta (ou mais otimizado) mais lentamente.</span><span class="sxs-lookup"><span data-stu-id="87d96-172">The fully-optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="87d96-173">Para métodos em que a JIT rápida não seria usada (por exemplo, se o método é atribuído com <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), o JIT com otimização total é usado.</span><span class="sxs-lookup"><span data-stu-id="87d96-173">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully-optimizing JIT is used.</span></span>

<span data-ttu-id="87d96-174">Para métodos chamados com frequência, o compilador just-in-time, eventualmente, cria código totalmente otimizado em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="87d96-174">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="87d96-175">Em seguida, o código otimizado substitui o código pré-compilado para esse método.</span><span class="sxs-lookup"><span data-stu-id="87d96-175">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="87d96-176">O código gerado pelo Quick JIT pode ser executado mais lentamente, alocar mais memória ou usar mais espaço de pilha.</span><span class="sxs-lookup"><span data-stu-id="87d96-176">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="87d96-177">Se houver problemas, você poderá desabilitar o JIT rápido usando essa propriedade do MSBuild no arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="87d96-177">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="87d96-178">Para desabilitar completamente o TC, use essa propriedade do MSBuild em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="87d96-178">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="87d96-179">Se você alterar essas configurações no arquivo de projeto, talvez seja necessário executar uma compilação limpa para que as novas configurações sejam refletidas (exclua os diretórios `obj` e `bin` e recompile).</span><span class="sxs-lookup"><span data-stu-id="87d96-179">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="87d96-180">Para obter mais informações sobre como configurar a compilação em tempo de execução, consulte [Opções de configuração de tempo de execução para compilação](../run-time-config/compilation.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-180">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="87d96-181">Imagens ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="87d96-181">ReadyToRun images</span></span>

<span data-ttu-id="87d96-182">Você pode melhorar o tempo de inicialização do seu aplicativo .NET Core compilando seus assemblies de aplicativos como o formato ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="87d96-182">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="87d96-183">R2R é uma forma de compilação antecipada (AOT).</span><span class="sxs-lookup"><span data-stu-id="87d96-183">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="87d96-184">Os binários R2R melhoram o desempenho de inicialização reduzindo a quantidade de trabalho que o compilador just-in-time (JIT) precisa fazer à medida que seu aplicativo é carregado.</span><span class="sxs-lookup"><span data-stu-id="87d96-184">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="87d96-185">Os binários contêm código nativo similar comparado ao que o JIT produziria.</span><span class="sxs-lookup"><span data-stu-id="87d96-185">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="87d96-186">Entretanto, os binários R2R são maiores porque contêm código de IL (linguagem intermediária), que ainda é necessário para alguns cenários, e a versão nativa do mesmo código.</span><span class="sxs-lookup"><span data-stu-id="87d96-186">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="87d96-187">O R2R só está disponível quando você publica um aplicativo autocontido que tenha como alvo um RID (Runtime Environment) específico, como o Linux x64 ou o Windows x64.</span><span class="sxs-lookup"><span data-stu-id="87d96-187">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="87d96-188">Para compilar seu projeto como ReadyToRun, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="87d96-188">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="87d96-189">Adicione a configuração de `<PublishReadyToRun>` ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="87d96-189">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="87d96-190">Publique um aplicativo autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="87d96-190">Publish a self-contained app.</span></span> <span data-ttu-id="87d96-191">Por exemplo, esse comando cria um aplicativo autossuficiente para a versão de 64 bits do Windows:</span><span class="sxs-lookup"><span data-stu-id="87d96-191">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="87d96-192">Restrições de plataforma cruzada/arquitetura</span><span class="sxs-lookup"><span data-stu-id="87d96-192">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="87d96-193">O compilador ReadyToRun atualmente não tem suporte para o direcionamento cruzado.</span><span class="sxs-lookup"><span data-stu-id="87d96-193">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="87d96-194">Você precisa compilar em determinado destino.</span><span class="sxs-lookup"><span data-stu-id="87d96-194">You must compile on a given target.</span></span> <span data-ttu-id="87d96-195">Por exemplo, se você quiser imagens R2R para Windows x64, será necessário executar o comando Publicar nesse ambiente.</span><span class="sxs-lookup"><span data-stu-id="87d96-195">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="87d96-196">Exceções ao direcionamento cruzado:</span><span class="sxs-lookup"><span data-stu-id="87d96-196">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="87d96-197">O Windows x64 pode ser usado para compilar imagens do Windows ARM32, ARM64 e x86.</span><span class="sxs-lookup"><span data-stu-id="87d96-197">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="87d96-198">O Windows x86 pode ser usado para compilar imagens do Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="87d96-198">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="87d96-199">O Linux x64 pode ser usado para compilar imagens do Linux ARM32 e ARM64.</span><span class="sxs-lookup"><span data-stu-id="87d96-199">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="87d96-200">Tempo de execução/SDK</span><span class="sxs-lookup"><span data-stu-id="87d96-200">Runtime/SDK</span></span>

### <a name="major-version-roll-forward"></a><span data-ttu-id="87d96-201">Roll forward de versão principal</span><span class="sxs-lookup"><span data-stu-id="87d96-201">Major-version Roll Forward</span></span>

<span data-ttu-id="87d96-202">O .NET Core 3.0 introduz um recurso opcional que permite que seu aplicativo efetue roll forward para a versão principal mais recente do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87d96-202">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="87d96-203">Adicionalmente, foi adicionada uma nova configuração para controlar como o roll forward é aplicado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87d96-203">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="87d96-204">Isso pode ser configurado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="87d96-204">This can be configured in the following ways:</span></span>

- <span data-ttu-id="87d96-205">Propriedade do arquivo de projeto: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="87d96-205">Project file property: `RollForward`</span></span>
- <span data-ttu-id="87d96-206">Propriedade do arquivo de configuração de tempo de execução: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="87d96-206">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="87d96-207">Variável de ambiente: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="87d96-207">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="87d96-208">Argumento de linha de comando: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="87d96-208">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="87d96-209">Um dos valores a seguir precisa ser especificado.</span><span class="sxs-lookup"><span data-stu-id="87d96-209">One of the following values must be specified.</span></span> <span data-ttu-id="87d96-210">Se a configuração for omitida, **Secundária** será o padrão.</span><span class="sxs-lookup"><span data-stu-id="87d96-210">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="87d96-211">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="87d96-211">**LatestPatch**</span></span>\
<span data-ttu-id="87d96-212">Efetuar roll forward para a versão de patch mais recente.</span><span class="sxs-lookup"><span data-stu-id="87d96-212">Roll forward to the highest patch version.</span></span> <span data-ttu-id="87d96-213">Isso desabilita o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="87d96-213">This disables minor version roll forward.</span></span>
- <span data-ttu-id="87d96-214">**Secundária**</span><span class="sxs-lookup"><span data-stu-id="87d96-214">**Minor**</span></span>\
<span data-ttu-id="87d96-215">Se a versão secundária solicitada estiver ausente, efetue roll forward para a menor versão secundária mais alta.</span><span class="sxs-lookup"><span data-stu-id="87d96-215">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="87d96-216">Se a versão secundária solicitada estiver presente, a política **LatestPatch** será usada.</span><span class="sxs-lookup"><span data-stu-id="87d96-216">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="87d96-217">**Principal**</span><span class="sxs-lookup"><span data-stu-id="87d96-217">**Major**</span></span>\
<span data-ttu-id="87d96-218">Se a versão principal solicitada estiver ausente, efetuar roll forward para a versão principal mais alta e a versão secundária mais baixa.</span><span class="sxs-lookup"><span data-stu-id="87d96-218">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="87d96-219">Se a versão principal solicitada está presente, a política **Secundária** é usada.</span><span class="sxs-lookup"><span data-stu-id="87d96-219">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="87d96-220">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="87d96-220">**LatestMinor**</span></span>\
<span data-ttu-id="87d96-221">Efetuar roll forward para a versão secundária mais recente, mesmo se a versão secundária solicitada estiver presente.</span><span class="sxs-lookup"><span data-stu-id="87d96-221">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="87d96-222">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="87d96-222">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="87d96-223">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="87d96-223">**LatestMajor**</span></span>\
<span data-ttu-id="87d96-224">Efetuar roll forward para a versão principal e a secundária mais altas, mesmo se a principal solicitada estiver presente.</span><span class="sxs-lookup"><span data-stu-id="87d96-224">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="87d96-225">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="87d96-225">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="87d96-226">**Desabilitar**</span><span class="sxs-lookup"><span data-stu-id="87d96-226">**Disable**</span></span>\
<span data-ttu-id="87d96-227">Não efetuar roll forward.</span><span class="sxs-lookup"><span data-stu-id="87d96-227">Don't roll forward.</span></span> <span data-ttu-id="87d96-228">Associar somente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="87d96-228">Only bind to specified version.</span></span> <span data-ttu-id="87d96-229">Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes.</span><span class="sxs-lookup"><span data-stu-id="87d96-229">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="87d96-230">Esse valor só é recomendado para teste.</span><span class="sxs-lookup"><span data-stu-id="87d96-230">This value is only recommended for testing.</span></span>

<span data-ttu-id="87d96-231">Com a exceção da configuração **Desabilitar**, todas as configurações usarão a versão de patch mais recente disponível.</span><span class="sxs-lookup"><span data-stu-id="87d96-231">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="87d96-232">O build copia dependências</span><span class="sxs-lookup"><span data-stu-id="87d96-232">Build copies dependencies</span></span>

<span data-ttu-id="87d96-233">O comando `dotnet build` agora copia as dependências do NuGet para seu aplicativo do cache NuGet para a pasta de saída de build.</span><span class="sxs-lookup"><span data-stu-id="87d96-233">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="87d96-234">Anteriormente, as dependências eram copiadas apenas como parte de `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="87d96-234">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="87d96-235">Há algumas operações, como vinculação e publicação de página do razor, que ainda exigem publicação.</span><span class="sxs-lookup"><span data-stu-id="87d96-235">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="87d96-236">Ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="87d96-236">Local tools</span></span>

<span data-ttu-id="87d96-237">O .NET Core 3.0 apresenta ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="87d96-237">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="87d96-238">Ferramentas locais são semelhantes às [ferramentas globais](../tools/global-tools.md), mas estão associadas a um local específico no disco.</span><span class="sxs-lookup"><span data-stu-id="87d96-238">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="87d96-239">Ferramentas locais não estão disponíveis globalmente e são distribuídas como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="87d96-239">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="87d96-240">Se você tiver tentado ferramentas locais no .NET Core 3.0 Versão Prévia 1, tais como executar `dotnet tool restore` ou `dotnet tool install`, exclua a pasta de cache local de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="87d96-240">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="87d96-241">Caso contrário, as ferramentas locais não funcionarão em nenhuma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="87d96-241">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="87d96-242">Essa pasta está localizada em:</span><span class="sxs-lookup"><span data-stu-id="87d96-242">This folder is located at:</span></span>
>
> <span data-ttu-id="87d96-243">No macOS ou Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="87d96-243">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="87d96-244">No Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="87d96-244">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="87d96-245">As ferramentas locais dependem de um nome de arquivo de manifesto `dotnet-tools.json` no seu diretório atual.</span><span class="sxs-lookup"><span data-stu-id="87d96-245">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="87d96-246">Esse arquivo de manifesto define as ferramentas que estarão disponíveis nessa pasta e abaixo.</span><span class="sxs-lookup"><span data-stu-id="87d96-246">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="87d96-247">Você pode distribuir o arquivo de manifesto com o seu código para garantir que qualquer pessoa que trabalha com o seu código possa restaurar e usar as mesmas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="87d96-247">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="87d96-248">Para ferramentas globais e locais, é necessária uma versão compatível do runtime.</span><span class="sxs-lookup"><span data-stu-id="87d96-248">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="87d96-249">Muitas ferramentas que estão atualmente em NuGet.org direcionam para o runtime do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="87d96-249">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="87d96-250">Para instalar essas ferramentas, de forma global ou local, você ainda precisará instalar o [Runtime do NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="87d96-250">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="87d96-251">Tamanhos menores de heap de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="87d96-251">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="87d96-252">O tamanho do heap do coletor de lixo padrão foi reduzido, resultando em menor uso de memória pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87d96-252">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="87d96-253">Essa alteração se alinha melhor com o orçamento de alocação de geração 0 com os tamanhos de cache de processadores modernos.</span><span class="sxs-lookup"><span data-stu-id="87d96-253">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="87d96-254">Suporte de página grande de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="87d96-254">Garbage Collection Large Page support</span></span>

<span data-ttu-id="87d96-255">Páginas grandes (também conhecidas como páginas enormes no Linux) é um recurso em que o sistema operacional é capaz de estabelecer regiões de memória maiores do que o tamanho da página nativo (geralmente 4K) para melhorar o desempenho do aplicativo que está solicitando essas páginas grandes.</span><span class="sxs-lookup"><span data-stu-id="87d96-255">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="87d96-256">O coletor de lixo agora pode ser configurado com a configuração **GCLargePages** como um recurso opcional a ser escolhido para alocar páginas grandes no Windows.</span><span class="sxs-lookup"><span data-stu-id="87d96-256">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="87d96-257">Windows Desktop & COM</span><span class="sxs-lookup"><span data-stu-id="87d96-257">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="87d96-258">Windows Installer do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="87d96-258">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="87d96-259">O instalador MSI para Windows foi alterado do .NET Core 3.0 em diante.</span><span class="sxs-lookup"><span data-stu-id="87d96-259">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="87d96-260">Os instaladores de SDK agora atualizarão versões de faixa de recurso do SDK no local.</span><span class="sxs-lookup"><span data-stu-id="87d96-260">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="87d96-261">Faixas de recurso são definidas nos grupos de *centenas* na seção *patch* do número de versão.</span><span class="sxs-lookup"><span data-stu-id="87d96-261">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="87d96-262">Por exemplo, **3.0._101_** e **3.0._201_** são versões em duas faixas de recurso diferentes, enquanto **3.0._101_** e **3.0._199_** estão na mesma faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="87d96-262">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="87d96-263">Além disso, quando o SDK do .NET Core **3.0._101_** for instalado, o SDK do .NET Core **3.0._100_** será removido do computador se ele existir.</span><span class="sxs-lookup"><span data-stu-id="87d96-263">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="87d96-264">Quando o SDK do .NET Core **3.0._200_** for instalado no mesmo computador, o SDK do .NET Core **3.0._101_** não será removido.</span><span class="sxs-lookup"><span data-stu-id="87d96-264">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="87d96-265">Para obter mais informações sobre controle de versão, consulte [Visão geral de como é o controle de versão no .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-265">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="87d96-266">Área de Trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="87d96-266">Windows desktop</span></span>

<span data-ttu-id="87d96-267">O .NET Core 3.0 dá suporte a aplicativos da Área de Trabalho do Windows usando o Windows Forms e o WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="87d96-267">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="87d96-268">Essas estruturas também oferecem suporte ao uso de controles modernos e no estilo Fluent da biblioteca XAML da interface do usuário do Windows (WinUI) por meio de [Ilhas XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="87d96-268">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="87d96-269">O componente Windows Desktop faz parte do SDK do .NET Core 3.0 do Windows.</span><span class="sxs-lookup"><span data-stu-id="87d96-269">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="87d96-270">É possível criar um novo aplicativo de WPF ou Windows Forms com os seguintes comandos `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="87d96-270">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="87d96-271">O Visual Studio 2019 adiciona modelos de **Novo Projeto** ao Windows Forms e WPF no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="87d96-271">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="87d96-272">Para obter mais informações sobre como portar um aplicativo existente do .NET Framework, consulte [Portar projetos do WPF](../../desktop-wpf/migration/convert-project-from-net-framework.md) e [Portar projetos do Windows Forms](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-272">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="87d96-273">WinForms com DPI alto</span><span class="sxs-lookup"><span data-stu-id="87d96-273">WinForms high DPI</span></span>

<span data-ttu-id="87d96-274">Aplicativos do Windows Forms do .NET Core podem definir o modo de DPI alto com <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87d96-274">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87d96-275">O método `SetHighDpiMode` define o modo de DPI alto correspondente, a menos que a configuração tenha sido definida por outros meios, tais como `App.Manifest` ou P/Invoke antes de `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="87d96-275">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="87d96-276">Os valores `highDpiMode` possíveis, conforme expressos pelo enum <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>, são:</span><span class="sxs-lookup"><span data-stu-id="87d96-276">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="87d96-277">Para obter mais informações sobre os modos de DPI alto, confira [Desenvolvimento de aplicativos de área de trabalho de DPI alto no Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="87d96-277">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="87d96-278">Criar componentes COM</span><span class="sxs-lookup"><span data-stu-id="87d96-278">Create COM components</span></span>

<span data-ttu-id="87d96-279">No Windows, agora você pode criar componentes gerenciados que podem ser chamados por COM.</span><span class="sxs-lookup"><span data-stu-id="87d96-279">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="87d96-280">Essa funcionalidade é fundamental para usar o .NET Core com modelos de suplemento do COM e também para fornecer paridade com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87d96-280">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="87d96-281">Ao contrário do .NET Framework em que o *mscoree. dll* foi usado como o servidor COM, o .NET Core adicionará uma dll de inicializador nativa ao diretório *bin* quando você compilar o componente COM.</span><span class="sxs-lookup"><span data-stu-id="87d96-281">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="87d96-282">Para obter um exemplo de como criar um componente COM e consumi-lo, veja a [demonstração de COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="87d96-282">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="87d96-283">Interoperabilidade nativa do Windows</span><span class="sxs-lookup"><span data-stu-id="87d96-283">Windows Native Interop</span></span>

<span data-ttu-id="87d96-284">O Windows oferece uma API nativa rica na forma de APIs C simples, COM e WinRT.</span><span class="sxs-lookup"><span data-stu-id="87d96-284">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="87d96-285">Embora o .NET Core dê suporte a **P/Invoke**, o .NET Core 3.0 adiciona a capacidade de **criar conjuntamente APIs COM** e **ativar APIs WinRT**.</span><span class="sxs-lookup"><span data-stu-id="87d96-285">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="87d96-286">Para obter um exemplo de código, consulte a [demonstração do Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="87d96-286">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="87d96-287">Implantação do MSIX</span><span class="sxs-lookup"><span data-stu-id="87d96-287">MSIX Deployment</span></span>

<span data-ttu-id="87d96-288">[MSIX](https://docs.microsoft.com/windows/msix/) é um novo formato de pacote de aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="87d96-288">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="87d96-289">Ele pode ser usado para implantar aplicativos da área de trabalho do .NET Core 3.0 no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="87d96-289">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="87d96-290">O [Projeto de Empacotamento de Aplicativos do Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponível no Visual Studio 2019, permite criar pacotes MSIX com aplicativos .NET Core [autossuficientes](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="87d96-290">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="87d96-291">O arquivo de projeto do .NET Core precisa especificar os runtimes compatíveis na propriedade `<RuntimeIdentifiers>`:</span><span class="sxs-lookup"><span data-stu-id="87d96-291">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="87d96-292">Aprimoramentos do Linux</span><span class="sxs-lookup"><span data-stu-id="87d96-292">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="87d96-293">SerialPort para Linux</span><span class="sxs-lookup"><span data-stu-id="87d96-293">SerialPort for Linux</span></span>

<span data-ttu-id="87d96-294">O .NET Core 3.0 fornece suporte básico para <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> no Linux.</span><span class="sxs-lookup"><span data-stu-id="87d96-294">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="87d96-295">Anteriormente, o .NET Core só dava suporte ao uso de `SerialPort` no Windows.</span><span class="sxs-lookup"><span data-stu-id="87d96-295">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="87d96-296">Para saber mais sobre o suporte limitado para a porta serial no Linux, confira o [Problema do GitHub nº 33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="87d96-296">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="87d96-297">Limites de memória do Docker e cgroup</span><span class="sxs-lookup"><span data-stu-id="87d96-297">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="87d96-298">A execução do .NET Core 3.0 no Linux com o Docker funciona melhor com limites de memória CGroup.</span><span class="sxs-lookup"><span data-stu-id="87d96-298">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="87d96-299">Executar um contêiner do Docker com limites de memória, tais como `docker run -m`, altera o comportamento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87d96-299">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="87d96-300">Tamanho de heap do GC (coletor de lixo) padrão: máximo de 20 MB ou 75% do limite de memória no contêiner.</span><span class="sxs-lookup"><span data-stu-id="87d96-300">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="87d96-301">O tamanho explícito pode ser definido como um número absoluto ou um percentual do limite de cgroup.</span><span class="sxs-lookup"><span data-stu-id="87d96-301">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="87d96-302">O tamanho mínimo do segmento reservado por heap de GC é de 16 MB.</span><span class="sxs-lookup"><span data-stu-id="87d96-302">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="87d96-303">Esse tamanho reduz o número de heaps que são criados em computadores.</span><span class="sxs-lookup"><span data-stu-id="87d96-303">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="87d96-304">Suporte de GPIO para o Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="87d96-304">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="87d96-305">Foram lançados dois pacotes para o NuGet que você pode usar para programação de GPIO:</span><span class="sxs-lookup"><span data-stu-id="87d96-305">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="87d96-306">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="87d96-306">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="87d96-307">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="87d96-307">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="87d96-308">Os pacotes GPIO incluem as APIs para dispositivos *GPIO*, *SPI*, *I2C* e *PWM*.</span><span class="sxs-lookup"><span data-stu-id="87d96-308">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="87d96-309">O pacote de associações de IoT inclui associações de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="87d96-309">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="87d96-310">Para obter mais informações, veja o [repositório GitHub de dispositivos](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="87d96-310">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="87d96-311">Suporte a ARM64 no Linux</span><span class="sxs-lookup"><span data-stu-id="87d96-311">ARM64 Linux support</span></span>

<span data-ttu-id="87d96-312">O .NET Core 3.0 adiciona suporte para ARM64 para Linux.</span><span class="sxs-lookup"><span data-stu-id="87d96-312">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="87d96-313">O principal caso de uso para ARM64 atualmente é em cenários de IoT.</span><span class="sxs-lookup"><span data-stu-id="87d96-313">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="87d96-314">Para obter mais informações, consulte [Status do .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="87d96-314">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="87d96-315">[Imagens do Docker para o .NET Core ARM64](https://hub.docker.com/r/microsoft/dotnet/) estão disponíveis para Alpine, Debian e Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="87d96-315">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="87d96-316">O suporte do Windows a **ARM64** ainda não está disponível.</span><span class="sxs-lookup"><span data-stu-id="87d96-316">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="87d96-317">Segurança</span><span class="sxs-lookup"><span data-stu-id="87d96-317">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="87d96-318">TLS 1.3 e OpenSSL 1.1.1 no Linux</span><span class="sxs-lookup"><span data-stu-id="87d96-318">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="87d96-319">O .NET Core agora faz proveito do [suporte a protocolo TLS 1.3 no OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/) quando esse protocolo está disponível em um determinado ambiente.</span><span class="sxs-lookup"><span data-stu-id="87d96-319">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="87d96-320">Com o TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="87d96-320">With TLS 1.3:</span></span>

- <span data-ttu-id="87d96-321">Tempos de conexão são aprimorados com um menor número de viagens de ida e volta necessárias entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="87d96-321">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="87d96-322">Segurança aprimorada devido à remoção de vários algoritmos criptográficos obsoletos e não seguros.</span><span class="sxs-lookup"><span data-stu-id="87d96-322">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="87d96-323">Quando disponíveis, o .NET Core 3.0 usa **OpenSSL 1.1.1**, **1.1.0** ou **1.0.2** em um sistema Linux.</span><span class="sxs-lookup"><span data-stu-id="87d96-323">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="87d96-324">Quando o **OpenSSL 1.1.1** está disponível, ambos os tipos <xref:System.Net.Security.SslStream?displayProperty=nameWithType> e <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> usarão o **protocolo TLS 1.3** (supondo que o cliente e o servidor deem suporte ao **protocolo TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="87d96-324">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87d96-325">Windows e macOS ainda não oferecem suporte a **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="87d96-325">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="87d96-326">O .NET Core 3.0 será compatível com **TLS 1.3** nesses sistemas operacionais quando o suporte for disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="87d96-326">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="87d96-327">O exemplo de C# 8.0 a seguir demonstra o .NET Core 3.0 no Ubuntu 18.10 conectando-se a <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="87d96-327">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="87d96-328">Cifras de criptografia</span><span class="sxs-lookup"><span data-stu-id="87d96-328">Cryptography ciphers</span></span>

<span data-ttu-id="87d96-329">O .NET 3.0 adiciona o suporte para as criptografias **AES-GCM** e **AES-CCM**, implementadas com <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> e <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="87d96-329">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="87d96-330">Esses algoritmos são ambos do tipo [AEAD (criptografia autenticada com os dados de associação)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="87d96-330">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="87d96-331">O código a seguir demonstra como usar criptografia `AesGcm` para criptografar e descriptografar dados aleatórios.</span><span class="sxs-lookup"><span data-stu-id="87d96-331">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="87d96-332">Importar/exportar chave de criptografia</span><span class="sxs-lookup"><span data-stu-id="87d96-332">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="87d96-333">O .NET Core 3.0 dá suporte à importação e exportação de chaves públicas e privadas assimétricas de formatos padrão.</span><span class="sxs-lookup"><span data-stu-id="87d96-333">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="87d96-334">Você não precisa usar um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="87d96-334">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="87d96-335">Todos os tipos principais, tais como *RSA*, *DSA*, *ECDsa* e *ECDiffieHellman*, dão suporte aos seguintes formatos:</span><span class="sxs-lookup"><span data-stu-id="87d96-335">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="87d96-336">**Chave pública**</span><span class="sxs-lookup"><span data-stu-id="87d96-336">**Public Key**</span></span>
  - <span data-ttu-id="87d96-337">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="87d96-337">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="87d96-338">**Chave privada**</span><span class="sxs-lookup"><span data-stu-id="87d96-338">**Private key**</span></span>
  - <span data-ttu-id="87d96-339">PKCS nº 8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="87d96-339">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="87d96-340">PKCS nº 8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="87d96-340">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="87d96-341">Chaves RSA também dão suporte a:</span><span class="sxs-lookup"><span data-stu-id="87d96-341">RSA keys also support:</span></span>

- <span data-ttu-id="87d96-342">**Chave pública**</span><span class="sxs-lookup"><span data-stu-id="87d96-342">**Public Key**</span></span>
  - <span data-ttu-id="87d96-343">PKCS nº 1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="87d96-343">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="87d96-344">**Chave privada**</span><span class="sxs-lookup"><span data-stu-id="87d96-344">**Private key**</span></span>
  - <span data-ttu-id="87d96-345">PKCS nº 1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="87d96-345">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="87d96-346">Os métodos de exportação produzem dados binários codificados em DER e os métodos de importação esperam o mesmo.</span><span class="sxs-lookup"><span data-stu-id="87d96-346">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="87d96-347">Se uma chave for armazenada no formato PEM compatível com texto, o chamador precisará decodificar o conteúdo em Base64 antes de chamar um método de importação.</span><span class="sxs-lookup"><span data-stu-id="87d96-347">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="87d96-348">Arquivos **PKCS nº 8** podem ser inspecionados com <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> e **arquivos PFX/PKCS nº 12** podem ser inspecionados com <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87d96-348">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87d96-349">Arquivos **PFX/PKCS nº 12** podem ser manipulados com <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87d96-349">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="87d96-350">Alterações da API do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="87d96-350">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="87d96-351">Intervalos e índices</span><span class="sxs-lookup"><span data-stu-id="87d96-351">Ranges and indices</span></span>

<span data-ttu-id="87d96-352">O novo tipo <xref:System.Index?displayProperty=nameWithType> pode ser usado para indexação.</span><span class="sxs-lookup"><span data-stu-id="87d96-352">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="87d96-353">É possível criar um a partir de um `int` que conta desde o início, ou com um operador `^` de prefixo (C#) que conta do final:</span><span class="sxs-lookup"><span data-stu-id="87d96-353">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="87d96-354">Há também o tipo <xref:System.Range?displayProperty=nameWithType>, que consiste em dois valores `Index` (um para o início e outro para o final) e pode ser escrito com uma expressão de intervalo `x..y` (C#).</span><span class="sxs-lookup"><span data-stu-id="87d96-354">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="87d96-355">Em seguida, você pode indexar com um `Range`, o que produz uma fatia:</span><span class="sxs-lookup"><span data-stu-id="87d96-355">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="87d96-356">Para obter mais informações, consulte o [tutorial de intervalos e índices](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-356">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="87d96-357">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="87d96-357">Async streams</span></span>

<span data-ttu-id="87d96-358">O tipo <xref:System.Collections.Generic.IAsyncEnumerable%601> é uma nova versão assíncrona de <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="87d96-358">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="87d96-359">A linguagem permite o uso de `await foreach` em `IAsyncEnumerable<T>` para consumir seus elementos e o uso de `yield return` neles para produzir elementos.</span><span class="sxs-lookup"><span data-stu-id="87d96-359">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="87d96-360">O exemplo a seguir demonstra a produção e o consumo de fluxos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="87d96-360">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="87d96-361">A instrução `foreach` é assíncrona e usa `yield return` para produzir um fluxo assíncrono para chamadores.</span><span class="sxs-lookup"><span data-stu-id="87d96-361">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="87d96-362">Esse padrão (usar `yield return`) é o modelo recomendado para a produção de fluxos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="87d96-362">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="87d96-363">Além de poder `await foreach`, você também pode criar iteradores assíncronos, por exemplo, um iterador que retorne um `IAsyncEnumerable/IAsyncEnumerator` em que é possível aplicar `await` e `yield`.</span><span class="sxs-lookup"><span data-stu-id="87d96-363">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="87d96-364">Para objetos que precisam ser descartados, você pode usar `IAsyncDisposable`, que vários tipos BCL implementam, como `Stream` e `Timer`.</span><span class="sxs-lookup"><span data-stu-id="87d96-364">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="87d96-365">Para obter mais informações, consulte o [tutorial de fluxos assíncronos](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-365">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="87d96-366">Ponto flutuante de IEEE</span><span class="sxs-lookup"><span data-stu-id="87d96-366">IEEE Floating-point</span></span>

<span data-ttu-id="87d96-367">APIs de ponto flutuante estão sendo atualizadas para entrar em conformidade com a [revisão IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="87d96-367">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="87d96-368">O objetivo dessas alterações é expor todas as operações **necessárias** e garantir que elas sejam compatíveis de forma comportamental com a especificação IEEE. Para obter mais informações sobre melhorias de ponto flutuante, consulte a postagem de [ponto flutuante e aprimoramentos de formatação no blog do .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="87d96-368">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="87d96-369">As correções de análise e formatação incluem:</span><span class="sxs-lookup"><span data-stu-id="87d96-369">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="87d96-370">Analisar e arredondar corretamente entradas de qualquer tamanho.</span><span class="sxs-lookup"><span data-stu-id="87d96-370">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="87d96-371">Analisar e formatar corretamente o zero negativo.</span><span class="sxs-lookup"><span data-stu-id="87d96-371">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="87d96-372">Analisar corretamente `Infinity` e `NaN`, fazendo uma verificação sem diferenciação de maiúsculas e minúsculas e permitindo um `+` precedente opcional onde aplicável.</span><span class="sxs-lookup"><span data-stu-id="87d96-372">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="87d96-373">Novas APIs <xref:System.Math?displayProperty=nameWithType> incluem:</span><span class="sxs-lookup"><span data-stu-id="87d96-373">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="87d96-374"><xref:System.Math.BitIncrement(System.Double)> e <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="87d96-374"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="87d96-375">Correspondem às operações `nextUp` e `nextDown` do IEEE.</span><span class="sxs-lookup"><span data-stu-id="87d96-375">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="87d96-376">Retornam o menor número de ponto flutuante que compara o valor maior ou menor que a entrada (respectivamente).</span><span class="sxs-lookup"><span data-stu-id="87d96-376">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="87d96-377">Por exemplo, `Math.BitIncrement(0.0)` retorna `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="87d96-377">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="87d96-378"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> e <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="87d96-378"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="87d96-379">Correspondem às operações `maxNumMag` e `minNumMag` do IEEE; retornam o valor maior ou menor em magnitude das duas entradas (respectivamente).</span><span class="sxs-lookup"><span data-stu-id="87d96-379">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="87d96-380">Por exemplo, `Math.MaxMagnitude(2.0, -3.0)` retorna `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="87d96-380">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="87d96-381">Corresponde à operação `logB` IEEE que retorna um valor integral, ele retorna o log de base 2 integral do parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="87d96-381">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="87d96-382">Esse método é praticamente o mesmo que `floor(log2(x))`, mas feito com o mínimo de erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="87d96-382">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="87d96-383">Corresponde à operação IEEE `scaleB` que usa um valor integral, ele retorna efetivamente `x * pow(2, n)`, mas é feito com o mínimo de erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="87d96-383">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="87d96-384">Corresponde à operação `log2` do IEEE; retorna o logaritmo de base 2.</span><span class="sxs-lookup"><span data-stu-id="87d96-384">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="87d96-385">Minimiza o erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="87d96-385">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="87d96-386">Corresponde à operação `fma` do IEEE; executa uma adição e multiplicação fundida.</span><span class="sxs-lookup"><span data-stu-id="87d96-386">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="87d96-387">Em outras palavras, realiza `(x * y) + z` como uma única operação, minimizando o erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="87d96-387">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="87d96-388">Um exemplo é `FusedMultiplyAdd(1e308, 2.0, -1e308)`, que retorna `1e308`.</span><span class="sxs-lookup"><span data-stu-id="87d96-388">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="87d96-389">O `(1e308 * 2.0) - 1e308` regular retorna `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="87d96-389">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="87d96-390">Corresponde à operação `copySign` do IEEE; retorna o valor de `x`, mas com o sinal de `y`.</span><span class="sxs-lookup"><span data-stu-id="87d96-390">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="87d96-391">Intrínsecos dependentes da plataforma .NET</span><span class="sxs-lookup"><span data-stu-id="87d96-391">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="87d96-392">Foram adicionadas APIs que permitem acesso a determinadas instruções da CPU orientadas a desempenho, como o **SIMD** ou conjuntos de **instruções de manipulação de bits**.</span><span class="sxs-lookup"><span data-stu-id="87d96-392">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="87d96-393">Essas instruções podem ajudar a obter melhorias significativas de desempenho em determinados cenários, tais como processamento de dados eficiente em paralelo.</span><span class="sxs-lookup"><span data-stu-id="87d96-393">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="87d96-394">Quando apropriado, as bibliotecas .NET começaram usando estas instruções para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="87d96-394">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="87d96-395">Para obter mais informações, consulte [Intrínsecos dependentes da plataforma .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-395">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="87d96-396">APIs de versão aprimoradas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="87d96-396">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="87d96-397">Começando com o .NET Core 3.0, as APIs de versão fornecidas com o .NET Core agora retornam as informações que você espera.</span><span class="sxs-lookup"><span data-stu-id="87d96-397">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="87d96-398">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="87d96-398">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="87d96-399">Alteração da falha.</span><span class="sxs-lookup"><span data-stu-id="87d96-399">Breaking change.</span></span> <span data-ttu-id="87d96-400">Isso é tecnicamente uma alteração da falha, porque o esquema de controle de versão foi alterado.</span><span class="sxs-lookup"><span data-stu-id="87d96-400">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="87d96-401">Suporte interno rápido a JSON</span><span class="sxs-lookup"><span data-stu-id="87d96-401">Fast built-in JSON support</span></span>

<span data-ttu-id="87d96-402">Os usuários do .NET confiam amplamente no [Newtonsoft. JSON](https://www.newtonsoft.com/json) e em outras bibliotecas JSON populares, que continuam a ser boas escolhas.</span><span class="sxs-lookup"><span data-stu-id="87d96-402">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="87d96-403">`Newtonsoft.Json` usa cadeias de caracteres .NET como seu tipo de dados base, que é UTF-16 nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="87d96-403">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="87d96-404">O novo suporte interno a JSON é alto desempenho, baixa alocação e funciona com texto JSON codificado em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="87d96-404">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="87d96-405">Para obter mais informações sobre o namespace e tipos de <xref:System.Text.Json>, consulte os seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="87d96-405">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="87d96-406">Serialização JSON no .NET-visão geral</span><span class="sxs-lookup"><span data-stu-id="87d96-406">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="87d96-407">[Como serializar e desserializar JSON no .net](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="87d96-407">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="87d96-408">Como migrar de Newtonsoft. JSON para System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="87d96-408">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="87d96-409">Compatibilidade com HTTP/2</span><span class="sxs-lookup"><span data-stu-id="87d96-409">HTTP/2 support</span></span>

<span data-ttu-id="87d96-410">O tipo <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> dá suporte ao protocolo HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="87d96-410">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="87d96-411">Se o HTTP/2 estiver habilitado, a versão do protocolo HTTP é negociada via TLS/ALPN, e o HTTP/2 é usado apenas se o servidor selecionar seu uso.</span><span class="sxs-lookup"><span data-stu-id="87d96-411">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="87d96-412">O protocolo padrão permanece HTTP/1.1, mas o HTTP/2 pode ser ativado de duas maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="87d96-412">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="87d96-413">Primeiro, você pode definir a mensagem de solicitação HTTP para usar HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="87d96-413">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="87d96-414">Segundo, você pode alterar <xref:System.Net.Http.HttpClient> para usar HTTP/2 por padrão:</span><span class="sxs-lookup"><span data-stu-id="87d96-414">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="87d96-415">Muitas vezes, quando você está desenvolvendo um aplicativo, quer usar uma conexão não criptografada.</span><span class="sxs-lookup"><span data-stu-id="87d96-415">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="87d96-416">Se você souber que o ponto de extremidade estará usando HTTP/2, poderá ativar conexões não criptografadas para HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="87d96-416">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="87d96-417">Você pode ativá-lo definindo a variável de ambiente `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` como `1` ou ativando-a no contexto do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="87d96-417">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="87d96-418">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="87d96-418">Next steps</span></span>

- [<span data-ttu-id="87d96-419">Examine as alterações significativas entre o .NET Core 2,2 e 3,0.</span><span class="sxs-lookup"><span data-stu-id="87d96-419">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="87d96-420">Examine as alterações significativas no .NET Core 3,0 para aplicativos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="87d96-420">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)
