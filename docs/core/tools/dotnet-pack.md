---
title: Comando dotnet pack
description: O comando dotnet pack cria pacotes NuGet para seu projeto .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503649"
---
# <a name="dotnet-pack"></a><span data-ttu-id="db21d-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="db21d-103">dotnet pack</span></span>

<span data-ttu-id="db21d-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="db21d-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="db21d-105">Nome</span><span class="sxs-lookup"><span data-stu-id="db21d-105">Name</span></span>

<span data-ttu-id="db21d-106">`dotnet pack` – Empacota o código em um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="db21d-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="db21d-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="db21d-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="db21d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="db21d-108">Description</span></span>

<span data-ttu-id="db21d-109">O comando `dotnet pack` compila o projeto e cria pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="db21d-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="db21d-110">O resultado deste comando é um pacote NuGet (ou seja, um arquivo *.nupkg).*</span><span class="sxs-lookup"><span data-stu-id="db21d-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="db21d-111">Se você quiser gerar um pacote que contenha os símbolos de depuração, você tem duas opções disponíveis:</span><span class="sxs-lookup"><span data-stu-id="db21d-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="db21d-112">`--include-symbols`- cria o pacote de símbolos.</span><span class="sxs-lookup"><span data-stu-id="db21d-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="db21d-113">`--include-source`- ele cria o pacote `src` de símbolos com uma pasta dentro contendo os arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="db21d-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="db21d-114">As dependências do NuGet do projeto empacotado são adicionadas ao arquivo *.nuspec* para que possam ser resolvidas apropriadamente quando o pacote for instalado.</span><span class="sxs-lookup"><span data-stu-id="db21d-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="db21d-115">As referências de projeto a projeto não são empacotadas dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="db21d-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="db21d-116">No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="db21d-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="db21d-117">Por padrão, `dotnet pack` compila primeiro o projeto.</span><span class="sxs-lookup"><span data-stu-id="db21d-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="db21d-118">Se você quiser evitar esse comportamento, passe a opção `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="db21d-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="db21d-119">Com frequência, essa opção é útil em cenários de build de CI (integração contínua) nos quais você sabe que o código foi compilado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="db21d-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="db21d-120">Você pode fornecer as propriedades de MSBuild para o comando `dotnet pack` para o processo de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="db21d-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="db21d-121">Para obter mais informações, consulte [Propriedades de metadados do NuGet](csproj.md#nuget-metadata-properties) e a [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="db21d-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="db21d-122">A seção [Exemplos](#examples) mostra como usar a opção -p do MSBuild para alguns cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="db21d-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="db21d-123">Projetos da Web não são empacotáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="db21d-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="db21d-124">Para substituir o comportamento padrão, adicione a seguinte propriedade ao seu arquivo *.csproj*:</span><span class="sxs-lookup"><span data-stu-id="db21d-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="db21d-125">Argumentos</span><span class="sxs-lookup"><span data-stu-id="db21d-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="db21d-126">O projeto ou solução para embalar.</span><span class="sxs-lookup"><span data-stu-id="db21d-126">The project or solution to pack.</span></span> <span data-ttu-id="db21d-127">Ou é um caminho para um [arquivo csproj,](csproj.md)um arquivo de solução ou para um diretório.</span><span class="sxs-lookup"><span data-stu-id="db21d-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="db21d-128">Se não for especificado, o comando pesquisa o diretório atual para um arquivo de projeto ou solução.</span><span class="sxs-lookup"><span data-stu-id="db21d-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="db21d-129">Opções</span><span class="sxs-lookup"><span data-stu-id="db21d-129">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="db21d-130">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="db21d-130">Defines the build configuration.</span></span> <span data-ttu-id="db21d-131">O padrão para `Debug`a maioria dos projetos é, mas você pode substituir as configurações de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="db21d-131">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="db21d-132">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="db21d-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="db21d-133">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="db21d-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="db21d-134">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="db21d-134">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="db21d-135">Inclui os símbolos de depuração pacotes NuGet, além dos pacotes NuGet regulares no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="db21d-135">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="db21d-136">Os arquivos de fontes `src` estão incluídos na pasta dentro do pacote de símbolos.</span><span class="sxs-lookup"><span data-stu-id="db21d-136">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="db21d-137">Inclui os símbolos de depuração pacotes NuGet, além dos pacotes NuGet regulares no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="db21d-137">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="db21d-138">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="db21d-138">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="db21d-139">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="db21d-139">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="db21d-140">Não compila o projeto antes do empacotamento.</span><span class="sxs-lookup"><span data-stu-id="db21d-140">Doesn't build the project before packing.</span></span> <span data-ttu-id="db21d-141">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="db21d-141">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="db21d-142">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="db21d-142">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="db21d-143">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="db21d-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="db21d-144">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="db21d-144">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="db21d-145">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="db21d-145">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="db21d-146">Coloca os pacotes compilados no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="db21d-146">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="db21d-147">Especifica o runtime de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="db21d-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="db21d-148">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="db21d-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="db21d-149">Define o sinalizador operacional no pacote.</span><span class="sxs-lookup"><span data-stu-id="db21d-149">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="db21d-150">Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="db21d-150">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="db21d-151">Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.</span><span class="sxs-lookup"><span data-stu-id="db21d-151">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="db21d-152">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="db21d-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="db21d-153">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="db21d-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="db21d-154">Exemplos</span><span class="sxs-lookup"><span data-stu-id="db21d-154">Examples</span></span>

- <span data-ttu-id="db21d-155">Empacota o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="db21d-155">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="db21d-156">Empacote o projeto `app1`:</span><span class="sxs-lookup"><span data-stu-id="db21d-156">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="db21d-157">Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta`nupkgs`:</span><span class="sxs-lookup"><span data-stu-id="db21d-157">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="db21d-158">Empacote o projeto no diretório atual da pasta `nupkgs` e ignora a etapa de compilação:</span><span class="sxs-lookup"><span data-stu-id="db21d-158">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="db21d-159">Com o sufixo da versão do projeto configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*, empacote o projeto atual e atualize a versão do pacote resultante com o sufixo especificado:</span><span class="sxs-lookup"><span data-stu-id="db21d-159">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="db21d-160">Defina a versão do pacote como `2.1.0` com a propriedade MSBuild `PackageVersion`:</span><span class="sxs-lookup"><span data-stu-id="db21d-160">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="db21d-161">Empacote o projeto para uma determinada [estrutura de destino](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="db21d-161">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="db21d-162">Embale o projeto e use um tempo de execução específico (Windows 10) para a operação de restauração:</span><span class="sxs-lookup"><span data-stu-id="db21d-162">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="db21d-163">Empacotar o projeto, usando um [arquivo .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="db21d-163">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
