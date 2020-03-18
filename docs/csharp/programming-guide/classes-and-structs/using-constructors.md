---
title: Usando construtores – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 7c227b61c6d5b4ead00fced0dba046b90683fde1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626406"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="e50f5-102">Usando construtores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e50f5-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="e50f5-103">Quando uma [classe](../../language-reference/keywords/class.md) ou [struct](../../language-reference/builtin-types/struct.md) é criado, seu construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="e50f5-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="e50f5-104">Os construtores têm o mesmo nome que a classe ou struct e eles geralmente inicializam os membros de dados do novo objeto.</span><span class="sxs-lookup"><span data-stu-id="e50f5-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="e50f5-105">No exemplo a seguir, uma classe chamada `Taxi` é definida usando um construtor simples.</span><span class="sxs-lookup"><span data-stu-id="e50f5-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="e50f5-106">A classe é então instanciada com o operador [new](../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="e50f5-107">O construtor `Taxi` é invocado pelo operador `new` imediatamente após a memória ser alocada para o novo objeto.</span><span class="sxs-lookup"><span data-stu-id="e50f5-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="e50f5-108">Um construtor que não tem nenhum parâmetro é chamado de *construtor sem parâmetros*.</span><span class="sxs-lookup"><span data-stu-id="e50f5-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="e50f5-109">Os construtores sem parâmetros são invocados sempre que um objeto é instanciado usando o operador `new` e nenhum argumento é fornecido para `new`.</span><span class="sxs-lookup"><span data-stu-id="e50f5-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="e50f5-110">Para obter mais informações, consulte [Construtores de instâncias](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="e50f5-111">A menos que a classe seja [static](../../language-reference/keywords/static.md), as classes sem construtores recebem um construtor sem parâmetros público pelo compilador C# para habilitar a instanciação de classe.</span><span class="sxs-lookup"><span data-stu-id="e50f5-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="e50f5-112">Para obter mais informações, consulte [Classes Estáticas e Membros de Classe Estática](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="e50f5-113">Você pode impedir que uma classe seja instanciada tornando o construtor privado, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e50f5-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="e50f5-114">Para obter mais informações, consulte [Construtores particulares](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="e50f5-115">Os construtores de tipos [struct](../../language-reference/builtin-types/struct.md) são semelhantes aos construtores de classe, mas `structs` não podem conter um construtor sem parâmetros explícito porque um é fornecido automaticamente pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="e50f5-115">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="e50f5-116">Este construtor inicializa cada campo `struct` no [valor padrão.](../../language-reference/builtin-types/default-values.md)</span><span class="sxs-lookup"><span data-stu-id="e50f5-116">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="e50f5-117">No entanto, esse construtor sem parâmetro será invocado apenas se o `struct` for instanciado com `new`.</span><span class="sxs-lookup"><span data-stu-id="e50f5-117">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="e50f5-118">Por exemplo, esse código usa o construtor sem parâmetros para <xref:System.Int32>, de modo que você tenha certeza de que o inteiro é inicializado:</span><span class="sxs-lookup"><span data-stu-id="e50f5-118">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="e50f5-119">O código a seguir, no entanto, causa um erro do compilador porque ele não usa `new` e porque ele tenta usar um objeto que não foi inicializado:</span><span class="sxs-lookup"><span data-stu-id="e50f5-119">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="e50f5-120">Como alternativa, os objetos com base em `structs` (incluindo todos os tipos numéricos internos) podem ser inicializados ou atribuídos e, em seguida, usados como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e50f5-120">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="e50f5-121">Portanto, não é necessário chamar o construtor sem parâmetros para um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="e50f5-121">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="e50f5-122">Ambas as classes e `structs` podem definir construtores que usam parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e50f5-122">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="e50f5-123">Os construtores que usam parâmetros devem ser chamados por meio de uma instrução `new` ou uma instrução [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-123">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="e50f5-124">As classes e `structs` também podem definir vários construtores e nenhum deles precisa definir um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e50f5-124">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="e50f5-125">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="e50f5-125">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="e50f5-126">Essa classe pode ser criada usando qualquer uma das instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="e50f5-126">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="e50f5-127">Um construtor pode usar a palavra-chave `base` para chamar o construtor de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="e50f5-127">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="e50f5-128">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="e50f5-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="e50f5-129">Neste exemplo, o construtor da classe base é chamado antes de o bloco do construtor ser executado.</span><span class="sxs-lookup"><span data-stu-id="e50f5-129">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="e50f5-130">A palavra-chave `base` pode ser usada com ou sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e50f5-130">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="e50f5-131">Os parâmetros para o construtor podem ser usados como parâmetros para `base` ou como parte de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="e50f5-131">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="e50f5-132">Para obter mais informações, consulte [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-132">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="e50f5-133">Em uma classe derivada, se um construtor de classe base não for chamado explicitamente usando a palavra-chave `base`, o construtor sem parâmetros, se houver, será chamado implicitamente.</span><span class="sxs-lookup"><span data-stu-id="e50f5-133">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="e50f5-134">Isso significa que as seguintes declarações de construtor são efetivamente iguais:</span><span class="sxs-lookup"><span data-stu-id="e50f5-134">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="e50f5-135">Se uma classe base não oferecer um construtor sem parâmetros, a classe derivada deverá fazer uma chamada explícita para um construtor base usando `base`.</span><span class="sxs-lookup"><span data-stu-id="e50f5-135">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="e50f5-136">Um construtor pode invocar outro construtor no mesmo objeto usando a palavra-chave [this](../../language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-136">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="e50f5-137">Como `base`, `this` pode ser usado com ou sem parâmetros e todos os parâmetros no construtor estão disponíveis como parâmetros para `this` ou como parte de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="e50f5-137">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="e50f5-138">Por exemplo, o segundo construtor no exemplo anterior pode ser reescrito usando `this`:</span><span class="sxs-lookup"><span data-stu-id="e50f5-138">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="e50f5-139">O uso da palavra-chave `this` no exemplo anterior faz com que esse construtor seja chamado:</span><span class="sxs-lookup"><span data-stu-id="e50f5-139">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="e50f5-140">Os construtores podem ser marcados como [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) ou [private protected](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-140">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="e50f5-141">Esses modificadores de acesso definem como os usuários da classe podem construir a classe.</span><span class="sxs-lookup"><span data-stu-id="e50f5-141">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="e50f5-142">Para obter mais informações, consulte [Modificadores de Acesso](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-142">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="e50f5-143">Um construtor pode ser declarado estático usando a palavra-chave [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-143">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="e50f5-144">Os construtores estáticos são chamados automaticamente, imediatamente antes de qualquer campo estático ser acessado e geralmente são usados para inicializar membros da classe estática.</span><span class="sxs-lookup"><span data-stu-id="e50f5-144">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="e50f5-145">Para obter mais informações, consulte [Construtores estáticos](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e50f5-145">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e50f5-146">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e50f5-146">C# Language Specification</span></span>  

<span data-ttu-id="e50f5-147">Para obter mais informações, veja [Construtores de instância](~/_csharplang/spec/classes.md#instance-constructors) e [Construtores estáticos](~/_csharplang/spec/classes.md#static-constructors) na [Especificação de Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="e50f5-147">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="e50f5-148">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="e50f5-148">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e50f5-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="e50f5-149">See also</span></span>

- [<span data-ttu-id="e50f5-150">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="e50f5-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e50f5-151">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="e50f5-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e50f5-152">Construtores</span><span class="sxs-lookup"><span data-stu-id="e50f5-152">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e50f5-153">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="e50f5-153">Finalizers</span></span>](./destructors.md)
