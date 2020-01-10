---
title: Construtores – Guia de Programação em C#
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 9c57ff6dd9acd8a8bcff6de4fce7d898f1135703
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714961"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="fc240-102">Construtores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fc240-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="fc240-103">Sempre que uma [classe](../../language-reference/keywords/class.md) ou [struct](../../language-reference/keywords/struct.md) é criada, o construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="fc240-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="fc240-104">Uma classe ou struct pode ter vários construtores que usam argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="fc240-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="fc240-105">Os construtores permitem que o programador defina valores padrão, limite a instanciação e grave códigos flexíveis e fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="fc240-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="fc240-106">Para obter mais informações e exemplos, consulte [Usando Construtores](./using-constructors.md) e [Construtores de Instância](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="fc240-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="fc240-107">Construtores sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc240-107">Parameterless constructors</span></span>
  
<span data-ttu-id="fc240-108">Se um construtor não for fornecido para a classe, o C# criará por padrão um construtor que instancia o objeto e define variáveis de membro para os valores padrão, conforme listado na [Tabela de Valores Padrão](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="fc240-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="fc240-109">Se você não fornecer um construtor para o struct, o C# dependerá de um *construtor sem parâmetro implícito* para inicializar automaticamente a cada campo de um tipo de valor para o valor padrão conforme listado na [Tabela de Valores Padrão](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="fc240-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="fc240-110">Para obter mais informações e exemplos, consulte [Construtores de Instância](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="fc240-110">For more information and examples, see [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="fc240-111">Sintaxe do construtor</span><span class="sxs-lookup"><span data-stu-id="fc240-111">Constructor syntax</span></span>

<span data-ttu-id="fc240-112">Um construtor é um método cujo nome é igual ao nome de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="fc240-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="fc240-113">Sua assinatura do método inclui apenas o nome do método e lista de parâmetros, ele não inclui um tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="fc240-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="fc240-114">O exemplo a seguir mostra o construtor para uma classe denominada `Person`.</span><span class="sxs-lookup"><span data-stu-id="fc240-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="fc240-115">Se um construtor puder ser implementado como uma única instrução, você poderá usar uma [definição de corpo da expressão](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="fc240-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="fc240-116">O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*.</span><span class="sxs-lookup"><span data-stu-id="fc240-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="fc240-117">A definição de corpo da expressão atribui o argumento ao campo `locationName`.</span><span class="sxs-lookup"><span data-stu-id="fc240-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="fc240-118">Construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="fc240-118">Static constructors</span></span>

<span data-ttu-id="fc240-119">Os exemplos anteriores têm todos os construtores de instância mostrado, que criam um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="fc240-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="fc240-120">Uma classe ou struct também pode ter um construtor estático, que inicializa membros estáticos do tipo.</span><span class="sxs-lookup"><span data-stu-id="fc240-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="fc240-121">Construtores estáticos não têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fc240-121">Static constructors are parameterless.</span></span> <span data-ttu-id="fc240-122">Se você não fornecer um construtor estático para inicializar campos estáticos, o compilador C# inicializará campos estáticos com seu valor padrão, conforme listado na [Tabela de Valores Padrão](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="fc240-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span>

<span data-ttu-id="fc240-123">O exemplo a seguir usa um construtor estático para inicializar um campo estático.</span><span class="sxs-lookup"><span data-stu-id="fc240-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="fc240-124">Você também pode definir um construtor estático com uma definição de corpo da expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fc240-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="fc240-125">Para obter mais informações e exemplos, consulte [Construtores Estáticos](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="fc240-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc240-126">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="fc240-126">In This Section</span></span>  
 [<span data-ttu-id="fc240-127">Usando construtores</span><span class="sxs-lookup"><span data-stu-id="fc240-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="fc240-128">Construtores de instância</span><span class="sxs-lookup"><span data-stu-id="fc240-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="fc240-129">Construtores particulares</span><span class="sxs-lookup"><span data-stu-id="fc240-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="fc240-130">Construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="fc240-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="fc240-131">Como escrever um construtor de cópia</span><span class="sxs-lookup"><span data-stu-id="fc240-131">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="fc240-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="fc240-132">See also</span></span>

- [<span data-ttu-id="fc240-133">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fc240-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fc240-134">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="fc240-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="fc240-135">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="fc240-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="fc240-136">static</span><span class="sxs-lookup"><span data-stu-id="fc240-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="fc240-137">Por que inicializadores são executados na ordem oposta como construtores? Parte um</span><span class="sxs-lookup"><span data-stu-id="fc240-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
