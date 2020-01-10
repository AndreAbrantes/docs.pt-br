---
title: Modificador override – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713242"
---
# <a name="override-c-reference"></a><span data-ttu-id="66cbf-102">override (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="66cbf-102">override (C# Reference)</span></span>

<span data-ttu-id="66cbf-103">O modificador `override` é necessário para estender ou modificar a implementação abstrata ou virtual de um método, propriedade, indexador ou evento herdado.</span><span class="sxs-lookup"><span data-stu-id="66cbf-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="66cbf-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="66cbf-104">Example</span></span>

<span data-ttu-id="66cbf-105">Neste exemplo, a classe `Square` deve fornecer uma implementação substituída de `GetArea` porque `GetArea` é herdado da classe abstrata `Shape`:</span><span class="sxs-lookup"><span data-stu-id="66cbf-105">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="66cbf-106">Um método `override` fornece uma nova implementação de um membro herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="66cbf-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="66cbf-107">O método que é substituído por uma declaração `override` é conhecido como o método base substituído.</span><span class="sxs-lookup"><span data-stu-id="66cbf-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="66cbf-108">O método base substituído deve ter a mesma assinatura que o método `override`.</span><span class="sxs-lookup"><span data-stu-id="66cbf-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="66cbf-109">Para obter informações sobre herança, consulte [Herança](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="66cbf-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="66cbf-110">Você não pode substituir um método não virtual ou estático.</span><span class="sxs-lookup"><span data-stu-id="66cbf-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="66cbf-111">O método base substituído deve ser `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="66cbf-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="66cbf-112">Uma declaração `override` não pode alterar a acessibilidade do método `virtual`.</span><span class="sxs-lookup"><span data-stu-id="66cbf-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="66cbf-113">O método `override` e o método `virtual` devem ter o mesmo [modificador de nível de acesso](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="66cbf-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="66cbf-114">Não é possível usar os modificadores `new`, `static` ou `virtual` para modificar um método `override`.</span><span class="sxs-lookup"><span data-stu-id="66cbf-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="66cbf-115">Uma declaração de propriedade de substituição deve especificar exatamente o mesmo modificador de acesso, tipo e nome que a propriedade herdada e a propriedade substituída deve ser `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="66cbf-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="66cbf-116">Para obter mais informações sobre como usar a palavra-chave `override`, consulte [Controle de versão com as palavras-chave override e new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Quando usar as palavras-chave override e new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="66cbf-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="66cbf-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="66cbf-117">Example</span></span>

<span data-ttu-id="66cbf-118">Este exemplo define uma classe base chamada `Employee` e uma classe derivada chamada `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="66cbf-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="66cbf-119">A classe `SalesEmployee` inclui um campo extra, `salesbonus`, e substitui o método `CalculatePay` para levar isso em consideração.</span><span class="sxs-lookup"><span data-stu-id="66cbf-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="66cbf-120">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="66cbf-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="66cbf-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="66cbf-121">See also</span></span>

- [<span data-ttu-id="66cbf-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="66cbf-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="66cbf-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="66cbf-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="66cbf-124">Herança</span><span class="sxs-lookup"><span data-stu-id="66cbf-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="66cbf-125">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="66cbf-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="66cbf-126">Modificadores</span><span class="sxs-lookup"><span data-stu-id="66cbf-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="66cbf-127">abstract</span><span class="sxs-lookup"><span data-stu-id="66cbf-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="66cbf-128">virtual</span><span class="sxs-lookup"><span data-stu-id="66cbf-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="66cbf-129">new (modificador)</span><span class="sxs-lookup"><span data-stu-id="66cbf-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="66cbf-130">Polimorfismo</span><span class="sxs-lookup"><span data-stu-id="66cbf-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
