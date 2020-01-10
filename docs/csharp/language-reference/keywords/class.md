---
title: Palavra-chave class – Referência de C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 187a49131e903e00cab54d9db43b6cd8eb359a3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713686"
---
# <a name="class-c-reference"></a><span data-ttu-id="7f826-102">class (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7f826-102">class (C# Reference)</span></span>

<span data-ttu-id="7f826-103">Classes são declaradas usando a palavra-chave `class`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7f826-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="7f826-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f826-104">Remarks</span></span>

<span data-ttu-id="7f826-105">Somente a herança única é permitida em C#.</span><span class="sxs-lookup"><span data-stu-id="7f826-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="7f826-106">Em outras palavras, uma classe pode herdar a implementação de apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="7f826-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="7f826-107">No entanto, uma classe pode implementar mais de uma interface.</span><span class="sxs-lookup"><span data-stu-id="7f826-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="7f826-108">A tabela a seguir mostra exemplos de implementação de interface e herança de classe:</span><span class="sxs-lookup"><span data-stu-id="7f826-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="7f826-109">{1&gt;Herança&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7f826-109">Inheritance</span></span>|<span data-ttu-id="7f826-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f826-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="7f826-111">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7f826-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="7f826-112">Simples</span><span class="sxs-lookup"><span data-stu-id="7f826-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="7f826-113">Nenhuma, implementa duas interfaces</span><span class="sxs-lookup"><span data-stu-id="7f826-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="7f826-114">Única, implementa uma interface</span><span class="sxs-lookup"><span data-stu-id="7f826-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="7f826-115">Classes que você declara diretamente dentro de um namespace, não aninhadas em outras classes, podem ser [públicas](./public.md) ou [internas](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="7f826-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="7f826-116">As classes são `internal` por padrão.</span><span class="sxs-lookup"><span data-stu-id="7f826-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="7f826-117">Os membros da classe, incluindo classes aninhadas, podem ser [públicos](public.md), [internos protegidos](protected-internal.md), [protegidos](protected.md), [internos](internal.md), [privados](private.md) ou [protegidos privados](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="7f826-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="7f826-118">Os membros são `private` por padrão.</span><span class="sxs-lookup"><span data-stu-id="7f826-118">Members are `private` by default.</span></span>

<span data-ttu-id="7f826-119">Para obter mais informações, consulte [Modificadores de Acesso](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="7f826-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="7f826-120">É possível declarar classes genéricas que têm parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="7f826-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="7f826-121">Para obter mais informações, consulte [Classes genéricas](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7f826-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="7f826-122">Uma classe pode conter declarações dos seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="7f826-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="7f826-123">Construtores</span><span class="sxs-lookup"><span data-stu-id="7f826-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="7f826-124">Constantes</span><span class="sxs-lookup"><span data-stu-id="7f826-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="7f826-125">Campos</span><span class="sxs-lookup"><span data-stu-id="7f826-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="7f826-126">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="7f826-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="7f826-127">Métodos</span><span class="sxs-lookup"><span data-stu-id="7f826-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="7f826-128">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7f826-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="7f826-129">Indexadores</span><span class="sxs-lookup"><span data-stu-id="7f826-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="7f826-130">Operadores</span><span class="sxs-lookup"><span data-stu-id="7f826-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="7f826-131">Eventos</span><span class="sxs-lookup"><span data-stu-id="7f826-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="7f826-132">Delegados</span><span class="sxs-lookup"><span data-stu-id="7f826-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="7f826-133">Classes</span><span class="sxs-lookup"><span data-stu-id="7f826-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="7f826-134">Interfaces</span><span class="sxs-lookup"><span data-stu-id="7f826-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="7f826-135">Structs</span><span class="sxs-lookup"><span data-stu-id="7f826-135">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="7f826-136">Enumerações</span><span class="sxs-lookup"><span data-stu-id="7f826-136">Enumerations</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="7f826-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f826-137">Example</span></span>

<span data-ttu-id="7f826-138">O exemplo a seguir demonstra a declaração de métodos, construtores e campos de classe.</span><span class="sxs-lookup"><span data-stu-id="7f826-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="7f826-139">Ele também demonstra a instanciação de objetos e a impressão de dados de instância.</span><span class="sxs-lookup"><span data-stu-id="7f826-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="7f826-140">Neste exemplo, duas classes são declaradas.</span><span class="sxs-lookup"><span data-stu-id="7f826-140">In this example, two classes are declared.</span></span> <span data-ttu-id="7f826-141">A primeira classe, `Child`, contém dois campos particulares (`name` e `age`), dois construtores públicos e um método público.</span><span class="sxs-lookup"><span data-stu-id="7f826-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="7f826-142">A segunda classe, `StringTest`, é usada para conter `Main`.</span><span class="sxs-lookup"><span data-stu-id="7f826-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="7f826-143">Comments</span><span class="sxs-lookup"><span data-stu-id="7f826-143">Comments</span></span>

<span data-ttu-id="7f826-144">Observe que, no exemplo anterior, os campos particulares (`name` e `age`) só podem ser acessados por meio dos métodos públicos da classe `Child`.</span><span class="sxs-lookup"><span data-stu-id="7f826-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="7f826-145">Por exemplo, você não pode imprimir o nome do filho, do método `Main`, usando uma instrução como esta:</span><span class="sxs-lookup"><span data-stu-id="7f826-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="7f826-146">Acessar membros particulares de `Child` de `Main` seria possível apenas se `Main` fosse um membro da classe.</span><span class="sxs-lookup"><span data-stu-id="7f826-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="7f826-147">Tipos declarados dentro de uma classe sem um modificador de acesso têm o valor padrão de `private`, portanto, os membros de dados neste exemplo ainda seriam `private` se a palavra-chave fosse removida.</span><span class="sxs-lookup"><span data-stu-id="7f826-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="7f826-148">Por fim, observe que, para o objeto criado usando o construtor sem parâmetro (`child3`), o campo `age` foi inicializado como zero por padrão.</span><span class="sxs-lookup"><span data-stu-id="7f826-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7f826-149">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7f826-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7f826-150">Veja também</span><span class="sxs-lookup"><span data-stu-id="7f826-150">See also</span></span>

- [<span data-ttu-id="7f826-151">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7f826-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7f826-152">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7f826-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7f826-153">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7f826-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="7f826-154">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="7f826-154">Reference Types</span></span>](./reference-types.md)
