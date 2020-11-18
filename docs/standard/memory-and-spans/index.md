---
title: Memória e extensão
ms.date: 10/03/2018
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: 4b0464cc81cf0908a907f8305ea4e35b716c18fb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830656"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="b18ce-102">Tipos relacionados a memória e extensão</span><span class="sxs-lookup"><span data-stu-id="b18ce-102">Memory- and span-related types</span></span>

<span data-ttu-id="b18ce-103">A partir do .NET Core 2,1, o .NET inclui vários tipos inter-relacionados que representam uma região contígua e fortemente tipada de memória arbitrária.</span><span class="sxs-lookup"><span data-stu-id="b18ce-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly typed region of arbitrary memory.</span></span> <span data-ttu-id="b18ce-104">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="b18ce-104">These include:</span></span>

- <span data-ttu-id="b18ce-105"><xref:System.Span%601?displayProperty=nameWithType>, um tipo usado para acessar uma região contígua da memória.</span><span class="sxs-lookup"><span data-stu-id="b18ce-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="b18ce-106">Uma instância <xref:System.Span%601> pode ser sustentada por uma matriz do tipo `T`, uma <xref:System.String>, um buffer alocado com [stackalloc](../../csharp/language-reference/operators/stackalloc.md) ou um ponteiro para memória não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b18ce-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="b18ce-107">Como ela deve ser alocada na pilha, tem várias restrições.</span><span class="sxs-lookup"><span data-stu-id="b18ce-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="b18ce-108">Por exemplo, um campo em uma classe não pode ser do tipo <xref:System.Span%601>, nem a extensão pode ser usada em operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="b18ce-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="b18ce-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, uma versão imutável da estrutura <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="b18ce-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="b18ce-110"><xref:System.Memory%601?displayProperty=nameWithType>, uma região contígua da memória alocada no heap gerenciado, em vez da pilha.</span><span class="sxs-lookup"><span data-stu-id="b18ce-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="b18ce-111">Uma instância <xref:System.Memory%601> pode ser sustentada por uma matriz do tipo `T` ou uma <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b18ce-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="b18ce-112">Como ela pode ser armazenada no heap gerenciado, <xref:System.Memory%601> não tem nenhuma das limitações de <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="b18ce-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="b18ce-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, uma versão imutável da estrutura <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="b18ce-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="b18ce-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, que aloca blocos fortemente tipados de memória de um pool de memória para um proprietário.</span><span class="sxs-lookup"><span data-stu-id="b18ce-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="b18ce-115">Instâncias <xref:System.Buffers.IMemoryOwner%601> podem ser alocadas do pool chamando <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> e lançadas de volta ao pool chamando <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b18ce-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="b18ce-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, que representa o proprietário de um bloco de memória e controla o gerenciamento do tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="b18ce-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="b18ce-117"><xref:System.Buffers.MemoryManager%601>, uma classe base abstrata que pode ser usada para substituir a implementação de <xref:System.Memory%601>, de modo que <xref:System.Memory%601> possa ser sustentada por tipos adicionais, como identificadores seguros.</span><span class="sxs-lookup"><span data-stu-id="b18ce-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="b18ce-118"><xref:System.Buffers.MemoryManager%601> destina-se a cenários avançados.</span><span class="sxs-lookup"><span data-stu-id="b18ce-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="b18ce-119"><xref:System.ArraySegment%601>, um wrapper para determinado número de elementos de matriz, começando em um índice específico.</span><span class="sxs-lookup"><span data-stu-id="b18ce-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="b18ce-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, uma coleção de métodos de extensão para converter cadeias de caracteres, matrizes e segmentos de matriz para blocos <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="b18ce-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="b18ce-121">Para estruturas anteriores, <xref:System.Span%601> e <xref:System.Memory%601> estão disponíveis no [pacote do System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).</span><span class="sxs-lookup"><span data-stu-id="b18ce-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="b18ce-122">Para obter mais informações, consulte o namespace de <xref:System.Buffers?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b18ce-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="b18ce-123">Como trabalhando com memória e extensão</span><span class="sxs-lookup"><span data-stu-id="b18ce-123">Working with memory and span</span></span>

<span data-ttu-id="b18ce-124">Como os tipos relacionados a memória e extensão normalmente são usados para armazenar dados em um pipeline de processamento, é importante que os desenvolvedores sigam um conjunto de melhores práticas ao usar <xref:System.Span%601>, <xref:System.Memory%601> e tipos relacionados.</span><span class="sxs-lookup"><span data-stu-id="b18ce-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="b18ce-125">Essas práticas recomendadas são documentadas em [memória \<T> e abrangem as \<T> diretrizes de uso](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="b18ce-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b18ce-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="b18ce-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
