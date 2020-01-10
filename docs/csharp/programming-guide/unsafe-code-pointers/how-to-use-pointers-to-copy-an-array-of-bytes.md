---
title: Como usar ponteiros para copiar uma matriz de bytes- C# guia de programação
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698450"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="f7648-102">Como usar ponteiros para copiar uma matriz de bytes (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="f7648-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="f7648-103">O exemplo a seguir usa ponteiros para copiar bytes de uma matriz para outra.</span><span class="sxs-lookup"><span data-stu-id="f7648-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="f7648-104">Este exemplo usa a palavra-chave [não seguro](../../language-reference/keywords/unsafe.md), que permite que você use ponteiros no método `Copy`.</span><span class="sxs-lookup"><span data-stu-id="f7648-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="f7648-105">A instrução [fixo](../../language-reference/keywords/fixed-statement.md) é usada para declarar ponteiros para as matrizes de origem e de destino.</span><span class="sxs-lookup"><span data-stu-id="f7648-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="f7648-106">A instrução `fixed`*fixa* o local das matrizes de origem e de destino na memória para que elas não sejam movidas pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f7648-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="f7648-107">Os blocos de memória para as matrizes não serão fixado quando o bloco `fixed` for concluído.</span><span class="sxs-lookup"><span data-stu-id="f7648-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="f7648-108">Como o método `Copy` neste exemplo usa a palavra-chave `unsafe`, ele precisa ser compilado com a opção do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f7648-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="f7648-109">Este exemplo acessa os elementos das duas matrizes usando índices em vez de um segundo ponteiro não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f7648-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="f7648-110">A declaração dos ponteiros `pSource` e `pTarget` fixa as matrizes.</span><span class="sxs-lookup"><span data-stu-id="f7648-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="f7648-111">Esse recurso está disponível começando com o C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="f7648-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="f7648-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7648-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="f7648-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="f7648-113">See also</span></span>

- [<span data-ttu-id="f7648-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f7648-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f7648-115">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="f7648-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="f7648-116">-unsafe (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="f7648-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="f7648-117">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="f7648-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
