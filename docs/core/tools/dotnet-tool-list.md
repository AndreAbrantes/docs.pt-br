---
title: Comando dotnet tool list
description: O comando dotnet da lista de ferramentas lista as ferramentas .NET que estão instaladas em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: d884f2c41834dd9704de3a8ca15417ba368fde4b
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634279"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="d8441-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="d8441-103">dotnet tool list</span></span>

<span data-ttu-id="d8441-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d8441-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d8441-105">Name</span><span class="sxs-lookup"><span data-stu-id="d8441-105">Name</span></span>

<span data-ttu-id="d8441-106">`dotnet tool list` -Lista todas as [ferramentas .net](global-tools.md) do tipo especificado atualmente instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="d8441-106">`dotnet tool list` - Lists all [.NET tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d8441-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d8441-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="d8441-108">Description</span><span class="sxs-lookup"><span data-stu-id="d8441-108">Description</span></span>

<span data-ttu-id="d8441-109">O `dotnet tool list` comando fornece uma maneira de listar todas as ferramentas globais, de caminho de ferramenta ou locais do .net instaladas em seu computador.</span><span class="sxs-lookup"><span data-stu-id="d8441-109">The `dotnet tool list` command provides a way for you to list all .NET global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="d8441-110">O comando lista o nome do pacote, a versão instalada e o comando da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d8441-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="d8441-111">Para usar o comando, especifique um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="d8441-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="d8441-112">Para listar as ferramentas globais instaladas no local padrão, use a `--global` opção</span><span class="sxs-lookup"><span data-stu-id="d8441-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="d8441-113">Para listar as ferramentas globais instaladas em um local personalizado, use a `--tool-path` opção.</span><span class="sxs-lookup"><span data-stu-id="d8441-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="d8441-114">Para listar as ferramentas locais, use a `--local` opção ou omita as `--global` `--tool-path` Opções, e `--local` .</span><span class="sxs-lookup"><span data-stu-id="d8441-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="d8441-115">**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="d8441-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="d8441-116">Opções</span><span class="sxs-lookup"><span data-stu-id="d8441-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="d8441-117">Lista as ferramentas globais em todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="d8441-117">Lists user-wide global tools.</span></span> <span data-ttu-id="d8441-118">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="d8441-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="d8441-119">Omitir `--global` e `--tool-path` listar as ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="d8441-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d8441-120">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="d8441-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="d8441-121">Lista as ferramentas locais para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d8441-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="d8441-122">Não pode ser combinado com `--global` as `--tool-path` Opções ou.</span><span class="sxs-lookup"><span data-stu-id="d8441-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="d8441-123">Omitir `--global` e `--tool-path` listar as ferramentas locais, mesmo se `--local` não for especificado.</span><span class="sxs-lookup"><span data-stu-id="d8441-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="d8441-124">Especifica um local personalizado onde encontrar ferramentas globais.</span><span class="sxs-lookup"><span data-stu-id="d8441-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="d8441-125">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="d8441-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="d8441-126">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="d8441-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="d8441-127">Omitir `--global` e `--tool-path` listar as ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="d8441-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="d8441-128">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d8441-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="d8441-129">Lista todas as ferramentas globais instaladas por todo o usuário em seu computador (perfil de usuário atual).</span><span class="sxs-lookup"><span data-stu-id="d8441-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="d8441-130">Lista as ferramentas globais de um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="d8441-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="d8441-131">Lista as ferramentas globais de um diretório específico do Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="d8441-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="d8441-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="d8441-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="d8441-133">Lista todas as ferramentas locais disponíveis no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d8441-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8441-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8441-134">See also</span></span>

- [<span data-ttu-id="d8441-135">Ferramentas .NET</span><span class="sxs-lookup"><span data-stu-id="d8441-135">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="d8441-136">Tutorial: instalar e usar uma ferramenta global do .NET usando a CLI do .NET</span><span class="sxs-lookup"><span data-stu-id="d8441-136">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="d8441-137">Tutorial: instalar e usar uma ferramenta local do .NET usando a CLI do .NET</span><span class="sxs-lookup"><span data-stu-id="d8441-137">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
