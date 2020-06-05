---
title: 'Como: Definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 3b1f47250453c32735d633b98da0bd0ddb1ed5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393851"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="2aa19-102">Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2aa19-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="2aa19-103">Você pode definir uma classe na qual é possível criar objetos que fornecem funcionalidade idêntica em diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="2aa19-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="2aa19-104">Para fazer isso, você deve especificar um ou mais *parâmetros de tipo* na definição.</span><span class="sxs-lookup"><span data-stu-id="2aa19-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="2aa19-105">A classe pode servir como um modelo para objetos que usam vários tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="2aa19-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="2aa19-106">Uma classe definida dessa maneira é chamada de *classe genérica*.</span><span class="sxs-lookup"><span data-stu-id="2aa19-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="2aa19-107">A vantagem de definir uma classe genérica é que você a define apenas uma vez, e seu código pode usá-la para criar vários objetos que usam uma ampla variedade de tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="2aa19-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="2aa19-108">Isso resulta em um melhor desempenho do que definir a classe com o `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="2aa19-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="2aa19-109">Além das classes, você também pode definir e usar estruturas genéricas, interfaces, procedimentos e delegados.</span><span class="sxs-lookup"><span data-stu-id="2aa19-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="2aa19-110">Para definir uma classe com um parâmetro de tipo</span><span class="sxs-lookup"><span data-stu-id="2aa19-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="2aa19-111">Defina a classe da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="2aa19-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="2aa19-112">Adicione `(Of` *typeparameter* `)` imediatamente após o nome da classe para especificar um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="2aa19-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="2aa19-113">Se você tiver mais de um parâmetro de tipo, crie uma lista separada por vírgulas dentro dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="2aa19-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="2aa19-114">Não repita a `Of` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="2aa19-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="2aa19-115">Se o seu código executar operações em um parâmetro de tipo diferente de atribuição simples, siga esse parâmetro de tipo com uma `As` cláusula para adicionar uma ou mais *restrições*.</span><span class="sxs-lookup"><span data-stu-id="2aa19-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="2aa19-116">Uma restrição garante que o tipo fornecido para esse parâmetro de tipo atenda a um requisito, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2aa19-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="2aa19-117">Dá suporte a uma operação, como `>` , que seu código executa</span><span class="sxs-lookup"><span data-stu-id="2aa19-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="2aa19-118">Dá suporte a um membro, como um método, que seu código acessa</span><span class="sxs-lookup"><span data-stu-id="2aa19-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="2aa19-119">Expõe um construtor sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="2aa19-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="2aa19-120">Se você não especificar nenhuma restrição, as únicas operações e membros que seu código pode usar são aquelas com suporte pelo [tipo de dados Object](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="2aa19-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="2aa19-121">Para obter mais informações, consulte [lista de tipos](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="2aa19-121">For more information, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="2aa19-122">Identifique cada membro de classe que deve ser declarado com um tipo fornecido e declare-o `As` `typeparameter` .</span><span class="sxs-lookup"><span data-stu-id="2aa19-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="2aa19-123">Isso se aplica ao armazenamento interno, aos parâmetros de procedimento e aos valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="2aa19-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="2aa19-124">Certifique-se de que seu código usa apenas operações e métodos com suporte de qualquer tipo de dados ao qual possa fornecer `itemType` .</span><span class="sxs-lookup"><span data-stu-id="2aa19-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="2aa19-125">O exemplo a seguir define uma classe que gerencia uma lista muito simples.</span><span class="sxs-lookup"><span data-stu-id="2aa19-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="2aa19-126">Ele contém a lista na matriz interna `items` e o código de uso pode declarar o tipo de dados dos elementos da lista.</span><span class="sxs-lookup"><span data-stu-id="2aa19-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="2aa19-127">Um construtor com parâmetros permite que o código de uso defina o limite superior de `items` e o construtor sem parâmetros define isso como 9 (para um total de 10 itens).</span><span class="sxs-lookup"><span data-stu-id="2aa19-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="2aa19-128">Você pode declarar uma classe de `simpleList` para manter uma lista de `Integer` valores, outra classe para manter uma lista de `String` valores e outra para conter `Date` valores.</span><span class="sxs-lookup"><span data-stu-id="2aa19-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="2aa19-129">Exceto para o tipo de dados dos membros da lista, os objetos criados a partir de todas essas classes se comportam de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="2aa19-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="2aa19-130">O argumento de tipo que o código usando fornece ao `itemType` pode ser um tipo intrínseco, como `Boolean` ou `Double` , uma estrutura, uma enumeração ou qualquer tipo de classe, incluindo um que seu aplicativo define.</span><span class="sxs-lookup"><span data-stu-id="2aa19-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="2aa19-131">Você pode testar a classe `simpleList` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2aa19-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="2aa19-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="2aa19-132">See also</span></span>

- [<span data-ttu-id="2aa19-133">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="2aa19-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="2aa19-134">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2aa19-134">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="2aa19-135">Componentes de independência de linguagem e componentes independentes da linguagem</span><span class="sxs-lookup"><span data-stu-id="2aa19-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="2aa19-136">Desse</span><span class="sxs-lookup"><span data-stu-id="2aa19-136">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="2aa19-137">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="2aa19-137">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="2aa19-138">Como: Usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="2aa19-138">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="2aa19-139">Tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="2aa19-139">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
