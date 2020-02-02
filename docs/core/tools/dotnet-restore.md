---
title: Comando dotnet restore
description: Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: dc73b7b2482d25872be922e68103fb86067146f7
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920554"
---
# <a name="dotnet-restore"></a><span data-ttu-id="37b71-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="37b71-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="37b71-104">Name</span><span class="sxs-lookup"><span data-stu-id="37b71-104">Name</span></span>

<span data-ttu-id="37b71-105">`dotnet restore` – Restaura as dependências e as ferramentas de um projeto.</span><span class="sxs-lookup"><span data-stu-id="37b71-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37b71-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="37b71-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="37b71-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="37b71-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37b71-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="37b71-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="37b71-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="37b71-109">Description</span></span>

<span data-ttu-id="37b71-110">O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="37b71-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="37b71-111">Por padrão, a restauração das dependências e as ferramentas são executadas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="37b71-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="37b71-112">Para restaurar as dependências, o NuGet precisa dos feeds nos quais os pacotes estão localizados.</span><span class="sxs-lookup"><span data-stu-id="37b71-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="37b71-113">Os feeds são geralmente fornecidos por meio do arquivo de configuração *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="37b71-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="37b71-114">Um arquivo de configuração padrão é fornecido quando o SDK do .NET Core é instalado.</span><span class="sxs-lookup"><span data-stu-id="37b71-114">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="37b71-115">Especifique mais feeds criando seu próprio arquivo *nuget.config* no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="37b71-115">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="37b71-116">Você pode substituir os feeds *NuGet. config* pela opção `-s`.</span><span class="sxs-lookup"><span data-stu-id="37b71-116">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="37b71-117">Para dependências, especifique onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`.</span><span class="sxs-lookup"><span data-stu-id="37b71-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="37b71-118">Se não é especificado, o cache do pacote NuGet padrão é usado, o qual pode ser encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="37b71-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="37b71-119">Por exemplo, */home/user1* no Linux ou *C:\Usuário\user1* no Windows.</span><span class="sxs-lookup"><span data-stu-id="37b71-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="37b71-120">Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="37b71-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="37b71-121">Diferenças do nuget.config</span><span class="sxs-lookup"><span data-stu-id="37b71-121">nuget.config differences</span></span>

<span data-ttu-id="37b71-122">O comportamento do comando `dotnet restore` será afetado pelas configurações no arquivo *nuget.config*, se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="37b71-122">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="37b71-123">Por exemplo, a definição da `globalPackagesFolder` em *nuget.config* coloca os pacotes NuGet restaurados na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="37b71-123">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="37b71-124">Essa é uma alternativa para especificar a opção `--packages` no comando `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="37b71-124">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="37b71-125">Para obter mais informações, confira a [Referência do nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="37b71-125">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="37b71-126">Há três configurações específicas que são ignoradas por `dotnet restore`:</span><span class="sxs-lookup"><span data-stu-id="37b71-126">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="37b71-127">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="37b71-127">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="37b71-128">Os redirecionamentos de associação não funcionam com elementos `<PackageReference>` e o .NET Core só dá suporte a elementos `<PackageReference>` em pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="37b71-128">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="37b71-129">solution</span><span class="sxs-lookup"><span data-stu-id="37b71-129">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="37b71-130">Essa configuração é específica do Visual Studio e não se aplica ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="37b71-130">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="37b71-131">O .NET Core não usa um arquivo `packages.config` e, em vez disso, usa elementos `<PackageReference>` para pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="37b71-131">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="37b71-132">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="37b71-132">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="37b71-133">Essa configuração não é aplicável, pois o [NuGet ainda não dá suporte à verificação de multiplataforma](https://github.com/NuGet/Home/issues/7939) de pacotes confiáveis.</span><span class="sxs-lookup"><span data-stu-id="37b71-133">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="37b71-134">`dotnet restore` implícito</span><span class="sxs-lookup"><span data-stu-id="37b71-134">Implicit `dotnet restore`</span></span>

<span data-ttu-id="37b71-135">Começando com o .NET Core 2.0, se necessário, o `dotnet restore` será executado implicitamente quando você executar os comandos a seguir:</span><span class="sxs-lookup"><span data-stu-id="37b71-135">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="37b71-136">Na maioria dos casos, você não precisa usar o comando `dotnet restore` explicitamente.</span><span class="sxs-lookup"><span data-stu-id="37b71-136">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="37b71-137">Às vezes, pode ser inconveniente executar `dotnet restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="37b71-137">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="37b71-138">Por exemplo, alguns sistemas automatizados, como os sistemas de compilação, precisam chamar o `dotnet restore` explicitamente para controlar o momento em que a restauração ocorre para que possam controlar o uso de rede.</span><span class="sxs-lookup"><span data-stu-id="37b71-138">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="37b71-139">Para evitar que o `dotnet restore` seja executado implicitamente, use o sinalizador `--no-restore` com um desses comandos para desabilitar a restauração implícita.</span><span class="sxs-lookup"><span data-stu-id="37b71-139">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="37b71-140">Arguments</span><span class="sxs-lookup"><span data-stu-id="37b71-140">Arguments</span></span>

`ROOT`

<span data-ttu-id="37b71-141">Caminho opcional para o arquivo de projeto a ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="37b71-141">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="37b71-142">Opções</span><span class="sxs-lookup"><span data-stu-id="37b71-142">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="37b71-143">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="37b71-143">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="37b71-144">O arquivo de configuração NuGet (*nuget.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="37b71-144">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="37b71-145">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="37b71-145">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="37b71-146">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="37b71-146">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="37b71-147">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="37b71-147">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="37b71-148">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="37b71-148">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="37b71-149">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="37b71-149">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="37b71-150">Especifica para não armazenar os pacotes e solicitações HTTP em cache.</span><span class="sxs-lookup"><span data-stu-id="37b71-150">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="37b71-151">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="37b71-151">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="37b71-152">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="37b71-152">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="37b71-153">Especifica um runtime para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="37b71-153">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="37b71-154">Isso é usado para restaurar pacotes para runtimes não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="37b71-154">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="37b71-155">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="37b71-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="37b71-156">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="37b71-156">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="37b71-157">Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="37b71-157">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="37b71-158">Essa configuração substitui todas as fontes especificadas nos arquivos *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="37b71-158">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="37b71-159">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="37b71-159">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="37b71-160">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="37b71-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="37b71-161">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="37b71-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="37b71-162">O valor padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="37b71-162">Default value is `minimal`.</span></span>

`--interactive`

<span data-ttu-id="37b71-163">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="37b71-163">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="37b71-164">A partir do .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="37b71-164">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37b71-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="37b71-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="37b71-166">O arquivo de configuração NuGet (*nuget.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="37b71-166">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="37b71-167">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="37b71-167">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="37b71-168">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="37b71-168">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="37b71-169">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="37b71-169">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="37b71-170">Especifica para não armazenar os pacotes e solicitações HTTP em cache.</span><span class="sxs-lookup"><span data-stu-id="37b71-170">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="37b71-171">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="37b71-171">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="37b71-172">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="37b71-172">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="37b71-173">Especifica um runtime para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="37b71-173">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="37b71-174">Isso é usado para restaurar pacotes para runtimes não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="37b71-174">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="37b71-175">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="37b71-175">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="37b71-176">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="37b71-176">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="37b71-177">Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="37b71-177">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="37b71-178">Isso substitui todas as fontes especificadas nos arquivos *NuGet. config* , lendo efetivamente o arquivo *NuGet. config* como se o elemento de `<packageSource>` não estivesse lá.</span><span class="sxs-lookup"><span data-stu-id="37b71-178">This overrides all of the sources specified in the *nuget.config* files, effectively reading the *nuget.config* file as if the `<packageSource>` element was not there.</span></span> <span data-ttu-id="37b71-179">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="37b71-179">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="37b71-180">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="37b71-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="37b71-181">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="37b71-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="37b71-182">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="37b71-182">The default is `minimal`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="37b71-183">Exemplos</span><span class="sxs-lookup"><span data-stu-id="37b71-183">Examples</span></span>

<span data-ttu-id="37b71-184">Restaure as dependências e as ferramentas para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="37b71-184">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="37b71-185">Restaure as dependências e as ferramentas para o projeto `app1` encontrado no caminho fornecido:</span><span class="sxs-lookup"><span data-stu-id="37b71-185">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="37b71-186">Restaure as dependências e as ferramentas para o projeto no diretório atual usando o caminho de arquivo fornecido como a fonte:</span><span class="sxs-lookup"><span data-stu-id="37b71-186">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="37b71-187">Restaure as dependências e as ferramentas para o projeto no diretório atual usando os caminhos dos dois arquivos fornecidos como fontes:</span><span class="sxs-lookup"><span data-stu-id="37b71-187">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="37b71-188">Restaure as dependências e as ferramentas para o projeto no diretório atual mostrando a saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="37b71-188">Restore dependencies and tools for the project in the current directory showing detailed output:</span></span>

`dotnet restore --verbosity detailed`
