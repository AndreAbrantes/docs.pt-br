---
title: -pathmap (opções do compilador C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606632"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="de81d-102">-pathmap (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="de81d-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="de81d-103">A opção do compilador **-pathmap** especifica como mapear caminhos físicos para os nomes de caminho de origem emitidos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="de81d-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="de81d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de81d-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="de81d-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="de81d-105">Arguments</span></span>

 <span data-ttu-id="de81d-106">`path1` O caminho completo para os arquivos de origem no ambiente atual</span><span class="sxs-lookup"><span data-stu-id="de81d-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="de81d-107">`sourcePath1` O caminho de origem substituído por `path1` em arquivos de saída.</span><span class="sxs-lookup"><span data-stu-id="de81d-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="de81d-108">Para especificar vários caminhos de origem mapeados, separe-os com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="de81d-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="de81d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="de81d-109">Remarks</span></span>

<span data-ttu-id="de81d-110">O compilador grava o caminho de origem em sua saída pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="de81d-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="de81d-111">O caminho de origem é substituído por um argumento quando o <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> é aplicado a um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="de81d-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="de81d-112">O caminho de origem é inserido em um arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="de81d-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="de81d-113">O caminho do arquivo PDB é inserido em um arquivo PE (executável portátil).</span><span class="sxs-lookup"><span data-stu-id="de81d-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="de81d-114">Essa opção mapeia cada caminho físico no computador em que o compilador é executado para um caminho correspondente que deve ser gravado nos arquivos de saída.</span><span class="sxs-lookup"><span data-stu-id="de81d-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="de81d-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de81d-115">Example</span></span>

<span data-ttu-id="de81d-116">Compilar `t.cs` no diretório **C:\\work\\tests** e mapear esse diretório para **\publish** na saída:</span><span class="sxs-lookup"><span data-stu-id="de81d-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="de81d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="de81d-117">See also</span></span>

- [<span data-ttu-id="de81d-118">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="de81d-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="de81d-119">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="de81d-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
