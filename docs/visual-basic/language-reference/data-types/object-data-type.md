---
title: Tipo de dados Object
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 14770e74a0169dba3a45a04845dd32323e6201e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415577"
---
# <a name="object-data-type"></a><span data-ttu-id="2359f-102">Tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="2359f-102">Object Data Type</span></span>

<span data-ttu-id="2359f-103">Contém endereços que se referem a objetos.</span><span class="sxs-lookup"><span data-stu-id="2359f-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="2359f-104">Você pode atribuir qualquer tipo de referência (cadeia de caracteres, matriz, classe ou interface) a uma `Object` variável.</span><span class="sxs-lookup"><span data-stu-id="2359f-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="2359f-105">Uma `Object` variável também pode se referir a dados de qualquer tipo de valor (numérico, `Boolean` , `Char` , `Date` , estrutura ou Enumeração).</span><span class="sxs-lookup"><span data-stu-id="2359f-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>

## <a name="remarks"></a><span data-ttu-id="2359f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="2359f-106">Remarks</span></span>

<span data-ttu-id="2359f-107">O `Object` tipo de dados pode apontar para dados de qualquer tipo de dados, incluindo qualquer instância de objeto que seu aplicativo reconhece.</span><span class="sxs-lookup"><span data-stu-id="2359f-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="2359f-108">Use `Object` quando você não souber em tempo de compilação a qual tipo de dados a variável pode apontar.</span><span class="sxs-lookup"><span data-stu-id="2359f-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>

<span data-ttu-id="2359f-109">O valor padrão de `Object` é `Nothing` (uma referência nula).</span><span class="sxs-lookup"><span data-stu-id="2359f-109">The default value of `Object` is `Nothing` (a null reference).</span></span>

## <a name="data-types"></a><span data-ttu-id="2359f-110">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="2359f-110">Data Types</span></span>

<span data-ttu-id="2359f-111">Você pode atribuir uma variável, constante ou expressão de qualquer tipo de dados a uma `Object` variável.</span><span class="sxs-lookup"><span data-stu-id="2359f-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="2359f-112">Para determinar o tipo de dados `Object` ao qual uma variável se refere atualmente, você pode usar o <xref:System.Type.GetTypeCode%2A> método da <xref:System.Type?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="2359f-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2359f-113">O exemplo a seguir ilustra isto.</span><span class="sxs-lookup"><span data-stu-id="2359f-113">The following example illustrates this.</span></span>

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

<span data-ttu-id="2359f-114">O `Object` tipo de dados é um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="2359f-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="2359f-115">No entanto, Visual Basic trata uma `Object` variável como um tipo de valor quando se refere aos dados de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2359f-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>

## <a name="storage"></a><span data-ttu-id="2359f-116">Armazenamento</span><span class="sxs-lookup"><span data-stu-id="2359f-116">Storage</span></span>

<span data-ttu-id="2359f-117">Qualquer tipo de dados ao qual se refere, uma `Object` variável não contém o próprio valor de dados, mas sim um ponteiro para o valor.</span><span class="sxs-lookup"><span data-stu-id="2359f-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="2359f-118">Ele sempre usa quatro bytes na memória do computador, mas isso não inclui o armazenamento para os dados que representam o valor da variável.</span><span class="sxs-lookup"><span data-stu-id="2359f-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="2359f-119">Devido ao código que usa o ponteiro para localizar os dados, as `Object` variáveis que mantêm os tipos de valor são um pouco mais lentas para acessar do que as variáveis explicitamente digitadas.</span><span class="sxs-lookup"><span data-stu-id="2359f-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="2359f-120">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="2359f-120">Programming Tips</span></span>

- <span data-ttu-id="2359f-121">**Considerações sobre interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="2359f-121">**Interop Considerations.**</span></span> <span data-ttu-id="2359f-122">Se você estiver fazendo a interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos COM, tenha em mente que os tipos de ponteiro em outros ambientes não são compatíveis com o tipo de Visual Basic `Object` .</span><span class="sxs-lookup"><span data-stu-id="2359f-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>

- <span data-ttu-id="2359f-123">**Desempenho.**</span><span class="sxs-lookup"><span data-stu-id="2359f-123">**Performance.**</span></span> <span data-ttu-id="2359f-124">Uma variável que você declara com o `Object` tipo é flexível o suficiente para conter uma referência a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="2359f-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="2359f-125">No entanto, quando você invoca um método ou propriedade em tal variável, sempre ocorre a *ligação tardia* (em tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="2359f-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="2359f-126">Para forçar a *ligação antecipada* (no momento da compilação) e melhorar o desempenho, declare a variável com um nome de classe específico ou converta-a para o tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="2359f-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>

  <span data-ttu-id="2359f-127">Ao declarar uma variável de objeto, tente usar um tipo de classe específico, por exemplo <xref:System.OperatingSystem> , em vez do tipo generalizado `Object` .</span><span class="sxs-lookup"><span data-stu-id="2359f-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="2359f-128">Você também deve usar a classe mais específica disponível, como <xref:System.Windows.Forms.TextBox> em vez de <xref:System.Windows.Forms.Control> , para que você possa acessar suas propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="2359f-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="2359f-129">Normalmente, você pode usar a lista de **classes** no **pesquisador de objetos** para localizar os nomes de classe disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2359f-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>

- <span data-ttu-id="2359f-130">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="2359f-130">**Widening.**</span></span> <span data-ttu-id="2359f-131">Todos os tipos de dados e todos os tipos de referência ampliam para o `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="2359f-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="2359f-132">Isso significa que você pode converter qualquer tipo para `Object` sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="2359f-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

  <span data-ttu-id="2359f-133">No entanto, se você converter entre tipos de valor e `Object` , Visual Basic executar operações chamadas *Boxing* e *unboxing*, o que torna a execução mais lenta.</span><span class="sxs-lookup"><span data-stu-id="2359f-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>

- <span data-ttu-id="2359f-134">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="2359f-134">**Type Characters.**</span></span> <span data-ttu-id="2359f-135">`Object`Não tem caractere de tipo literal ou caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="2359f-135">`Object` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="2359f-136">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="2359f-136">**Framework Type.**</span></span> <span data-ttu-id="2359f-137">O tipo correspondente no .NET Framework é a <xref:System.Object?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="2359f-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>

## <a name="example"></a><span data-ttu-id="2359f-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2359f-138">Example</span></span>

<span data-ttu-id="2359f-139">O exemplo a seguir ilustra uma `Object` variável que aponta para uma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="2359f-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a><span data-ttu-id="2359f-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="2359f-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="2359f-141">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="2359f-141">Data Types</span></span>](index.md)
- [<span data-ttu-id="2359f-142">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="2359f-142">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="2359f-143">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="2359f-143">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="2359f-144">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="2359f-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="2359f-145">Como determinar se dois objetos estão relacionados</span><span class="sxs-lookup"><span data-stu-id="2359f-145">How to: Determine Whether Two Objects Are Related</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="2359f-146">Como determinar se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="2359f-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
