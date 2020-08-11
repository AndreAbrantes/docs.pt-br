---
title: Pacote de distribuição do .NET Core
description: Aprenda a empacotar, nomear e controlar a versão do .NET Core para distribuição.
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 3324a6a151fc6dc46a8f13ea17c89da99d108d82
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062880"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="76bef-103">Pacote de distribuição do .NET Core</span><span class="sxs-lookup"><span data-stu-id="76bef-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="76bef-104">À medida que o .NET Core fica disponível em mais plataformas, é muito útil saber como empacotar, nomear e controlar a versão dele.</span><span class="sxs-lookup"><span data-stu-id="76bef-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="76bef-105">Dessa forma, os mantenedores do pacote podem ajudar a garantir uma experiência consistente, independentemente de onde os usuários escolhem executar o .NET.</span><span class="sxs-lookup"><span data-stu-id="76bef-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="76bef-106">Este artigo é útil para usuários que estão:</span><span class="sxs-lookup"><span data-stu-id="76bef-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="76bef-107">Tentando criar o .NET Core com base na origem.</span><span class="sxs-lookup"><span data-stu-id="76bef-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="76bef-108">Querendo fazer alterações à CLI do .NET Core que poderiam afetar o layout resultante ou os pacotes produzidos.</span><span class="sxs-lookup"><span data-stu-id="76bef-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="76bef-109">Layout de disco</span><span class="sxs-lookup"><span data-stu-id="76bef-109">Disk layout</span></span>

