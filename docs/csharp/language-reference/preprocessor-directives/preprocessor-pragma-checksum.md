---
description: '#pragma checksum – Referência de C#'
title: '#pragma checksum – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 60c491000337fd50da217e97054e86faccb2e7d7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137975"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="e8891-103">#pragma checksum (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e8891-103">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="e8891-104">Gera somas de verificação para os arquivos de origem para ajudar na depuração de páginas do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e8891-104">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8891-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8891-105">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8891-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8891-106">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="e8891-107">O nome do arquivo que exige o monitoramento de alterações ou atualizações.</span><span class="sxs-lookup"><span data-stu-id="e8891-107">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="e8891-108">O GUID (identificador global exclusivo) do algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="e8891-108">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="e8891-109">A cadeia de caracteres de dígitos hexadecimais que representa os bytes da soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="e8891-109">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="e8891-110">Deve ser um número par de dígitos hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="e8891-110">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="e8891-111">Um número ímpar de dígitos resulta em um aviso em tempo de compilação e a diretiva é ignorada.</span><span class="sxs-lookup"><span data-stu-id="e8891-111">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8891-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8891-112">Remarks</span></span>  
 <span data-ttu-id="e8891-113">O depurador do Visual Studio usa uma soma de verificação para certificar-se de sempre encontrar a fonte correta.</span><span class="sxs-lookup"><span data-stu-id="e8891-113">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="e8891-114">O compilador calcula a soma de verificação para um arquivo de origem e, em seguida, emite a saída no arquivo PDB (banco de dados do programa).</span><span class="sxs-lookup"><span data-stu-id="e8891-114">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="e8891-115">Em seguida, o depurador usa o PDB para comparar com a soma de verificação que ele calcula para o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="e8891-115">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="e8891-116">Essa solução não funciona para projetos do ASP.NET, porque é a soma de verificação calculada é para o arquivo de origem gerado e não para o arquivo .aspx.</span><span class="sxs-lookup"><span data-stu-id="e8891-116">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="e8891-117">Para resolver esse problema, a `#pragma checksum` fornece suporte à soma de verificação para páginas do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e8891-117">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="e8891-118">Quando você cria um projeto do ASP.NET em Visual C#, o arquivo de origem gerado contém uma soma de verificação para o arquivo .aspx, do qual a fonte é gerada.</span><span class="sxs-lookup"><span data-stu-id="e8891-118">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="e8891-119">Então, o compilador grava essas informações no arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="e8891-119">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="e8891-120">Se o compilador não encontrar uma diretiva `#pragma checksum` no arquivo, ele calcula a soma de verificação e grava o valor no arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="e8891-120">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8891-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8891-121">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8891-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8891-122">See also</span></span>

- [<span data-ttu-id="e8891-123">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="e8891-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e8891-124">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="e8891-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e8891-125">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="e8891-125">C# Preprocessor Directives</span></span>](./index.md)
