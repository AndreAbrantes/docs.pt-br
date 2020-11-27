---
title: 'Alteração significativa: complexidade do LINQ OrderBy. primeiro {OrDefault} aumentou'
description: Saiba mais sobre a alteração significativa do .NET 5,0 em bibliotecas principais do .NET em que a implementação de OrderBy. First foi alterada.
ms.date: 11/01/2020
ms.openlocfilehash: 3c4f8fd0bb2051c3e1ac14eab091be11f10f88b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760410"
---
# <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="585c8-103">Complexidade do LINQ OrderBy. primeiro {OrDefault} aumentou</span><span class="sxs-lookup"><span data-stu-id="585c8-103">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="585c8-104">A implementação de <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> e <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> foi alterada, resultando em maior complexidade para a operação.</span><span class="sxs-lookup"><span data-stu-id="585c8-104">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

## <a name="change-description"></a><span data-ttu-id="585c8-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="585c8-105">Change description</span></span>

<span data-ttu-id="585c8-106">No .NET Core 1. x-3. x, chamando <xref:System.Linq.Enumerable.OrderBy%2A> ou <xref:System.Linq.Enumerable.OrderByDescending%2A> seguido por <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> opera com a `O(N)` complexidade.</span><span class="sxs-lookup"><span data-stu-id="585c8-106">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="585c8-107">Como apenas o primeiro elemento (ou padrão) é necessário, apenas uma enumeração é necessária para encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="585c8-107">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="585c8-108">No entanto, o predicado que é fornecido para <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> é invocado exatamente `N` vezes, em que `N` é o comprimento da sequência.</span><span class="sxs-lookup"><span data-stu-id="585c8-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="585c8-109">No .NET 5,0 e versões posteriores, [foi feita uma alteração](https://github.com/dotnet/runtime/pull/36643) que chamava <xref:System.Linq.Enumerable.OrderBy%2A> ou <xref:System.Linq.Enumerable.OrderByDescending%2A> seguiu por <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> opera com `O(N log N)` complexidade em vez de `O(N)` complexidade.</span><span class="sxs-lookup"><span data-stu-id="585c8-109">In .NET 5.0 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="585c8-110">No entanto, o predicado que é fornecido para <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> pode ser invocado *menos* de `N` vezes, o que é mais importante para o desempenho geral.</span><span class="sxs-lookup"><span data-stu-id="585c8-110">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="585c8-111">Essa alteração corresponde à implementação e à complexidade da operação no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="585c8-111">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="585c8-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="585c8-112">Reason for change</span></span>

<span data-ttu-id="585c8-113">O benefício de invocar o predicado menos vezes supera uma complexidade geral mais baixa, de modo que a implementação introduzida no .NET Core 1,0 foi revertida.</span><span class="sxs-lookup"><span data-stu-id="585c8-113">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="585c8-114">Para obter mais informações, consulte [este problema de dotnet/tempo de execução](https://github.com/dotnet/runtime/issues/31554).</span><span class="sxs-lookup"><span data-stu-id="585c8-114">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="585c8-115">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="585c8-115">Version introduced</span></span>

<span data-ttu-id="585c8-116">5.0</span><span class="sxs-lookup"><span data-stu-id="585c8-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="585c8-117">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="585c8-117">Recommended action</span></span>

<span data-ttu-id="585c8-118">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="585c8-118">No action is required on the developer's part.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="585c8-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="585c8-119">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->