---
title: Operadores de comparação
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: fcbb9052a79fa4b20b5a0f8fdc15de73d55a4281
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873443"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="b5196-102">Operadores de comparação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5196-102">Comparison Operators (Visual Basic)</span></span>

<span data-ttu-id="b5196-103">A seguir estão os operadores de comparação definidos no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5196-103">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="b5196-104">`<` operador</span><span class="sxs-lookup"><span data-stu-id="b5196-104">`<` operator</span></span>

 <span data-ttu-id="b5196-105">`<=` operador</span><span class="sxs-lookup"><span data-stu-id="b5196-105">`<=` operator</span></span>

 <span data-ttu-id="b5196-106">`>` operador</span><span class="sxs-lookup"><span data-stu-id="b5196-106">`>` operator</span></span>

 <span data-ttu-id="b5196-107">`>=` operador</span><span class="sxs-lookup"><span data-stu-id="b5196-107">`>=` operator</span></span>

 <span data-ttu-id="b5196-108">`=` operador</span><span class="sxs-lookup"><span data-stu-id="b5196-108">`=` operator</span></span>

 <span data-ttu-id="b5196-109">`<>` operador</span><span class="sxs-lookup"><span data-stu-id="b5196-109">`<>` operator</span></span>

 [<span data-ttu-id="b5196-110">Operador Is</span><span class="sxs-lookup"><span data-stu-id="b5196-110">Is Operator</span></span>](is-operator.md)

 [<span data-ttu-id="b5196-111">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="b5196-111">IsNot Operator</span></span>](isnot-operator.md)

 [<span data-ttu-id="b5196-112">Operador Like</span><span class="sxs-lookup"><span data-stu-id="b5196-112">Like Operator</span></span>](like-operator.md)

 <span data-ttu-id="b5196-113">Esses operadores comparam duas expressões para determinar se elas são iguais e se não, como diferem.</span><span class="sxs-lookup"><span data-stu-id="b5196-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="b5196-114">`Is`, `IsNot` e `Like` são discutidos em detalhes em páginas de ajuda separadas.</span><span class="sxs-lookup"><span data-stu-id="b5196-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="b5196-115">Os operadores de comparação relacional são discutidos em detalhes nesta página.</span><span class="sxs-lookup"><span data-stu-id="b5196-115">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5196-116">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5196-116">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="b5196-117">Partes</span><span class="sxs-lookup"><span data-stu-id="b5196-117">Parts</span></span>

 `result`  
 <span data-ttu-id="b5196-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b5196-118">Required.</span></span> <span data-ttu-id="b5196-119">Um `Boolean` valor que representa o resultado da comparação.</span><span class="sxs-lookup"><span data-stu-id="b5196-119">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="b5196-120">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="b5196-120">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="b5196-121">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b5196-121">Required.</span></span> <span data-ttu-id="b5196-122">Qualquer expressão.</span><span class="sxs-lookup"><span data-stu-id="b5196-122">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="b5196-123">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b5196-123">Required.</span></span> <span data-ttu-id="b5196-124">Qualquer operador de comparação relacional.</span><span class="sxs-lookup"><span data-stu-id="b5196-124">Any relational comparison operator.</span></span>

 <span data-ttu-id="b5196-125">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="b5196-125">`object1`, `object2`</span></span>  
 <span data-ttu-id="b5196-126">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b5196-126">Required.</span></span> <span data-ttu-id="b5196-127">Qualquer nome de objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="b5196-127">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="b5196-128">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b5196-128">Required.</span></span> <span data-ttu-id="b5196-129">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="b5196-129">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="b5196-130">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b5196-130">Required.</span></span> <span data-ttu-id="b5196-131">Qualquer `String` expressão ou intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b5196-131">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5196-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5196-132">Remarks</span></span>

 <span data-ttu-id="b5196-133">A tabela a seguir contém uma lista dos operadores de comparação relacional e as condições que determinam se `result` é `True` ou `False` .</span><span class="sxs-lookup"><span data-stu-id="b5196-133">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="b5196-134">Operador</span><span class="sxs-lookup"><span data-stu-id="b5196-134">Operator</span></span>|<span data-ttu-id="b5196-135">`True` se</span><span class="sxs-lookup"><span data-stu-id="b5196-135">`True` if</span></span>|<span data-ttu-id="b5196-136">`False` se</span><span class="sxs-lookup"><span data-stu-id="b5196-136">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="b5196-137">`<` (Menor que)</span><span class="sxs-lookup"><span data-stu-id="b5196-137">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="b5196-138">`<=` (Menor que ou igual a)</span><span class="sxs-lookup"><span data-stu-id="b5196-138">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="b5196-139">`>` (Maior que)</span><span class="sxs-lookup"><span data-stu-id="b5196-139">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="b5196-140">`>=` (Maior ou igual a)</span><span class="sxs-lookup"><span data-stu-id="b5196-140">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="b5196-141">`=` (Igual a)</span><span class="sxs-lookup"><span data-stu-id="b5196-141">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="b5196-142">`<>` (Diferente de)</span><span class="sxs-lookup"><span data-stu-id="b5196-142">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="b5196-143">O [operador =](assignment-operator.md) também é usado como um operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="b5196-143">The [= Operator](assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="b5196-144">O `Is` operador, o `IsNot` operador e o `Like` operador têm funcionalidades de comparação específicas que diferem dos operadores na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="b5196-144">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="b5196-145">Comparando números</span><span class="sxs-lookup"><span data-stu-id="b5196-145">Comparing Numbers</span></span>

 <span data-ttu-id="b5196-146">Quando você compara uma expressão do tipo `Single` a um do tipo `Double` , a `Single` expressão é convertida em `Double` .</span><span class="sxs-lookup"><span data-stu-id="b5196-146">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="b5196-147">Esse comportamento é oposto ao comportamento encontrado no Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="b5196-147">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="b5196-148">Da mesma forma, quando você compara uma expressão do tipo `Decimal` com uma expressão do tipo `Single` ou `Double` , a `Decimal` expressão é convertida em `Single` ou `Double` .</span><span class="sxs-lookup"><span data-stu-id="b5196-148">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="b5196-149">Para `Decimal` expressões, qualquer valor fracionário menor que 1e 28 pode ser perdido.</span><span class="sxs-lookup"><span data-stu-id="b5196-149">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="b5196-150">Essa perda de valor fracionário pode fazer com que dois valores sejam comparados como iguais quando não forem.</span><span class="sxs-lookup"><span data-stu-id="b5196-150">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="b5196-151">Por esse motivo, você deve tomar cuidado ao usar igualdade ( `=` ) para comparar duas variáveis de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="b5196-151">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="b5196-152">É mais seguro testar se o valor absoluto da diferença entre os dois números é menor que uma pequena tolerância aceitável.</span><span class="sxs-lookup"><span data-stu-id="b5196-152">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="b5196-153">Irprecisão de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="b5196-153">Floating-point Imprecision</span></span>

 <span data-ttu-id="b5196-154">Quando você trabalha com números de ponto flutuante, tenha em mente que eles nem sempre têm uma representação precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="b5196-154">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="b5196-155">Isso pode levar a resultados inesperados de determinadas operações, como comparação de valor e o [operador Mod](mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b5196-155">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](mod-operator.md).</span></span> <span data-ttu-id="b5196-156">Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="b5196-156">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="b5196-157">Comparando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="b5196-157">Comparing Strings</span></span>

 <span data-ttu-id="b5196-158">Quando você compara Cadeias de caracteres, as expressões de cadeia são avaliadas com base na ordem de classificação alfabética, que depende da `Option Compare` configuração.</span><span class="sxs-lookup"><span data-stu-id="b5196-158">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="b5196-159">`Option Compare Binary` baseia as comparações de cadeia de caracteres em uma ordem de classificação derivada das representações binárias internas dos caracteres.</span><span class="sxs-lookup"><span data-stu-id="b5196-159">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="b5196-160">A ordem de classificação é determinada pela página de código.</span><span class="sxs-lookup"><span data-stu-id="b5196-160">The sort order is determined by the code page.</span></span> <span data-ttu-id="b5196-161">O exemplo a seguir mostra uma ordem de classificação binária típica.</span><span class="sxs-lookup"><span data-stu-id="b5196-161">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="b5196-162">`Option Compare Text` baseia comparações de cadeia de caracteres em uma ordem de classificação textual, que não diferencia maiúsculas de minúsculas, determinada pela localidade do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5196-162">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="b5196-163">Quando você define `Option Compare Text` e classifica os caracteres no exemplo anterior, a ordem de classificação de texto a seguir se aplica:</span><span class="sxs-lookup"><span data-stu-id="b5196-163">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="b5196-164">Dependência de localidade</span><span class="sxs-lookup"><span data-stu-id="b5196-164">Locale Dependence</span></span>

 <span data-ttu-id="b5196-165">Quando você define `Option Compare Text` , o resultado de uma comparação de cadeia de caracteres pode depender da localidade em que o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="b5196-165">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="b5196-166">Dois caracteres podem ser comparados como iguais em uma localidade, mas não em outro.</span><span class="sxs-lookup"><span data-stu-id="b5196-166">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="b5196-167">Se você estiver usando uma comparação de cadeias de caracteres para tomar decisões importantes, como, por exemplo, se deve aceitar uma tentativa de fazer logon, você deve ser alertado sobre a confidencialidade da localidade.</span><span class="sxs-lookup"><span data-stu-id="b5196-167">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="b5196-168">Considere a configuração `Option Compare Binary` ou a chamada do <xref:Microsoft.VisualBasic.Strings.StrComp%2A> , que leva a localidade em conta.</span><span class="sxs-lookup"><span data-stu-id="b5196-168">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="b5196-169">Programação sem tipo com operadores de comparação relacionais</span><span class="sxs-lookup"><span data-stu-id="b5196-169">Typeless Programming with Relational Comparison Operators</span></span>

 <span data-ttu-id="b5196-170">O uso de operadores de comparação relacional com `Object` expressões não é permitido em `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="b5196-170">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="b5196-171">Quando `Option Strict` é `Off` , e `expression1` ou `expression2` é uma `Object` expressão, os tipos de tempo de execução determinam como eles são comparados.</span><span class="sxs-lookup"><span data-stu-id="b5196-171">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="b5196-172">A tabela a seguir mostra como as expressões são comparadas e o resultado da comparação, dependendo do tipo de tempo de execução dos operandos.</span><span class="sxs-lookup"><span data-stu-id="b5196-172">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="b5196-173">Se os operandos forem</span><span class="sxs-lookup"><span data-stu-id="b5196-173">If operands are</span></span>|<span data-ttu-id="b5196-174">A comparação é</span><span class="sxs-lookup"><span data-stu-id="b5196-174">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="b5196-175">Mesmo `String`</span><span class="sxs-lookup"><span data-stu-id="b5196-175">Both `String`</span></span>|<span data-ttu-id="b5196-176">Comparação de classificação com base em características de classificação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b5196-176">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="b5196-177">Ambos numéricos</span><span class="sxs-lookup"><span data-stu-id="b5196-177">Both numeric</span></span>|<span data-ttu-id="b5196-178">Objetos convertidos em `Double` , comparação numérica.</span><span class="sxs-lookup"><span data-stu-id="b5196-178">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="b5196-179">Um numérico e um `String`</span><span class="sxs-lookup"><span data-stu-id="b5196-179">One numeric and one `String`</span></span>|<span data-ttu-id="b5196-180">O `String` é convertido em a `Double` e uma comparação numérica é executada.</span><span class="sxs-lookup"><span data-stu-id="b5196-180">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="b5196-181">Se o `String` não puder ser convertido em `Double` , um <xref:System.InvalidCastException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="b5196-181">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="b5196-182">Ou ambos são tipos de referência diferentes de `String`</span><span class="sxs-lookup"><span data-stu-id="b5196-182">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="b5196-183"><xref:System.InvalidCastException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="b5196-183">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="b5196-184">Comparações numéricas tratam `Nothing` como 0.</span><span class="sxs-lookup"><span data-stu-id="b5196-184">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="b5196-185">Comparações de cadeia de caracteres tratam `Nothing` como `""` (uma cadeia de caracteres vazia).</span><span class="sxs-lookup"><span data-stu-id="b5196-185">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="b5196-186">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="b5196-186">Overloading</span></span>

 <span data-ttu-id="b5196-187">Os operadores de comparação relacional ( `<` .</span><span class="sxs-lookup"><span data-stu-id="b5196-187">The relational comparison operators (`<`.</span></span> <span data-ttu-id="b5196-188">`<=`,,,, `>` `>=` `=` `<>` ) podem ser *sobrecarregados*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="b5196-188">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b5196-189">Se o seu código usar qualquer um desses operadores em uma classe ou estrutura desse tipo, certifique-se de entender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="b5196-189">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="b5196-190">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b5196-190">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="b5196-191">Observe que o [operador =](assignment-operator.md) pode ser sobrecarregado apenas como um operador de comparação relacional, não como um operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="b5196-191">Notice that the [= Operator](assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="b5196-192">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5196-192">Example</span></span>

 <span data-ttu-id="b5196-193">O exemplo a seguir mostra vários usos de operadores de comparação relacionais, que você usa para comparar expressões.</span><span class="sxs-lookup"><span data-stu-id="b5196-193">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="b5196-194">Operadores de comparação relacional retornam um `Boolean` resultado que representa se a expressão declarada deve ou não ser avaliada `True` .</span><span class="sxs-lookup"><span data-stu-id="b5196-194">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="b5196-195">Quando você aplica os `>` `<` operadores e às cadeias de caracteres, a comparação é feita usando a ordem de classificação alfabética normal das cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b5196-195">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="b5196-196">Essa ordem pode ser dependente de sua configuração de localidade.</span><span class="sxs-lookup"><span data-stu-id="b5196-196">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="b5196-197">Se a classificação diferencia maiúsculas de minúsculas ou não depende da configuração de [comparação de opção](../statements/option-compare-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="b5196-197">Whether the sort is case-sensitive or not depends on the [Option Compare](../statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="b5196-198">No exemplo anterior, a primeira comparação retorna `False` e as comparações restantes são retornadas `True` .</span><span class="sxs-lookup"><span data-stu-id="b5196-198">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5196-199">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5196-199">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="b5196-200">= Operador</span><span class="sxs-lookup"><span data-stu-id="b5196-200">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="b5196-201">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5196-201">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b5196-202">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="b5196-202">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b5196-203">Solução de problemas de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b5196-203">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="b5196-204">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5196-204">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
