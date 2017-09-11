---
title: "abstract (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a109a8e37f84a2e91229bfce789a69cdc26adba9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="abstract-c-reference"></a><span data-ttu-id="4078b-102">abstract (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4078b-102">abstract (C# Reference)</span></span>
<span data-ttu-id="4078b-103">O modificador `abstract` indica que o item que está sendo modificado tem uma implementação ausente ou incompleta.</span><span class="sxs-lookup"><span data-stu-id="4078b-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="4078b-104">O modificador abstrato pode ser usado com classes, métodos, propriedades, indexadores e eventos.</span><span class="sxs-lookup"><span data-stu-id="4078b-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="4078b-105">Use o modificador `abstract` em uma declaração de classe para indicar que uma classe destina-se apenas a ser uma classe base de outras classes.</span><span class="sxs-lookup"><span data-stu-id="4078b-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="4078b-106">Membros marcados como abstratos ou incluídos em uma classe abstrata, devem ser implementados por classes que derivam da classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="4078b-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4078b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4078b-107">Example</span></span>  
 <span data-ttu-id="4078b-108">Neste exemplo, a classe `Square` deve fornecer uma implementação de `Area` porque deriva de `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="4078b-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 <span data-ttu-id="4078b-109">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4078b-109">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]</span></span>  
  
 <span data-ttu-id="4078b-110">As classes abstratas têm os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="4078b-110">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="4078b-111">Uma classe abstrata não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="4078b-111">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="4078b-112">Uma classe abstrata pode conter acessadores e métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="4078b-112">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="4078b-113">Não é possível modificar uma classe abstrata com o modificador [sealed](../../../csharp/language-reference/keywords/sealed.md) porque os dois modificadores têm significados opostos.</span><span class="sxs-lookup"><span data-stu-id="4078b-113">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="4078b-114">O modificador `sealed` impede que uma classe seja herdada e o modificador `abstract` requer uma classe a ser herdada.</span><span class="sxs-lookup"><span data-stu-id="4078b-114">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="4078b-115">Uma classe não abstrata derivada de uma classe abstrata deve incluir implementações reais de todos os acessadores e métodos abstratos herdados.</span><span class="sxs-lookup"><span data-stu-id="4078b-115">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="4078b-116">Use o modificador `abstract` em uma declaração de método ou propriedade para indicar que o método ou propriedade não contem a implementação.</span><span class="sxs-lookup"><span data-stu-id="4078b-116">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="4078b-117">Os métodos abstratos têm os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="4078b-117">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="4078b-118">Um método abstrato é implicitamente um método virtual.</span><span class="sxs-lookup"><span data-stu-id="4078b-118">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="4078b-119">Declarações de método abstrato são permitidas apenas em classes abstratas.</span><span class="sxs-lookup"><span data-stu-id="4078b-119">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="4078b-120">Como uma declaração de método abstrato não fornece nenhuma implementação real, não há nenhum corpo de método, a declaração do método simplesmente termina com um ponto e vírgula e não há chaves ({ }) após a assinatura.</span><span class="sxs-lookup"><span data-stu-id="4078b-120">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="4078b-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4078b-121">For example:</span></span>  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="4078b-122">A implementação é fornecida por um método de substituição [override](../../../csharp/language-reference/keywords/override.md), que é um membro de uma classe não abstrata.</span><span class="sxs-lookup"><span data-stu-id="4078b-122">The implementation is provided by an overriding method[override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="4078b-123">É um erro usar os modificadores [static](../../../csharp/language-reference/keywords/static.md) ou [virtual](../../../csharp/language-reference/keywords/virtual.md) em uma declaração de método abstrato.</span><span class="sxs-lookup"><span data-stu-id="4078b-123">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="4078b-124">Propriedades abstratas se comportam como métodos abstratos, exceto pelas diferenças na sintaxe de declaração e chamada.</span><span class="sxs-lookup"><span data-stu-id="4078b-124">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="4078b-125">É um erro usar o modificador `abstract` em uma propriedade estática.</span><span class="sxs-lookup"><span data-stu-id="4078b-125">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="4078b-126">Uma propriedade herdada abstrata pode ser substituída em uma classe derivada incluindo uma declaração de propriedade que usa o modificador [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="4078b-126">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="4078b-127">Para obter mais informações sobre classes abstratas, consulte [Classes e membros de classes abstratos e lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="4078b-127">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="4078b-128">Uma classe abstrata deve fornecer uma implementação para todos os membros de interface.</span><span class="sxs-lookup"><span data-stu-id="4078b-128">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="4078b-129">Uma classe abstrata que implementa uma interface pode mapear os métodos de interface em métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="4078b-129">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="4078b-130">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4078b-130">For example:</span></span>  
  
 <span data-ttu-id="4078b-131">[!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4078b-131">[!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4078b-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4078b-132">Example</span></span>  
 <span data-ttu-id="4078b-133">Nesse exemplo, a classe `DerivedClass` é derivada de uma classe abstrata `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="4078b-133">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="4078b-134">A classe abstrata contém um método abstrato, `AbstractMethod` e duas propriedades abstratas, `X` e `Y`.</span><span class="sxs-lookup"><span data-stu-id="4078b-134">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
 <span data-ttu-id="4078b-135">[!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4078b-135">[!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]</span></span>  
  
 <span data-ttu-id="4078b-136">No exemplo anterior, se você tentar instanciar a classe abstrata usando uma instrução como esta:</span><span class="sxs-lookup"><span data-stu-id="4078b-136">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 <span data-ttu-id="4078b-137">você receberá uma mensagem de erro informando que o compilador não pode criar uma instância da classe abstrata 'BaseClass'.</span><span class="sxs-lookup"><span data-stu-id="4078b-137">you will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4078b-138">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4078b-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4078b-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4078b-139">See Also</span></span>  
 <span data-ttu-id="4078b-140">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4078b-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4078b-141">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4078b-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4078b-142">[Modificadores](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="4078b-142">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="4078b-143">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span><span class="sxs-lookup"><span data-stu-id="4078b-143">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span></span>  
 <span data-ttu-id="4078b-144">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="4078b-144">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="4078b-145">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="4078b-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

