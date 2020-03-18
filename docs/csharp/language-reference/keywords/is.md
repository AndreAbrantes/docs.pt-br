---
title: is – Referência de C#
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: e64b690482419963a92764b2c97a42dbb231fbfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399633"
---
# <a name="is-c-reference"></a><span data-ttu-id="75baf-102">is (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="75baf-102">is (C# Reference)</span></span>

<span data-ttu-id="75baf-103">O operador `is` verifica se o resultado de uma expressão é compatível com um tipo fornecido ou (a partir do C# 7.0) testa uma expressão em relação a um padrão.</span><span class="sxs-lookup"><span data-stu-id="75baf-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="75baf-104">Saiba mais sobre o operador `is` de teste de tipo na seção [operador is](../operators/type-testing-and-cast.md#is-operator) do artigo [Operadores cast e teste de tipo](../operators/type-testing-and-cast.md).</span><span class="sxs-lookup"><span data-stu-id="75baf-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="75baf-105">Correspondência de padrões com `is`</span><span class="sxs-lookup"><span data-stu-id="75baf-105">Pattern matching with `is`</span></span>

<span data-ttu-id="75baf-106">Começando com o C# 7.0, as instruções `is` e [switch](switch.md) permitem a correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="75baf-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="75baf-107">A palavra-chave `is` dá suporte aos seguintes padrões:</span><span class="sxs-lookup"><span data-stu-id="75baf-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="75baf-108">[Padrão de tipo](#type-pattern), que testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="75baf-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="75baf-109">[Padrão constante](#constant-pattern), que testa se uma expressão é avaliada como um valor constante especificado.</span><span class="sxs-lookup"><span data-stu-id="75baf-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="75baf-110">[Padrão var](#var-pattern), uma correspondência que sempre é bem-sucedida e vincula o valor de uma expressão a uma nova variável local.</span><span class="sxs-lookup"><span data-stu-id="75baf-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="75baf-111">Padrão de tipo</span><span class="sxs-lookup"><span data-stu-id="75baf-111">Type pattern</span></span>

<span data-ttu-id="75baf-112">Ao usar o padrão de tipo para realizar a correspondência de padrões, `is` testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="75baf-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="75baf-113">Trata-se de uma extensão simples da instrução `is` que habilita a conversão e a avaliação de tipo concisas.</span><span class="sxs-lookup"><span data-stu-id="75baf-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="75baf-114">A forma geral do padrão de tipo `is` é:</span><span class="sxs-lookup"><span data-stu-id="75baf-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="75baf-115">Quando *expr* é uma expressão que avalia para uma instância de algum tipo, *tipo* é o nome do tipo para o qual o resultado de *expr* deve `true`ser convertido, e *varname* é o objeto para o qual o resultado de *expr* é convertido se o `is` teste for .</span><span class="sxs-lookup"><span data-stu-id="75baf-115">Where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span>

<span data-ttu-id="75baf-116">A expressão `is` será `true` se *expr* não for `null` e qualquer um dos seguintes for verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="75baf-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="75baf-117">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="75baf-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="75baf-118">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="75baf-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="75baf-119">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="75baf-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="75baf-120">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de runtime que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="75baf-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="75baf-121">O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="75baf-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="75baf-122">O *tipo de runtime* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="75baf-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="75baf-123">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="75baf-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="75baf-124">A partir do C# 7.1, *expr* pode ter um tipo de tempo de compilação definido por um parâmetro de tipo genérico e suas restrições.</span><span class="sxs-lookup"><span data-stu-id="75baf-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="75baf-125">Se *expr* for `true` e `is` for usado com uma instrução `if`, *varname* será atribuído somente dentro da instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="75baf-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="75baf-126">O escopo de *varname* é da expressão `is` até o final do bloco que envolve a instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="75baf-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="75baf-127">Usar *varname* em qualquer outro local gera um erro em tempo de compilação para o uso de uma variável que não foi atribuída.</span><span class="sxs-lookup"><span data-stu-id="75baf-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="75baf-128">O exemplo a seguir usa o padrão de tipo `is` para fornecer a implementação do método <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> de um tipo.</span><span class="sxs-lookup"><span data-stu-id="75baf-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="75baf-129">Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="75baf-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="75baf-130">O uso da correspondência de padrões de tipo produz código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null`.</span><span class="sxs-lookup"><span data-stu-id="75baf-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="75baf-131">O padrão de tipo `is` também produz código mais compacto ao determinar o tipo de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="75baf-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="75baf-132">O exemplo a seguir usa o padrão de tipo `is` para determinar se um objeto é uma instância de `Person` ou `Dog` antes de exibir o valor de uma propriedade adequada.</span><span class="sxs-lookup"><span data-stu-id="75baf-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="75baf-133">O código equivalente sem correspondência de padrões requer uma atribuição separada que inclui uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="75baf-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="75baf-134">Padrão de constante</span><span class="sxs-lookup"><span data-stu-id="75baf-134">Constant pattern</span></span>

<span data-ttu-id="75baf-135">Ao executar a correspondência de padrões com o padrão constante, `is` testa se uma expressão é igual a uma constante especificada.</span><span class="sxs-lookup"><span data-stu-id="75baf-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="75baf-136">No C# 6 e em versões anteriores, o padrão constante tem suporte da instrução [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="75baf-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="75baf-137">A partir do C# 7.0, ele também é compatível com a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="75baf-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="75baf-138">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="75baf-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="75baf-139">em que *expr* é a expressão a ser avaliada e *constant* é o valor a ser testado.</span><span class="sxs-lookup"><span data-stu-id="75baf-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="75baf-140">*constant* pode ser qualquer uma das expressões de constante a seguir:</span><span class="sxs-lookup"><span data-stu-id="75baf-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="75baf-141">Um valor literal.</span><span class="sxs-lookup"><span data-stu-id="75baf-141">A literal value.</span></span>

- <span data-ttu-id="75baf-142">O nome de uma variável `const` declarada.</span><span class="sxs-lookup"><span data-stu-id="75baf-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="75baf-143">Uma constante de enumeração.</span><span class="sxs-lookup"><span data-stu-id="75baf-143">An enumeration constant.</span></span>

<span data-ttu-id="75baf-144">A expressão de constante é avaliada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="75baf-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="75baf-145">Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="75baf-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="75baf-146">Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="75baf-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="75baf-147">O exemplo a seguir combina os padrões de tipo e constante para testar se um objeto é uma instância de `Dice` e, caso seja, para determinar se o valor de uma distribuição de dados é 6.</span><span class="sxs-lookup"><span data-stu-id="75baf-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="75baf-148">É possível verificar em busca de `null` usando o padrão de constante.</span><span class="sxs-lookup"><span data-stu-id="75baf-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="75baf-149">A palavra-chave `null` é compatível com a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="75baf-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="75baf-150">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="75baf-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="75baf-151">O exemplo a seguir demonstra uma comparação de verificações de `null`:</span><span class="sxs-lookup"><span data-stu-id="75baf-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="75baf-152">Padrão var</span><span class="sxs-lookup"><span data-stu-id="75baf-152">var pattern</span></span>

<span data-ttu-id="75baf-153">Um padrão combina `var` com o padrão sempre tem sucesso.</span><span class="sxs-lookup"><span data-stu-id="75baf-153">A pattern match with the `var` pattern always succeeds.</span></span> <span data-ttu-id="75baf-154">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="75baf-154">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="75baf-155">Quando o valor de *expr* é sempre atribuído a uma variável local chamada *varname*.</span><span class="sxs-lookup"><span data-stu-id="75baf-155">Where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="75baf-156">*varname* é uma variável do mesmo tipo que o tipo de tempo de compilação de *expr*.</span><span class="sxs-lookup"><span data-stu-id="75baf-156">*varname* is a variable of the same type as the compile-time type of *expr*.</span></span>

<span data-ttu-id="75baf-157">Se *expr* avaliar `null`, `is` a `true` expressão produz `null` e atribui ao *varname*.</span><span class="sxs-lookup"><span data-stu-id="75baf-157">If *expr* evaluates to `null`, the `is` expression produces `true` and assigns `null` to *varname*.</span></span> <span data-ttu-id="75baf-158">O padrão var é um `is` dos poucos usos que produz `true` por um `null` valor.</span><span class="sxs-lookup"><span data-stu-id="75baf-158">The var pattern is one of the few uses of `is` that produces `true` for a `null` value.</span></span>

<span data-ttu-id="75baf-159">Você pode `var` usar o padrão para criar uma variável temporária dentro de uma expressão booleana, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="75baf-159">You can use the `var` pattern to create a temporary variable within a Boolean expression, as the following example shows:</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="75baf-160">No exemplo anterior, a variável temporária é usada para armazenar o resultado de uma operação cara.</span><span class="sxs-lookup"><span data-stu-id="75baf-160">In the preceding example, the temporary variable is used to store the result of an expensive operation.</span></span> <span data-ttu-id="75baf-161">A variável pode então ser usada várias vezes.</span><span class="sxs-lookup"><span data-stu-id="75baf-161">The variable can then be used multiple times.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="75baf-162">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="75baf-162">C# language specification</span></span>
  
<span data-ttu-id="75baf-163">Para saber mais, confira a seção [O operador is](~/_csharplang/spec/expressions.md#the-is-operator) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md) e as seguintes propostas da linguagem C#:</span><span class="sxs-lookup"><span data-stu-id="75baf-163">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="75baf-164">Correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="75baf-164">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="75baf-165">Correspondência de padrões com genéricos</span><span class="sxs-lookup"><span data-stu-id="75baf-165">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="75baf-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="75baf-166">See also</span></span>

- [<span data-ttu-id="75baf-167">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="75baf-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="75baf-168">C# palavras-chave</span><span class="sxs-lookup"><span data-stu-id="75baf-168">C# keywords</span></span>](index.md)
- [<span data-ttu-id="75baf-169">Operadores cast e teste de tipo</span><span class="sxs-lookup"><span data-stu-id="75baf-169">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
