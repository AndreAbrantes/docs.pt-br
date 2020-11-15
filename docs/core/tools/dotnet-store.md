---
title: Comando dotnet store
description: O comando "dotnet store" armazena os assemblies especificados no repositório de pacotes de runtime.
ms.date: 02/14/2020
ms.openlocfilehash: 8efb11c6bf648bc7787d5627e02b180abb8a0afd
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634331"
---
# <a name="dotnet-store"></a><span data-ttu-id="afcb9-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="afcb9-103">dotnet store</span></span>

<span data-ttu-id="afcb9-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="afcb9-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="afcb9-105">Name</span><span class="sxs-lookup"><span data-stu-id="afcb9-105">Name</span></span>

<span data-ttu-id="afcb9-106">`dotnet store` – Armazena os assemblies especificados no [repositório de pacotes de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="afcb9-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="afcb9-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="afcb9-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest <PATH_TO_MANIFEST_FILE>
    -f|--framework <FRAMEWORK_VERSION> -r|--runtime <RUNTIME_IDENTIFIER>
    [--framework-version <FRAMEWORK_VERSION>] [--output <OUTPUT_DIRECTORY>]
    [--skip-optimization] [--skip-symbols] [-v|--verbosity <LEVEL>]
    [--working-dir <WORKING_DIRECTORY>]

dotnet store -h|--help
```

## <a name="description"></a><span data-ttu-id="afcb9-108">Description</span><span class="sxs-lookup"><span data-stu-id="afcb9-108">Description</span></span>

<span data-ttu-id="afcb9-109">`dotnet store` armazena os assemblies especificados no [repositório de pacotes de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="afcb9-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="afcb9-110">Por padrão, os assemblies são otimizados para a estrutura e o runtime de destino.</span><span class="sxs-lookup"><span data-stu-id="afcb9-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="afcb9-111">Para obter mais informações, consulte o tópico [repositório de pacotes de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="afcb9-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="afcb9-112">Opções obrigatórias</span><span class="sxs-lookup"><span data-stu-id="afcb9-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="afcb9-113">Especifica a [estrutura de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="afcb9-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="afcb9-114">A estrutura de destino deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="afcb9-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="afcb9-115">O *arquivo de manifesto do repositório de pacotes* é um arquivo XML que contém a lista de pacotes a serem armazenados.</span><span class="sxs-lookup"><span data-stu-id="afcb9-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="afcb9-116">O formato do arquivo de manifesto é compatível com o formato de projeto de estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="afcb9-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="afcb9-117">Portanto, um arquivo de projeto que referencia os pacotes desejados pode ser usado com a opção `-m|--manifest` para armazenar assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="afcb9-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="afcb9-118">Para especificar vários arquivos de manifesto, repita a opção e o caminho para cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="afcb9-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="afcb9-119">Por exemplo: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="afcb9-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="afcb9-120">O [identificador de tempo de execução](../rid-catalog.md) para o destino.</span><span class="sxs-lookup"><span data-stu-id="afcb9-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="afcb9-121">Opções opcionais</span><span class="sxs-lookup"><span data-stu-id="afcb9-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="afcb9-122">Especifica a versão do SDK do .NET.</span><span class="sxs-lookup"><span data-stu-id="afcb9-122">Specifies the .NET SDK version.</span></span> <span data-ttu-id="afcb9-123">Essa opção permite que você selecione uma versão da estrutura específica, além da estrutura especificada pela opção `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="afcb9-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="afcb9-124">Mostra informações de ajuda.</span><span class="sxs-lookup"><span data-stu-id="afcb9-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="afcb9-125">Especifica o caminho para o repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="afcb9-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="afcb9-126">Se não for especificado, o padrão será o subdiretório de *armazenamento* do diretório de instalação .net do perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="afcb9-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="afcb9-127">Ignora a fase de otimização.</span><span class="sxs-lookup"><span data-stu-id="afcb9-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="afcb9-128">Ignora a geração de símbolos.</span><span class="sxs-lookup"><span data-stu-id="afcb9-128">Skips symbol generation.</span></span> <span data-ttu-id="afcb9-129">No momento, só é possível gerar símbolos no Windows e no Linux.</span><span class="sxs-lookup"><span data-stu-id="afcb9-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="afcb9-130">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="afcb9-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="afcb9-131">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="afcb9-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="afcb9-132">O diretório de trabalho usado pelo comando.</span><span class="sxs-lookup"><span data-stu-id="afcb9-132">The working directory used by the command.</span></span> <span data-ttu-id="afcb9-133">Se não for especificado, ele usará o subdiretório *obj* do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="afcb9-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="afcb9-134">Exemplos</span><span class="sxs-lookup"><span data-stu-id="afcb9-134">Examples</span></span>

- <span data-ttu-id="afcb9-135">Armazene os pacotes especificados no arquivo de projeto *packages.csproj* para .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="afcb9-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="afcb9-136">Armazene os pacotes especificados no *packages.csproj* sem otimização:</span><span class="sxs-lookup"><span data-stu-id="afcb9-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="afcb9-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afcb9-137">See also</span></span>

- [<span data-ttu-id="afcb9-138">Repositório de pacotes de runtime</span><span class="sxs-lookup"><span data-stu-id="afcb9-138">Runtime package store</span></span>](../deploying/runtime-store.md)
