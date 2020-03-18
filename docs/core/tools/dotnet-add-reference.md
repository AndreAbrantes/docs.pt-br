---
title: dotnet adicionar comando de referência
description: O comando dotnet add reference fornece uma opção conveniente para adicionar referências projeto a projeto.
ms.date: 02/14/2020
ms.openlocfilehash: 84ea25e94efc8d84aebfeccf62c30a64551c5019
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503793"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="dc1ba-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="dc1ba-103">dotnet add reference</span></span>

<span data-ttu-id="dc1ba-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="dc1ba-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="dc1ba-105">Nome</span><span class="sxs-lookup"><span data-stu-id="dc1ba-105">Name</span></span>

<span data-ttu-id="dc1ba-106">`dotnet add reference` – Adiciona as referências P2P (projeto a projeto).</span><span class="sxs-lookup"><span data-stu-id="dc1ba-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dc1ba-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="dc1ba-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="dc1ba-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc1ba-108">Description</span></span>

<span data-ttu-id="dc1ba-109">O comando `dotnet add reference` fornece uma opção conveniente para adicionar referências de projeto a um projeto.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="dc1ba-110">Depois de executar o comando, os elementos `<ProjectReference>` são adicionados ao arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="dc1ba-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="dc1ba-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="dc1ba-112">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-112">Specifies the project file.</span></span> <span data-ttu-id="dc1ba-113">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="dc1ba-114">Referências P2P (projeto a projeto) a serem adicionadas.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="dc1ba-115">Especifique um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-115">Specify one or more projects.</span></span> <span data-ttu-id="dc1ba-116">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com sistemas baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="dc1ba-117">Opções</span><span class="sxs-lookup"><span data-stu-id="dc1ba-117">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="dc1ba-118">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-118">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dc1ba-119">Adiciona referências de projeto somente ao direcionar uma [estrutura](../../standard/frameworks.md)específica .</span><span class="sxs-lookup"><span data-stu-id="dc1ba-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`--interactive`**

  <span data-ttu-id="dc1ba-120">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="dc1ba-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="dc1ba-121">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="dc1ba-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="dc1ba-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dc1ba-122">Examples</span></span>

- <span data-ttu-id="dc1ba-123">Adicionar referência de projeto:</span><span class="sxs-lookup"><span data-stu-id="dc1ba-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="dc1ba-124">Adicionar várias referências de projeto ao projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="dc1ba-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="dc1ba-125">Adicionar várias referências de projeto usando um padrão de recurso de curinga no Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="dc1ba-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
