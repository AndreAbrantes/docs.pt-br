---
title: Matrizes – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715050"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="1a4c5-102">Matrizes (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1a4c5-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="1a4c5-103">Você pode armazenar diversas variáveis do mesmo tipo em uma estrutura de dados de matriz.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="1a4c5-104">Você pode declarar uma matriz especificando o tipo de seus elementos.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="1a4c5-105">Se você quiser que a matriz armazene elementos de qualquer tipo, você pode especificar `object` como seu tipo.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="1a4c5-106">No sistema de tipos unificado do C#, todos os tipos, predefinidos e definidos pelo usuário, tipos de referência e tipos de valor, herdam direta ou indiretamente de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="1a4c5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a4c5-107">Example</span></span>

<span data-ttu-id="1a4c5-108">O exemplo a seguir cria matrizes unidimensionais, multidimensionais e denteadas:</span><span class="sxs-lookup"><span data-stu-id="1a4c5-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="1a4c5-109">Visão geral da matriz</span><span class="sxs-lookup"><span data-stu-id="1a4c5-109">Array overview</span></span>

<span data-ttu-id="1a4c5-110">Uma matriz tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1a4c5-110">An array has the following properties:</span></span>

- <span data-ttu-id="1a4c5-111">Uma matriz pode ser [Unidimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) ou [Denteada](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="1a4c5-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="1a4c5-112">O número de dimensões e o tamanho de cada dimensão são estabelecidos quando a instância de matriz é criada.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="1a4c5-113">Esses valores não podem ser alterados durante o ciclo de vida da instância.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="1a4c5-114">Os valores padrão dos elementos de matriz numérica são definidos como zero, e os elementos de referência são definidos como null.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="1a4c5-115">Uma matriz denteada é uma matriz de matrizes e, portanto, seus elementos são tipos de referência e são inicializados para `null`.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="1a4c5-116">As matrizes são indexadas por zero: uma matriz com elementos `n` é indexada de `0` para `n-1`.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="1a4c5-117">Os elementos de matriz podem ser de qualquer tipo, inclusive um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="1a4c5-118">Os tipos de matriz são [tipos de referência](../../language-reference/keywords/reference-types.md) derivados do tipo base abstrato <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="1a4c5-119">Como esse tipo implementa <xref:System.Collections.IEnumerable> e <xref:System.Collections.Generic.IEnumerable%601>, você pode usar a iteração [foreach](../../language-reference/keywords/foreach-in.md) em todas as matrizes em c#.</span><span class="sxs-lookup"><span data-stu-id="1a4c5-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1a4c5-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1a4c5-120">Related sections</span></span>

- [<span data-ttu-id="1a4c5-121">Matrizes como objetos</span><span class="sxs-lookup"><span data-stu-id="1a4c5-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="1a4c5-122">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="1a4c5-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="1a4c5-123">Passando matrizes como argumentos</span><span class="sxs-lookup"><span data-stu-id="1a4c5-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="1a4c5-124">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1a4c5-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1a4c5-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="1a4c5-125">See also</span></span>

- [<span data-ttu-id="1a4c5-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1a4c5-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1a4c5-127">Coleções</span><span class="sxs-lookup"><span data-stu-id="1a4c5-127">Collections</span></span>](../concepts/collections.md)
