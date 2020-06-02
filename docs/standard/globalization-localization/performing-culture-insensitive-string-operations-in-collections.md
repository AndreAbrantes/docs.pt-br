---
title: Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
ms.openlocfilehash: 377fa58e052e8f8e35a546c21fe2b4fb00cb103d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288258"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="edcf6-102">Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções</span><span class="sxs-lookup"><span data-stu-id="edcf6-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="edcf6-103">Há classes e membros no namespace <xref:System.Collections> que fornecem, por padrão, o comportamento sensível à cultura.</span><span class="sxs-lookup"><span data-stu-id="edcf6-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="edcf6-104">Os construtores sem parâmetros para as classes <xref:System.Collections.CaseInsensitiveComparer> e <xref:System.Collections.CaseInsensitiveHashCodeProvider> inicializam uma nova instância usando a propriedade <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="edcf6-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="edcf6-105">Todas as sobrecargas do método <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> criam uma nova instância da classe <xref:System.Collections.Hashtable> usando a propriedade `Thread.CurrentCulture` por padrão.</span><span class="sxs-lookup"><span data-stu-id="edcf6-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="edcf6-106">As sobrecargas do método <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> executam, por padrão, classificações sensíveis à cultura usando `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="edcf6-107">A classificação e a pesquisa em uma <xref:System.Collections.SortedList> podem ser afetadas por `Thread.CurrentCulture`, quando as cadeias de caracteres são usadas como as chaves.</span><span class="sxs-lookup"><span data-stu-id="edcf6-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="edcf6-108">Siga as recomendações de uso fornecidas nesta seção para obter os resultados insensíveis à cultura dessas classes e métodos no namespace `Collections`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="edcf6-109">Passar <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> para um método de comparação realiza uma comparação que não diferencia a cultura.</span><span class="sxs-lookup"><span data-stu-id="edcf6-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="edcf6-110">No entanto, não causa uma comparação não linguística, por exemplo, para caminhos de arquivos, chaves do Registro e variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="edcf6-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="edcf6-111">Também não oferece suporte a decisões de segurança com base no resultado da comparação.</span><span class="sxs-lookup"><span data-stu-id="edcf6-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="edcf6-112">Para obter uma comparação não linguística ou suporte para decisões de segurança com base no resultado, o aplicativo deve usar um método de comparação que aceite um valor <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="edcf6-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="edcf6-113">Assim, o aplicativo deve passar <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="edcf6-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="edcf6-114">Usar as classes CaseInsensitiveHashCodeProvider e CaseInsensitiveComparer</span><span class="sxs-lookup"><span data-stu-id="edcf6-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="edcf6-115">Os construtores sem parâmetros `CaseInsensitiveHashCodeProvider` e `CaseInsensitiveComparer` inicializam uma nova instância da classe usando o `Thread.CurrentCulture`, resultando no comportamento sensível à cultura.</span><span class="sxs-lookup"><span data-stu-id="edcf6-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="edcf6-116">O exemplo de código a seguir demonstra o construtor para um `Hashtable` que é sensível à cultura, pois usa os construtores sem parâmetros para `CaseInsensitiveHashCodeProvider` e `CaseInsensitiveComparer`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="edcf6-117">Se você quiser criar um `Hashtable` insensível à cultura usando as classes `CaseInsensitiveComparer` e `CaseInsensitiveHashCodeProvider`, inicialize novas instâncias dessas classes usando os construtores que aceitam um parâmetro `culture`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="edcf6-118">Para o parâmetro `culture`, especifique <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="edcf6-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="edcf6-119">O exemplo de código a seguir demonstra o construtor para um `Hashtable` insensível à cultura.</span><span class="sxs-lookup"><span data-stu-id="edcf6-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="edcf6-120">Usar o método CollectionsUtil.CreateCaseInsensitiveHashTable</span><span class="sxs-lookup"><span data-stu-id="edcf6-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="edcf6-121">O método `CollectionsUtil.CreateCaseInsensitiveHashTable` é um atalho útil para criar uma nova instância da classe `Hashtable` que não diferencia maiúsculas de minúsculas das cadeias de caractere.</span><span class="sxs-lookup"><span data-stu-id="edcf6-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="edcf6-122">No entanto, todas as sobrecargas do método `CollectionsUtil.CreateCaseInsensitiveHashTable` são sensíveis à cultura, pois usam a propriedade `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="edcf6-123">Não é possível criar um `Hashtable` insensível à cultura usando esse método.</span><span class="sxs-lookup"><span data-stu-id="edcf6-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="edcf6-124">Para criar um `Hashtable` insensível à cultura, use o construtor `Hashtable` que aceita um parâmetro `culture`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="edcf6-125">Para o parâmetro `culture`, especifique `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="edcf6-126">O exemplo de código a seguir demonstra o construtor para um `Hashtable` insensível à cultura.</span><span class="sxs-lookup"><span data-stu-id="edcf6-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="edcf6-127">Usar a classe SortedList</span><span class="sxs-lookup"><span data-stu-id="edcf6-127">Using the SortedList Class</span></span>

<span data-ttu-id="edcf6-128">Um `SortedList` representa uma coleção de pares chave/valor que são classificados pelas chaves e são acessíveis por chave e por índice.</span><span class="sxs-lookup"><span data-stu-id="edcf6-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="edcf6-129">Quando você usa um `SortedList` no qual as cadeias de caracteres são as chaves, a classificação e a pesquisa podem ser afetadas pela propriedade `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="edcf6-130">Para obter o comportamento insensível à cultura de um `SortedList`, crie um `SortedList` usando um dos construtores que aceita um parâmetro `comparer`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="edcf6-131">O parâmetro `comparer` especifica a implementação de <xref:System.Collections.IComparer> a ser usada ao comparar chaves.</span><span class="sxs-lookup"><span data-stu-id="edcf6-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="edcf6-132">Para o parâmetro, especifique uma classe de comparação personalizada que usa `CultureInfo.InvariantCulture` para comparar as chaves.</span><span class="sxs-lookup"><span data-stu-id="edcf6-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="edcf6-133">O exemplo a seguir ilustra uma classe de comparação personalizada insensível à cultura que você pode especificar como o parâmetro `comparer` para um construtor `SortedList`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

