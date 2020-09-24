---
title: Interfaces genéricas – Guia de Programação em C#
description: Saiba mais sobre como usar interfaces genéricas em C#. Confira exemplos de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: ec86395a41baea75694572b59b2c76cbde24fedf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170383"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="ceaf3-104">Interfaces genéricas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ceaf3-104">Generic Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="ceaf3-105">Muitas vezes, é útil definir interfaces para classes de coleção genéricas ou para as classe genéricas que representam itens na coleção.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-105">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="ceaf3-106">Para classes genéricas, prefere-se usar interfaces genéricas, como <xref:System.IComparable%601> em vez de <xref:System.IComparable>, a fim de evitar operações de conversão boxing e unboxing em tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-106">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="ceaf3-107">A biblioteca de classes .NET define várias interfaces genéricas para uso com as classes de coleção no <xref:System.Collections.Generic> namespace.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-107">The .NET class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="ceaf3-108">Quando uma interface é especificada como uma restrição em um parâmetro de tipo, somente os tipos que implementam a interface podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-108">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="ceaf3-109">O exemplo de código a seguir mostra uma classe `SortedList<T>` que deriva da classe `GenericList<T>`.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-109">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="ceaf3-110">Para obter mais informações, consulte [Introdução aos Genéricos](./index.md).</span><span class="sxs-lookup"><span data-stu-id="ceaf3-110">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="ceaf3-111">`SortedList<T>` adiciona a restrição `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-111">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="ceaf3-112">Isso habilita o método `BubbleSort` em `SortedList<T>` a usar o método genérico <xref:System.IComparable%601.CompareTo%2A> em elementos de lista.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-112">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="ceaf3-113">Neste exemplo, os elementos de lista são uma classe simples, `Person`, que implementa `IComparable<Person>`.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-113">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="ceaf3-114">Várias interfaces podem ser especificadas como restrições em um único tipo, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ceaf3-114">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="ceaf3-115">Uma interface pode definir mais de um parâmetro de tipo, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ceaf3-115">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="ceaf3-116">As regras de herança que se aplicam às classes também se aplicam às interfaces:</span><span class="sxs-lookup"><span data-stu-id="ceaf3-116">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="ceaf3-117">Interfaces genéricas poderão herdar de interfaces não genéricas se a interface genérica for contravariante, o que significa que ela usa apenas seu parâmetro de tipo como um valor retornado.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-117">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="ceaf3-118">Na biblioteca de classes .NET, é <xref:System.Collections.Generic.IEnumerable%601> herdado de <xref:System.Collections.IEnumerable> porque <xref:System.Collections.Generic.IEnumerable%601> apenas usa `T` no valor de retorno de <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> e no <xref:System.Collections.Generic.IEnumerator%601.Current%2A> getter da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-118">In the .NET class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="ceaf3-119">Classes concretas podem implementar interfaces construídas fechadas, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ceaf3-119">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="ceaf3-120">Classes genéricas podem implementar interfaces genéricas ou interfaces construídas fechadas, contanto que a lista de parâmetros de classe forneça todos os argumentos exigidos pela interface, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ceaf3-120">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="ceaf3-121">As regras que controlam a sobrecarga de método são as mesmas para métodos em classes genéricas, structs genéricos ou interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="ceaf3-121">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="ceaf3-122">Para obter mais informações, consulte [Métodos Genéricos](./generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ceaf3-122">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceaf3-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="ceaf3-123">See also</span></span>

- [<span data-ttu-id="ceaf3-124">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="ceaf3-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ceaf3-125">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="ceaf3-125">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="ceaf3-126">interface</span><span class="sxs-lookup"><span data-stu-id="ceaf3-126">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="ceaf3-127">Genéricos</span><span class="sxs-lookup"><span data-stu-id="ceaf3-127">Generics</span></span>](../../../standard/generics/index.md)
