---
title: Comando dotnet store
description: O comando "dotnet store" armazena os assemblies especificados no repositório de pacotes de runtime.
ms.date: 05/29/2018
ms.openlocfilehash: cc5b4b6160ba296e1529f006c15e238746d9e08a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733057"
---
# <a name="dotnet-store"></a><span data-ttu-id="7994e-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="7994e-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="7994e-104">Name</span><span class="sxs-lookup"><span data-stu-id="7994e-104">Name</span></span>

<span data-ttu-id="7994e-105">`dotnet store` – Armazena os assemblies especificados no [repositório de pacotes de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="7994e-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="7994e-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7994e-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="7994e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7994e-107">Description</span></span>

<span data-ttu-id="7994e-108">`dotnet store` armazena os assemblies especificados no [repositório de pacotes de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="7994e-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="7994e-109">Por padrão, os assemblies são otimizados para a estrutura e o runtime de destino.</span><span class="sxs-lookup"><span data-stu-id="7994e-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="7994e-110">Para obter mais informações, consulte o tópico [repositório de pacotes de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="7994e-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="7994e-111">Opções obrigatórias</span><span class="sxs-lookup"><span data-stu-id="7994e-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7994e-112">Especifica a [estrutura de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7994e-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="7994e-113">O *arquivo de manifesto do repositório de pacotes* é um arquivo XML que contém a lista de pacotes a serem armazenados.</span><span class="sxs-lookup"><span data-stu-id="7994e-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="7994e-114">O formato do arquivo de manifesto é compatível com o formato de projeto de estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="7994e-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="7994e-115">Portanto, um arquivo de projeto que referencia os pacotes desejados pode ser usado com a opção `-m|--manifest` para armazenar assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="7994e-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="7994e-116">Para especificar vários arquivos de manifesto, repita a opção e o caminho para cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="7994e-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="7994e-117">Por exemplo: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="7994e-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="7994e-118">O [identificador do runtime](../rid-catalog.md) a ser usado como destino.</span><span class="sxs-lookup"><span data-stu-id="7994e-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="7994e-119">Opções opcionais</span><span class="sxs-lookup"><span data-stu-id="7994e-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="7994e-120">Especifica a versão do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7994e-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="7994e-121">Essa opção permite que você selecione uma versão da estrutura específica, além da estrutura especificada pela opção `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="7994e-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="7994e-122">Mostra informações de ajuda.</span><span class="sxs-lookup"><span data-stu-id="7994e-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7994e-123">Especifica o caminho para o repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="7994e-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="7994e-124">Se não for especificado, o padrão será o subdiretório *repositório* do diretório de instalação do .NET Core do perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="7994e-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="7994e-125">Ignora a fase de otimização.</span><span class="sxs-lookup"><span data-stu-id="7994e-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="7994e-126">Ignora a geração de símbolos.</span><span class="sxs-lookup"><span data-stu-id="7994e-126">Skips symbol generation.</span></span> <span data-ttu-id="7994e-127">No momento, só é possível gerar símbolos no Windows e no Linux.</span><span class="sxs-lookup"><span data-stu-id="7994e-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7994e-128">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="7994e-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7994e-129">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7994e-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="7994e-130">O diretório de trabalho usado pelo comando.</span><span class="sxs-lookup"><span data-stu-id="7994e-130">The working directory used by the command.</span></span> <span data-ttu-id="7994e-131">Se não for especificado, ele usará o subdiretório *obj* do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="7994e-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="7994e-132">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7994e-132">Examples</span></span>

<span data-ttu-id="7994e-133">Armazene os pacotes especificados no arquivo de projeto *packages.csproj* para .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="7994e-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="7994e-134">Armazene os pacotes especificados no *packages.csproj* sem otimização:</span><span class="sxs-lookup"><span data-stu-id="7994e-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="7994e-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="7994e-135">See also</span></span>

- [<span data-ttu-id="7994e-136">Repositório de pacote de runtime</span><span class="sxs-lookup"><span data-stu-id="7994e-136">Runtime package store</span></span>](../deploying/runtime-store.md)