```vb
Imports System.Collections
Imports System.Globalization

Friend Class InvariantComparer
    Implements IComparer
    Private m_compareInfo As CompareInfo
    Friend Shared [Default] As New InvariantComparer()

    Friend Sub New()
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo
    End Sub

    Public Function Compare(a As Object, b As Object) As Integer _
            Implements IComparer.Compare
        Dim sa As String = CType(a, String)
        Dim sb As String = CType(b, String)
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then
            Return m_compareInfo.Compare(sa, sb)
        Else
            Return Comparer.Default.Compare(a, b)
        End If
    End Function
End Class
```

```csharp
using System;
using System.Collections;
using System.Globalization;

internal class InvariantComparer : IComparer
{
    private CompareInfo m_compareInfo;
    internal static readonly InvariantComparer Default = new
        InvariantComparer();

    internal InvariantComparer()
    {
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;
    }

    public int Compare(Object a, Object b)
    {
        String sa = a as String;
        String sb = b as String;
        if (sa != null && sb != null)
            return m_compareInfo.Compare(sa, sb);
        else
            return Comparer.Default.Compare(a,b);
    }
}
```

<span data-ttu-id="edcf6-134">Em geral, se você usar `SortedList` em cadeias de caracteres sem especificar um comparador personalizado invariável, uma alteração em `Thread.CurrentCulture` após o preenchimento da lista poderá invalidar a lista.</span><span class="sxs-lookup"><span data-stu-id="edcf6-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="edcf6-135">Usar o método ArrayList.Sort</span><span class="sxs-lookup"><span data-stu-id="edcf6-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="edcf6-136">Sobrecargas do método `ArrayList.Sort` executam, por padrão, classificações sensíveis à cultura usando a propriedade `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="edcf6-137">Os resultados podem variar de acordo com a cultura, devido a ordens de classificação diferentes.</span><span class="sxs-lookup"><span data-stu-id="edcf6-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="edcf6-138">Para eliminar o comportamento sensível à cultura, use as sobrecargas desse método para aceitar uma implementação `IComparer`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="edcf6-139">Para o parâmetro `comparer`, especifique uma classe de comparação invariável personalizada que usa `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="edcf6-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="edcf6-140">Um exemplo de uma classe de comparação invariável personalizada é fornecido no tópico [Usar a classe SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1).</span><span class="sxs-lookup"><span data-stu-id="edcf6-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="edcf6-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="edcf6-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="edcf6-142">Executando operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="edcf6-142">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