<span data-ttu-id="76bef-110">Quando instalado, o .NET Core consiste em vários componentes que são dispostos da seguinte maneira no sistema de arquivos:</span><span class="sxs-lookup"><span data-stu-id="76bef-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="76bef-111">(1) **dotnet** O host (também conhecido como o "muxer") tem duas funções distintas: ativar um runtime para iniciar um aplicativo e ativar um SDK para enviar comandos a ele.</span><span class="sxs-lookup"><span data-stu-id="76bef-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="76bef-112">O host é um executável nativo (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="76bef-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="76bef-113">Embora haja um único host, a maioria dos outros componentes está em diretórios com controle de versão (2,3,5,6).</span><span class="sxs-lookup"><span data-stu-id="76bef-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="76bef-114">Isso significa que várias versões podem estar presentes no sistema, pois são instaladas lado a lado.</span><span class="sxs-lookup"><span data-stu-id="76bef-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="76bef-115">(2) \*\*host/fxr/ \<fxr version> \*\* contém a lógica de resolução de estrutura usada pelo host.</span><span class="sxs-lookup"><span data-stu-id="76bef-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="76bef-116">O host usa o hostfxr mais recente instalado.</span><span class="sxs-lookup"><span data-stu-id="76bef-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="76bef-117">O hostfxr é responsável por selecionar o runtime apropriado ao executar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76bef-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="76bef-118">Por exemplo, um aplicativo criado para o runtime do .NET Core 2.0.0 usa o 2.0.5 quando ele está disponível.</span><span class="sxs-lookup"><span data-stu-id="76bef-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="76bef-119">Da mesma forma, o hostfxr seleciona o SDK adequado durante o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="76bef-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="76bef-120">(3) \*\*SDK/ \<sdk version> \*\* o SDK (também conhecido como "ferramentas") é um conjunto de ferramentas gerenciadas que são usadas para escrever e criar bibliotecas e aplicativos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76bef-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="76bef-121">O SDK inclui o CLI do .NET Core, os compiladores de linguagens gerenciadas, o MSBuild e tarefas e destinos de compilação associados, NuGet, novos modelos de projeto e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="76bef-121">The SDK includes the .NET Core CLI, the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="76bef-122">(4) **sdk/NuGetFallbackFolder** contém um cache de pacotes do NuGet usados por um SDK durante a operação de restauração, como ao executar `dotnet restore` ou `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="76bef-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="76bef-123">Esta pasta é usada somente antes do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="76bef-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="76bef-124">Ele não pode ser compilado da origem, pois contém ativos binários pré-criados do `nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="76bef-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="76bef-125">A pasta **compartilhada** contém estruturas.</span><span class="sxs-lookup"><span data-stu-id="76bef-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="76bef-126">Uma estrutura compartilhada fornece um conjunto de bibliotecas em um local central para que elas possam ser usadas por aplicativos diferentes.</span><span class="sxs-lookup"><span data-stu-id="76bef-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="76bef-127">(5) \*\*compartilhado/Microsoft. NetCore. app/ \<runtime version> \*\* esta estrutura contém o tempo de execução do .NET Core e oferece suporte a bibliotecas gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="76bef-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="76bef-128">(6) \*\*Shared/Microsoft. AspNetCore. { App, All}/ \<aspnetcore version> \*\* contém as bibliotecas de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="76bef-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="76bef-129">As bibliotecas em `Microsoft.AspNetCore.App` são desenvolvidas e têm suporte como parte do projeto .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76bef-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="76bef-130">As bibliotecas em `Microsoft.AspNetCore.All` são um superconjunto que também contém bibliotecas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="76bef-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="76bef-131">(7) \*\*Shared/Microsoft. desktop. app/ \<desktop app version> \*\* contém as bibliotecas da área de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="76bef-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="76bef-132">Isso não está incluído em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="76bef-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="76bef-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** são a licença do .NET Core e licenças de bibliotecas de terceiros usadas no .NET Core, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="76bef-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="76bef-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` é a página de manual do dotnet.</span><span class="sxs-lookup"><span data-stu-id="76bef-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="76bef-135">`dotnet` é um symlink ao host(1) dotnet.</span><span class="sxs-lookup"><span data-stu-id="76bef-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="76bef-136">Esses arquivos são instalados em locais bem conhecidos para a integração do sistema.</span><span class="sxs-lookup"><span data-stu-id="76bef-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="76bef-137">(11, 12) **Microsoft. NetCore. app. ref, Microsoft. AspNetCore. app. ref** descreve a API de uma `x.y` versão do .net Core e ASP.NET Core respectivamente.</span><span class="sxs-lookup"><span data-stu-id="76bef-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="76bef-138">Esses pacotes são usados durante a compilação para essas versões de destino.</span><span class="sxs-lookup"><span data-stu-id="76bef-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="76bef-139">(13) \*\*Microsoft. NetCore. app. host. \<rid> \*\*</span><span class="sxs-lookup"><span data-stu-id="76bef-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span></span> <span data-ttu-id="76bef-140">contém um binário nativo para plataforma `rid` .</span><span class="sxs-lookup"><span data-stu-id="76bef-140">contains a native binary for platform `rid`.</span></span> <span data-ttu-id="76bef-141">Esse binário é um modelo ao compilar um aplicativo .NET Core em um binário nativo para essa plataforma.</span><span class="sxs-lookup"><span data-stu-id="76bef-141">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="76bef-142">(14) **Microsoft. WindowsDesktop. app. ref** descreve a API da `x.y` versão dos aplicativos da área de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="76bef-142">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="76bef-143">Esses arquivos são usados durante a compilação para esse destino.</span><span class="sxs-lookup"><span data-stu-id="76bef-143">These files are used when compiling for that target.</span></span> <span data-ttu-id="76bef-144">Isso não é fornecido em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="76bef-144">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="76bef-145">(15) **netstandard. library. ref** descreve a API do netpadrão `x.y` .</span><span class="sxs-lookup"><span data-stu-id="76bef-145">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="76bef-146">Esses arquivos são usados durante a compilação para esse destino.</span><span class="sxs-lookup"><span data-stu-id="76bef-146">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="76bef-147">(16) **/etc/dotnet/install_location** é um arquivo que contém o caminho completo para `{dotnet_root}` .</span><span class="sxs-lookup"><span data-stu-id="76bef-147">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="76bef-148">O caminho pode terminar com uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="76bef-148">The path may end with a newline.</span></span> <span data-ttu-id="76bef-149">Não é necessário adicionar esse arquivo quando a raiz é `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="76bef-149">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="76bef-150">(17) **modelos** contém os modelos usados pelo SDK.</span><span class="sxs-lookup"><span data-stu-id="76bef-150">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="76bef-151">Por exemplo, `dotnet new` localiza modelos de projeto aqui.</span><span class="sxs-lookup"><span data-stu-id="76bef-151">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="76bef-152">As pastas marcadas com `(*)` são usadas por vários pacotes.</span><span class="sxs-lookup"><span data-stu-id="76bef-152">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="76bef-153">Alguns formatos de pacote (por exemplo, `rpm` ) exigem um tratamento especial dessas pastas.</span><span class="sxs-lookup"><span data-stu-id="76bef-153">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="76bef-154">O mantenedor do pacote deve cuidar disso.</span><span class="sxs-lookup"><span data-stu-id="76bef-154">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="76bef-155">Pacotes recomendados</span><span class="sxs-lookup"><span data-stu-id="76bef-155">Recommended packages</span></span>

<span data-ttu-id="76bef-156">O controle de versão do .NET Core é baseado nos números de versão `[major].[minor]` do componente de runtime.</span><span class="sxs-lookup"><span data-stu-id="76bef-156">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="76bef-157">A versão do SDK usa o mesmo `[major].[minor]` e tem um `[patch]` independente que combina as semânticas de recurso e de patch para o SDK.</span><span class="sxs-lookup"><span data-stu-id="76bef-157">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="76bef-158">Por exemplo: SDK versão 2.2.302 é a segunda versão de patch da terceira versão de recurso do SDK que dá suporte ao tempo de execução 2,2.</span><span class="sxs-lookup"><span data-stu-id="76bef-158">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="76bef-159">Para obter mais informações sobre como o controle de versão funciona, veja [Visão geral do controle de versão do .NET Core](./versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="76bef-159">For more information about how versioning works, see [.NET Core versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="76bef-160">Alguns pacotes incluem parte do número de versão no nome deles.</span><span class="sxs-lookup"><span data-stu-id="76bef-160">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="76bef-161">Isso permite que você instale uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="76bef-161">This allows you to install a specific version.</span></span>
<span data-ttu-id="76bef-162">O restante da versão não está incluído no nome da versão.</span><span class="sxs-lookup"><span data-stu-id="76bef-162">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="76bef-163">Isso permite ao gerenciador de pacotes de SO atualize os pacotes (por exemplo, instalando automaticamente correções de segurança).</span><span class="sxs-lookup"><span data-stu-id="76bef-163">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="76bef-164">Gerenciadores de pacotes com suporte são específicos do Linux.</span><span class="sxs-lookup"><span data-stu-id="76bef-164">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="76bef-165">Veja a seguir uma lista dos pacotes recomendados:</span><span class="sxs-lookup"><span data-stu-id="76bef-165">The following lists the recommended packages:</span></span>

- <span data-ttu-id="76bef-166">`dotnet-sdk-[major].[minor]`-Instala o SDK mais recente para tempo de execução específico</span><span class="sxs-lookup"><span data-stu-id="76bef-166">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="76bef-167">**Versão:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="76bef-167">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="76bef-168">**Exemplo:** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="76bef-168">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="76bef-169">**Contém:** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="76bef-169">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="76bef-170">**Dependências:** `dotnet-runtime-[major].[minor]` ,,,,, `aspnetcore-runtime-[major].[minor]` `dotnet-targeting-pack-[major].[minor]` `aspnetcore-targeting-pack-[major].[minor]` `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` `dotnet-apphost-pack-[major].[minor]` ,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="76bef-170">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="76bef-171">`aspnetcore-runtime-[major].[minor]`-Instala um tempo de execução de ASP.NET Core específico</span><span class="sxs-lookup"><span data-stu-id="76bef-171">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="76bef-172">**Versão:**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="76bef-172">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="76bef-173">**Exemplo:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="76bef-173">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="76bef-174">**Contém:** (6)</span><span class="sxs-lookup"><span data-stu-id="76bef-174">**Contains:** (6)</span></span>
  - <span data-ttu-id="76bef-175">**Dependências:**`dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="76bef-175">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="76bef-176">`dotnet-runtime-deps-[major].[minor]`_(Opcional)_ -instala as dependências para executar aplicativos independentes</span><span class="sxs-lookup"><span data-stu-id="76bef-176">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="76bef-177">**Versão:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="76bef-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="76bef-178">**Exemplo:** dotnet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="76bef-178">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="76bef-179">**Dependências:** _dependências específicas de distribuição_</span><span class="sxs-lookup"><span data-stu-id="76bef-179">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="76bef-180">`dotnet-runtime-[major].[minor]`-Instala um tempo de execução específico</span><span class="sxs-lookup"><span data-stu-id="76bef-180">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="76bef-181">**Versão:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="76bef-181">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="76bef-182">**Exemplo:** dotnet-tempo de execução-2,1</span><span class="sxs-lookup"><span data-stu-id="76bef-182">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="76bef-183">**Contém:** (5)</span><span class="sxs-lookup"><span data-stu-id="76bef-183">**Contains:** (5)</span></span>
  - <span data-ttu-id="76bef-184">**Dependências:** `dotnet-hostfxr-[major].[minor]` ,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="76bef-184">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="76bef-185">`dotnet-hostfxr-[major].[minor]`-dependência</span><span class="sxs-lookup"><span data-stu-id="76bef-185">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="76bef-186">**Versão:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="76bef-186">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="76bef-187">**Exemplo:** dotnet-hostfxr-3,0</span><span class="sxs-lookup"><span data-stu-id="76bef-187">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="76bef-188">**Contém:** (2)</span><span class="sxs-lookup"><span data-stu-id="76bef-188">**Contains:** (2)</span></span>
  - <span data-ttu-id="76bef-189">**Dependências:**`dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="76bef-189">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="76bef-190">`dotnet-host`-dependência</span><span class="sxs-lookup"><span data-stu-id="76bef-190">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="76bef-191">**Versão:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="76bef-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="76bef-192">**Exemplo:** dotnet-host</span><span class="sxs-lookup"><span data-stu-id="76bef-192">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="76bef-193">**Contém:** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="76bef-193">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="76bef-194">`dotnet-apphost-pack-[major].[minor]`-dependência</span><span class="sxs-lookup"><span data-stu-id="76bef-194">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="76bef-195">**Versão:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="76bef-195">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="76bef-196">**Contém:** (13)</span><span class="sxs-lookup"><span data-stu-id="76bef-196">**Contains:** (13)</span></span>

- <span data-ttu-id="76bef-197">`dotnet-targeting-pack-[major].[minor]`-Permite direcionar um tempo de execução não mais recente</span><span class="sxs-lookup"><span data-stu-id="76bef-197">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="76bef-198">**Versão:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="76bef-198">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="76bef-199">**Contém:** (12)</span><span class="sxs-lookup"><span data-stu-id="76bef-199">**Contains:** (12)</span></span>

- <span data-ttu-id="76bef-200">`aspnetcore-targeting-pack-[major].[minor]`-Permite direcionar um tempo de execução não mais recente</span><span class="sxs-lookup"><span data-stu-id="76bef-200">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="76bef-201">**Versão:**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="76bef-201">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="76bef-202">**Contém:** (11)</span><span class="sxs-lookup"><span data-stu-id="76bef-202">**Contains:** (11)</span></span>

- <span data-ttu-id="76bef-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`-Permite direcionar uma versão do netstandard</span><span class="sxs-lookup"><span data-stu-id="76bef-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="76bef-204">**Versão:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="76bef-204">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="76bef-205">**Contém:** (15)</span><span class="sxs-lookup"><span data-stu-id="76bef-205">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="76bef-206">**Versão:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="76bef-206">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="76bef-207">**Contém:** (15)</span><span class="sxs-lookup"><span data-stu-id="76bef-207">**Contains:** (15)</span></span>

<span data-ttu-id="76bef-208">O `dotnet-runtime-deps-[major].[minor]` requer a compreensão das _dependências específicas do distribuição_.</span><span class="sxs-lookup"><span data-stu-id="76bef-208">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="76bef-209">Como o sistema de compilação distribuição pode ser capaz de derivar isso automaticamente, o pacote é opcional; nesse caso, essas dependências são adicionadas diretamente ao `dotnet-runtime-[major].[minor]` pacote.</span><span class="sxs-lookup"><span data-stu-id="76bef-209">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="76bef-210">Quando o conteúdo do pacote está sob uma pasta com versão, o nome do pacote `[major].[minor]` corresponde ao nome da pasta com versão.</span><span class="sxs-lookup"><span data-stu-id="76bef-210">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="76bef-211">Para todos os pacotes, exceto o `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` , isso também corresponde à versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76bef-211">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="76bef-212">As dependências entre os pacotes devem usar um requisito _de versão igual ou maior que_ .</span><span class="sxs-lookup"><span data-stu-id="76bef-212">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="76bef-213">Por exemplo, `dotnet-sdk-2.2:2.2.401` requer `aspnetcore-runtime-2.2 >= 2.2.6` .</span><span class="sxs-lookup"><span data-stu-id="76bef-213">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="76bef-214">Isso possibilita que o usuário Atualize sua instalação por meio de um pacote raiz (por exemplo, `dnf update dotnet-sdk-2.2` ).</span><span class="sxs-lookup"><span data-stu-id="76bef-214">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="76bef-215">A maioria das distribuições exigem que todos os artefatos sejam compilados da origem.</span><span class="sxs-lookup"><span data-stu-id="76bef-215">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="76bef-216">Isso tem algum impacto nos pacotes:</span><span class="sxs-lookup"><span data-stu-id="76bef-216">This has some impact on the packages:</span></span>

- <span data-ttu-id="76bef-217">As bibliotecas de terceiros em `shared/Microsoft.AspNetCore.All` não podem ser criadas facilmente usando o código-fonte.</span><span class="sxs-lookup"><span data-stu-id="76bef-217">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="76bef-218">Portanto, essa pasta é omitida do pacote `aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="76bef-218">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="76bef-219">O `NuGetFallbackFolder` é populado usando os artefatos binários de `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="76bef-219">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="76bef-220">Ele deve permanecer vazio.</span><span class="sxs-lookup"><span data-stu-id="76bef-220">It should remain empty.</span></span>

<span data-ttu-id="76bef-221">Vários pacotes `dotnet-sdk` podem fornecer os mesmos arquivos para o `NuGetFallbackFolder`.</span><span class="sxs-lookup"><span data-stu-id="76bef-221">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="76bef-222">Para evitar problemas com o gerenciador de pacotes, esses arquivos devem ser idênticos (soma de verificação, data de modificação e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="76bef-222">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="76bef-223">Compilando pacotes</span><span class="sxs-lookup"><span data-stu-id="76bef-223">Building packages</span></span>

<span data-ttu-id="76bef-224">O repositório [dotnet/source-build](https://github.com/dotnet/source-build) fornece instruções sobre como compilar um tarball de origem do SDK do .NET Core e todos os seus componentes.</span><span class="sxs-lookup"><span data-stu-id="76bef-224">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="76bef-225">A saída do repositório de build de origem corresponde o layout descrito na primeira seção deste artigo.</span><span class="sxs-lookup"><span data-stu-id="76bef-225">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
