---
title: Tipos de dados constante e literal
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 03d693653cd166bbf1096031f1a864b492e2e896
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086290"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="b8352-102">Tipos de dados constante e literal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8352-102">Constant and Literal Data Types (Visual Basic)</span></span>

<span data-ttu-id="b8352-103">Um literal é um valor que é expresso como ele mesmo, e não como o valor de uma variável ou o resultado de uma expressão, como o número 3 ou a cadeia de caracteres "Olá".</span><span class="sxs-lookup"><span data-stu-id="b8352-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="b8352-104">Uma constante é um nome significativo que assume o lugar de um literal e retém esse mesmo valor em todo o programa, em oposição a uma variável, cujo valor pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="b8352-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="b8352-105">Quando [Option Infer](../../../language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../language-reference/statements/option-strict-statement.md) é `On` , você deve declarar todas as constantes explicitamente com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b8352-105">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="b8352-106">No exemplo a seguir, o tipo de dados de `MyByte` é declarado explicitamente como tipo de dados `Byte` :</span><span class="sxs-lookup"><span data-stu-id="b8352-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="b8352-107">Quando `Option Infer` é `On` ou `Option Strict` é `Off` , você pode declarar uma constante sem especificar um tipo de dados com uma `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="b8352-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="b8352-108">O compilador determina o tipo da constante do tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="b8352-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="b8352-109">Um literal inteiro numérico é convertido por padrão no `Integer` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b8352-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="b8352-110">O tipo de dados padrão para números de ponto flutuante é `Double` , e as palavras-chave `True` e `False` especificam uma `Boolean` constante.</span><span class="sxs-lookup"><span data-stu-id="b8352-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="b8352-111">Literais e coerção de tipo</span><span class="sxs-lookup"><span data-stu-id="b8352-111">Literals and Type Coercion</span></span>  

 <span data-ttu-id="b8352-112">Em alguns casos, talvez você queira forçar um literal para um tipo de dados específico; por exemplo, ao atribuir um valor literal integral especialmente grande a uma variável do tipo `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="b8352-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="b8352-113">O exemplo a seguir produz um erro:</span><span class="sxs-lookup"><span data-stu-id="b8352-113">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="b8352-114">O erro resulta da representação do literal.</span><span class="sxs-lookup"><span data-stu-id="b8352-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="b8352-115">O `Decimal` tipo de dados pode conter um valor grande, mas o literal é representado implicitamente como um `Long` , que não pode.</span><span class="sxs-lookup"><span data-stu-id="b8352-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="b8352-116">Você pode forçar um literal para um tipo de dados específico de duas maneiras: anexando um caractere de tipo a ele ou colocando-o entre caracteres delimitadores.</span><span class="sxs-lookup"><span data-stu-id="b8352-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="b8352-117">Um caractere de tipo ou caracteres delimitadores devem anteceder e/ou seguir o literal imediatamente, sem nenhum espaço intermediário ou caracteres de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="b8352-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="b8352-118">Para que o exemplo anterior funcione, você pode acrescentar o `D` caractere de tipo ao literal, o que faz com que ele seja representado como `Decimal` :</span><span class="sxs-lookup"><span data-stu-id="b8352-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="b8352-119">O exemplo a seguir demonstra o uso correto de caracteres de tipo e caracteres de delimitador:</span><span class="sxs-lookup"><span data-stu-id="b8352-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="b8352-120">A tabela a seguir mostra os caracteres delimitadores e os caracteres de tipo disponíveis no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b8352-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="b8352-121">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="b8352-121">Data type</span></span>|<span data-ttu-id="b8352-122">Caractere delimitador</span><span class="sxs-lookup"><span data-stu-id="b8352-122">Enclosing character</span></span>|<span data-ttu-id="b8352-123">Caractere de tipo acrescentado</span><span class="sxs-lookup"><span data-stu-id="b8352-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="b8352-124">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-124">(none)</span></span>|<span data-ttu-id="b8352-125">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="b8352-126">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-126">(none)</span></span>|<span data-ttu-id="b8352-127">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="b8352-128">"</span><span class="sxs-lookup"><span data-stu-id="b8352-128">"</span></span>|<span data-ttu-id="b8352-129">C</span><span class="sxs-lookup"><span data-stu-id="b8352-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="b8352-130">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="b8352-131">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-131">(none)</span></span>|<span data-ttu-id="b8352-132">D ou @</span><span class="sxs-lookup"><span data-stu-id="b8352-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="b8352-133">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-133">(none)</span></span>|<span data-ttu-id="b8352-134">R ou #</span><span class="sxs-lookup"><span data-stu-id="b8352-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="b8352-135">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-135">(none)</span></span>|<span data-ttu-id="b8352-136">I ou%</span><span class="sxs-lookup"><span data-stu-id="b8352-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="b8352-137">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-137">(none)</span></span>|<span data-ttu-id="b8352-138">L ou &</span><span class="sxs-lookup"><span data-stu-id="b8352-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="b8352-139">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-139">(none)</span></span>|<span data-ttu-id="b8352-140">S</span><span class="sxs-lookup"><span data-stu-id="b8352-140">S</span></span>|  
|`Single`|<span data-ttu-id="b8352-141">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-141">(none)</span></span>|<span data-ttu-id="b8352-142">F ou!</span><span class="sxs-lookup"><span data-stu-id="b8352-142">F or !</span></span>|  
|`String`|<span data-ttu-id="b8352-143">"</span><span class="sxs-lookup"><span data-stu-id="b8352-143">"</span></span>|<span data-ttu-id="b8352-144">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="b8352-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8352-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8352-145">See also</span></span>

- [<span data-ttu-id="b8352-146">Constantes definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="b8352-146">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="b8352-147">Como declarar uma constante</span><span class="sxs-lookup"><span data-stu-id="b8352-147">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="b8352-148">Visão geral de constantes</span><span class="sxs-lookup"><span data-stu-id="b8352-148">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="b8352-149">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="b8352-149">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="b8352-150">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="b8352-150">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="b8352-151">Visão geral de enumerações</span><span class="sxs-lookup"><span data-stu-id="b8352-151">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="b8352-152">Como declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="b8352-152">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="b8352-153">Enumerações e qualificação de nome</span><span class="sxs-lookup"><span data-stu-id="b8352-153">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="b8352-154">Data Types</span><span class="sxs-lookup"><span data-stu-id="b8352-154">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="b8352-155">Constantes e enumerações</span><span class="sxs-lookup"><span data-stu-id="b8352-155">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
