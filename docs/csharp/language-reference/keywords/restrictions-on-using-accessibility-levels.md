---
title: Restrições ao uso de níveis de acessibilidade – Referência em C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 90c76e68ca526106f3a8be6e3db2640edbb2bc80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715159"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="cb42a-102">Restrições ao uso de níveis de acessibilidade (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="cb42a-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="cb42a-103">Quando você especifica um tipo em uma declaração, verifique se o nível de acessibilidade do tipo é dependente do nível de acessibilidade de um membro ou de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="cb42a-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="cb42a-104">Por exemplo, a classe base direta deve ser, pelo menos, tão acessível quanto a classe derivada.</span><span class="sxs-lookup"><span data-stu-id="cb42a-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="cb42a-105">As seguintes declarações causam um erro do compilador porque a classe base `BaseClass` é menos acessível que a `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="cb42a-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="cb42a-106">A tabela a seguir resume as restrições nos níveis de acessibilidade declarada.</span><span class="sxs-lookup"><span data-stu-id="cb42a-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="cb42a-107">Contexto</span><span class="sxs-lookup"><span data-stu-id="cb42a-107">Context</span></span>|<span data-ttu-id="cb42a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb42a-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="cb42a-109">Classes</span><span class="sxs-lookup"><span data-stu-id="cb42a-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="cb42a-110">A classe base direta de um tipo de classe deve ser, pelo menos, tão acessível quanto o próprio tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="cb42a-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="cb42a-111">Interfaces</span><span class="sxs-lookup"><span data-stu-id="cb42a-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="cb42a-112">As interfaces base explícitas de um tipo de interface devem ser, pelo menos, tão acessíveis quanto o próprio tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="cb42a-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="cb42a-113">Delegados</span><span class="sxs-lookup"><span data-stu-id="cb42a-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="cb42a-114">O tipo de retorno e os tipos de parâmetro de um tipo delegado devem ser, pelo menos, tão acessíveis quanto o próprio tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="cb42a-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="cb42a-115">Constantes</span><span class="sxs-lookup"><span data-stu-id="cb42a-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="cb42a-116">O tipo de uma constante deve ser, pelo menos, tão acessível quanto a própria constante.</span><span class="sxs-lookup"><span data-stu-id="cb42a-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="cb42a-117">Campos</span><span class="sxs-lookup"><span data-stu-id="cb42a-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="cb42a-118">O tipo de um campo deve ser, pelo menos, tão acessível quanto o próprio campo.</span><span class="sxs-lookup"><span data-stu-id="cb42a-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="cb42a-119">Métodos</span><span class="sxs-lookup"><span data-stu-id="cb42a-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="cb42a-120">O tipo de retorno e os tipos de parâmetro de um método devem ser, pelo menos, tão acessíveis quanto o próprio método.</span><span class="sxs-lookup"><span data-stu-id="cb42a-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="cb42a-121">Propriedades</span><span class="sxs-lookup"><span data-stu-id="cb42a-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="cb42a-122">O tipo de uma propriedade deve ser, pelo menos, tão acessível quanto a propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="cb42a-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="cb42a-123">Eventos</span><span class="sxs-lookup"><span data-stu-id="cb42a-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="cb42a-124">O tipo de um evento deve ser, pelo menos, tão acessível quanto o próprio evento.</span><span class="sxs-lookup"><span data-stu-id="cb42a-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="cb42a-125">Indexadores</span><span class="sxs-lookup"><span data-stu-id="cb42a-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="cb42a-126">O tipo e os tipos de parâmetro de um indexador devem ser, pelo menos, tão acessíveis quanto o próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="cb42a-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="cb42a-127">Operadores</span><span class="sxs-lookup"><span data-stu-id="cb42a-127">Operators</span></span>](../operators/index.md)|<span data-ttu-id="cb42a-128">O tipo de retorno e os tipos de parâmetro de um operador devem ser, pelo menos, tão acessíveis quanto o próprio operador.</span><span class="sxs-lookup"><span data-stu-id="cb42a-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="cb42a-129">Construtores</span><span class="sxs-lookup"><span data-stu-id="cb42a-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="cb42a-130">Os tipos de parâmetro de um construtor devem ser, pelo menos, tão acessíveis quanto o próprio construtor.</span><span class="sxs-lookup"><span data-stu-id="cb42a-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="cb42a-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb42a-131">Example</span></span>

<span data-ttu-id="cb42a-132">O exemplo a seguir contém declarações incorretas de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="cb42a-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="cb42a-133">O comentário que segue cada declaração indica o erro do compilador esperado.</span><span class="sxs-lookup"><span data-stu-id="cb42a-133">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible 
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error: 
    // "The parameter B.MyPrivateMethod is not accessible due to 
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a><span data-ttu-id="cb42a-134">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="cb42a-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cb42a-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="cb42a-135">See also</span></span>

- [<span data-ttu-id="cb42a-136">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="cb42a-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="cb42a-137">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cb42a-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cb42a-138">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="cb42a-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="cb42a-139">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="cb42a-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="cb42a-140">Domínio de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="cb42a-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="cb42a-141">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="cb42a-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="cb42a-142">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="cb42a-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="cb42a-143">public</span><span class="sxs-lookup"><span data-stu-id="cb42a-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="cb42a-144">private</span><span class="sxs-lookup"><span data-stu-id="cb42a-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="cb42a-145">protected</span><span class="sxs-lookup"><span data-stu-id="cb42a-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="cb42a-146">internal</span><span class="sxs-lookup"><span data-stu-id="cb42a-146">internal</span></span>](../../language-reference/keywords/internal.md)
