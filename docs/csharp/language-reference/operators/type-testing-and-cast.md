---
title: Operadores cast e teste de tipo – Referência de C#
description: Saiba mais sobre os operadores do C# que você pode usar para verificar o tipo de um resultado de expressão e convertê-lo para outro tipo, se necessário.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: c29833ece83e386446aaf0a5d242bda366cbfbb0
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239034"
---
# <a name="type-testing-and-cast-operators-c-reference"></a><span data-ttu-id="5e9cf-103">Operadores cast e teste de tipo (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="5e9cf-103">Type-testing and cast operators (C# reference)</span></span>

<span data-ttu-id="5e9cf-104">Você pode usar os seguintes operadores para executar a verificação de tipo ou conversão de tipo:</span><span class="sxs-lookup"><span data-stu-id="5e9cf-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="5e9cf-105">[operador is](#is-operator): para verificar se o tipo de runtime de uma expressão é compatível com um determinado tipo</span><span class="sxs-lookup"><span data-stu-id="5e9cf-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="5e9cf-106">[operador as](#as-operator): para converter explicitamente uma expressão em um determinado tipo, se o tipo de runtime for compatível com esse tipo</span><span class="sxs-lookup"><span data-stu-id="5e9cf-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="5e9cf-107">[operador cast ()](#cast-operator-): para executar uma conversão explícita</span><span class="sxs-lookup"><span data-stu-id="5e9cf-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="5e9cf-108">[operador typeof](#typeof-operator): para obter a instância <xref:System.Type?displayProperty=nameWithType> para um tipo</span><span class="sxs-lookup"><span data-stu-id="5e9cf-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="5e9cf-109">Operador is</span><span class="sxs-lookup"><span data-stu-id="5e9cf-109">is operator</span></span>

<span data-ttu-id="5e9cf-110">O operador `is` verifica se o tipo de runtime de um resultado de expressão é compatível com um determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="5e9cf-111">A partir C# do 7,0, o operador de `is` também testa um resultado de expressão em relação a um padrão.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="5e9cf-112">A expressão com o operador `is` de teste de tipo tem o seguinte formato</span><span class="sxs-lookup"><span data-stu-id="5e9cf-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="5e9cf-113">em que `E` é uma expressão que retorna um valor e `T` é o nome de um tipo ou um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="5e9cf-114">`E` não pode ser um método anônimo ou uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="5e9cf-115">A expressão `E is T` retorna `true` se o resultado de `E` não for nulo e puder ser convertido para o tipo `T` por uma conversão de referência, uma conversão boxing ou uma conversão unboxing; caso contrário, retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="5e9cf-116">O operador `is` não considera conversões definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="5e9cf-117">O exemplo a seguir demonstra que o operador `is` retorna `true` se o tipo de runtime de um resultado da expressão é derivado de um determinado tipo, ou seja, existe uma conversão de referência entre tipos:</span><span class="sxs-lookup"><span data-stu-id="5e9cf-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="5e9cf-118">O exemplo a seguir mostra que o operador de `is` leva em consideração as conversões boxing e unboxing, mas não considera as [conversões numéricas](../builtin-types/numeric-conversions.md):</span><span class="sxs-lookup"><span data-stu-id="5e9cf-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="5e9cf-119">Para saber mais sobre conversões em C#, confira o capítulo [Conversões](~/_csharplang/spec/conversions.md) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5e9cf-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="5e9cf-120">Teste de tipo com correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="5e9cf-120">Type testing with pattern matching</span></span>

<span data-ttu-id="5e9cf-121">A partir C# do 7,0, o operador de `is` também testa um resultado de expressão em relação a um padrão.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="5e9cf-122">Em particular, ele dá suporte ao padrão de tipo da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5e9cf-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="5e9cf-123">em que `E` é uma expressão que retorna um valor, `T` é o nome de um tipo ou um parâmetro de tipo, e `v` é uma nova variável local do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="5e9cf-124">Se o resultado de `E` não for nulo e puder ser convertido para `T` por uma conversão de referência, boxing ou unboxing, a expressão `E is T v` retornará `true` e o valor convertido do resultado de `E`será atribuído à variável `v`.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="5e9cf-125">O exemplo a seguir demonstra o uso do operador `is` com um padrão de tipo:</span><span class="sxs-lookup"><span data-stu-id="5e9cf-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="5e9cf-126">Para saber mais sobre o padrão de tipos e outros padrões com suporte, confira [Correspondência de padrões com is](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="5e9cf-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="5e9cf-127">Operador as</span><span class="sxs-lookup"><span data-stu-id="5e9cf-127">as operator</span></span>

<span data-ttu-id="5e9cf-128">O operador `as` converte explicitamente o resultado de uma expressão para uma determinada referência ou tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="5e9cf-129">Se a conversão não for possível, o operador `as` retorna `null`.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="5e9cf-130">Ao contrário do [operador cast ()](#cast-operator-), o operador `as` nunca lança uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="5e9cf-131">A expressão da forma</span><span class="sxs-lookup"><span data-stu-id="5e9cf-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="5e9cf-132">em que `E` é uma expressão que retorna um valor e `T` é o nome de um tipo ou um parâmetro de tipo, produz o mesmo resultado que</span><span class="sxs-lookup"><span data-stu-id="5e9cf-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="5e9cf-133">exceto que `E` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="5e9cf-134">O operador `as` considera apenas as conversões de referência, anulável, boxing e unboxing.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="5e9cf-135">Não é possível usar o operador `as` para executar uma conversão definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="5e9cf-136">Para fazer isso, use o operador [cast ()](#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="5e9cf-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="5e9cf-137">O exemplo a seguir demonstra o uso do operador `as`:</span><span class="sxs-lookup"><span data-stu-id="5e9cf-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="5e9cf-138">Como mostrado no exemplo anterior, você precisa comparar o resultado da expressão `as` com `null` para verificar se uma conversão foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="5e9cf-139">A partir C# do 7,0, você pode usar o [operador is](#type-testing-with-pattern-matching) para testar se a conversão é bem sucedido e, se tiver sucesso, atribuir seu resultado a uma nova variável.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="5e9cf-140">Operador cast ()</span><span class="sxs-lookup"><span data-stu-id="5e9cf-140">Cast operator ()</span></span>

<span data-ttu-id="5e9cf-141">Uma expressão de conversão do formulário `(T)E` realiza uma conversão explícita do resultado da expressão `E` para o tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="5e9cf-142">Se não existir nenhuma conversão explícita do tipo `E` para o tipo `T`, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="5e9cf-143">No tempo de execução, uma conversão explícita pode não ter êxito e uma expressão de conversão pode lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="5e9cf-144">O exemplo a seguir demonstra conversões numéricas e de referência explícitas:</span><span class="sxs-lookup"><span data-stu-id="5e9cf-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="5e9cf-145">Para saber mais sobre conversões explícitas sem suporte, confira a seção [Conversões explícitas](~/_csharplang/spec/conversions.md#explicit-conversions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5e9cf-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="5e9cf-146">Para saber mais sobre como definir uma conversão de tipo explícito ou implícito personalizado, confira [Operadores de conversão definidos pelo usuário](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5e9cf-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="5e9cf-147">Outros usos de ()</span><span class="sxs-lookup"><span data-stu-id="5e9cf-147">Other usages of ()</span></span>

<span data-ttu-id="5e9cf-148">Você também usa parênteses para [ chamar um método ou chamar um delegado ](member-access-operators.md#invocation-operator-).</span><span class="sxs-lookup"><span data-stu-id="5e9cf-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="5e9cf-149">Outro uso dos parênteses é ajustar a ordem na qual as operações em uma expressão são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="5e9cf-150">Para saber mais, confira [Operadores C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="5e9cf-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="5e9cf-151">Operador typeof</span><span class="sxs-lookup"><span data-stu-id="5e9cf-151">typeof operator</span></span>

<span data-ttu-id="5e9cf-152">O operador `typeof` obtém a instância <xref:System.Type?displayProperty=nameWithType> para um tipo.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="5e9cf-153">O argumento do operador `typeof` deve ser o nome de um tipo ou um parâmetro de tipo, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5e9cf-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="5e9cf-154">Você também pode usar o operador `typeof` com tipos genéricos não associados.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-154">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="5e9cf-155">O nome de um tipo genérico não associado deve conter o número apropriado de vírgulas, que é um a menos que o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="5e9cf-156">O exemplo a seguir mostra o uso do operador `typeof` com um tipo genérico não associado:</span><span class="sxs-lookup"><span data-stu-id="5e9cf-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="5e9cf-157">Uma expressão não pode ser um argumento do operador `typeof`.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="5e9cf-158">Para obter a instância de <xref:System.Type?displayProperty=nameWithType> para o tipo de tempo de execução de um resultado de expressão, use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="5e9cf-159">Teste de tipo com o operador `typeof`</span><span class="sxs-lookup"><span data-stu-id="5e9cf-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="5e9cf-160">Use o operador `typeof` para verificar se o tipo de runtime do resultado da expressão corresponde exatamente a um determinado tipo.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="5e9cf-161">O exemplo a seguir demonstra a diferença entre a verificação de tipo executada com o operador `typeof` e o [operador is](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="5e9cf-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="5e9cf-162">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="5e9cf-162">Operator overloadability</span></span>

<span data-ttu-id="5e9cf-163">Os operadores `is`, `as`e `typeof` não podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="5e9cf-164">Um tipo definido pelo usuário não pode sobrecarregar o operador `()`, mas pode definir conversões de tipo customizado que podem ser executadas por uma expressão de conversão.</span><span class="sxs-lookup"><span data-stu-id="5e9cf-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="5e9cf-165">Para saber mais, confira [Operadores de conversão definidos pelo usuário](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5e9cf-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5e9cf-166">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="5e9cf-166">C# language specification</span></span>

<span data-ttu-id="5e9cf-167">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="5e9cf-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5e9cf-168">Operador is</span><span class="sxs-lookup"><span data-stu-id="5e9cf-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="5e9cf-169">Operador as</span><span class="sxs-lookup"><span data-stu-id="5e9cf-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="5e9cf-170">Expressões cast</span><span class="sxs-lookup"><span data-stu-id="5e9cf-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="5e9cf-171">Operador typeof</span><span class="sxs-lookup"><span data-stu-id="5e9cf-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="5e9cf-172">Confira também</span><span class="sxs-lookup"><span data-stu-id="5e9cf-172">See also</span></span>

- [<span data-ttu-id="5e9cf-173">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5e9cf-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5e9cf-174">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="5e9cf-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="5e9cf-175">Como converter com segurança usando correspondência de padrões e os operadores is e as</span><span class="sxs-lookup"><span data-stu-id="5e9cf-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="5e9cf-176">Genéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="5e9cf-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
