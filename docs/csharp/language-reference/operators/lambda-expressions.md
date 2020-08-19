---
title: Expressões lambda-referência C#
description: Saiba mais sobre expressões lambda. Há lambdas de expressão que têm uma expressão como seu corpo, ou lambdas de instrução que têm um bloco de instrução como seu corpo.
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 3dd793ec000999935bff6b54b1b00e49211bd5ec
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558355"
---
# <a name="lambda-expressions-c-reference"></a><span data-ttu-id="3315c-104">Expressões lambda (referência C#)</span><span class="sxs-lookup"><span data-stu-id="3315c-104">Lambda expressions (C# reference)</span></span>

<span data-ttu-id="3315c-105">Uma *expressão lambda* é uma expressão de uma das duas seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="3315c-105">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="3315c-106">[Expressão lambda](#expression-lambdas) que tem uma expressão como corpo:</span><span class="sxs-lookup"><span data-stu-id="3315c-106">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="3315c-107">[Instrução lambda](#statement-lambdas) que tem um bloco de instrução como corpo:</span><span class="sxs-lookup"><span data-stu-id="3315c-107">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="3315c-108">Use o [operador de declaração lambda `=>`](lambda-operator.md) para separar a lista de parâmetros de lambda do corpo.</span><span class="sxs-lookup"><span data-stu-id="3315c-108">Use the [lambda declaration operator `=>`](lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="3315c-109">Para criar uma expressão lambda, especifique os parâmetros de entrada (se houver) no lado esquerdo do operador lambda e uma expressão ou um bloco de instrução do outro lado.</span><span class="sxs-lookup"><span data-stu-id="3315c-109">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="3315c-110">Qualquer expressão lambda pode ser convertida para um tipo [delegado](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="3315c-110">Any lambda expression can be converted to a [delegate](../builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="3315c-111">O tipo delegado no qual uma expressão lambda pode ser convertida é definido pelos tipos de parâmetros e pelo valor retornado.</span><span class="sxs-lookup"><span data-stu-id="3315c-111">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="3315c-112">Se uma expressão lambda não retornar um valor, ela poderá ser convertida em um dos tipos delegados `Action`; caso contrário, ela poderá ser convertida em um dos tipos delegados `Func`.</span><span class="sxs-lookup"><span data-stu-id="3315c-112">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="3315c-113">Por exemplo, uma expressão lambda que tem dois parâmetros e não retorna nenhum valor pode ser convertida em um delegado <xref:System.Action%602>.</span><span class="sxs-lookup"><span data-stu-id="3315c-113">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="3315c-114">Uma expressão lambda que tem um parâmetro e retorna um valor pode ser convertida em um delegado <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="3315c-114">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="3315c-115">No exemplo a seguir, a expressão lambda `x => x * x` , que especifica um parâmetro denominado `x` e retorna o valor de `x` quadrado, é atribuída a uma variável de um tipo delegado:</span><span class="sxs-lookup"><span data-stu-id="3315c-115">In the following example, the lambda expression `x => x * x`, which specifies a parameter that's named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="3315c-116">As lambdas de expressão também podem ser convertidas para os tipos de [árvore de expressão](../../programming-guide/concepts/expression-trees/index.md) , como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3315c-116">Expression lambdas can also be converted to the [expression tree](../../programming-guide/concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="3315c-117">Use expressões lambda em qualquer código que exija instâncias de tipos delegados ou árvores de expressão, por exemplo, como um argumento ao método <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> para passar o código que deve ser executado em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="3315c-117">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="3315c-118">Você também pode usar expressões lambda ao escrever [LINQ em C#](../../linq/index.md), como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3315c-118">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="3315c-119">Quando você usa a sintaxe baseada em método para chamar o método <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> na classe <xref:System.Linq.Enumerable?displayProperty=nameWithType>, por exemplo, no LINQ to Objects e no LINQ to XML, o parâmetro é um tipo delegado <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3315c-119">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3315c-120">Quando você chama o <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> método na <xref:System.Linq.Queryable?displayProperty=nameWithType> classe, por exemplo, em LINQ to SQL, o tipo de parâmetro é um tipo de árvore de expressão [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) .</span><span class="sxs-lookup"><span data-stu-id="3315c-120">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="3315c-121">Em ambos os casos, você pode usar a mesma expressão lambda para especificar o valor do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3315c-121">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="3315c-122">Isso faz com que as duas chamadas `Select` pareçam semelhantes, embora, na verdade, o tipo de objetos criado dos lambdas seja diferente.</span><span class="sxs-lookup"><span data-stu-id="3315c-122">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="3315c-123">Lambdas de expressão</span><span class="sxs-lookup"><span data-stu-id="3315c-123">Expression lambdas</span></span>

<span data-ttu-id="3315c-124">Uma expressão lambda com uma expressão no lado direito do operador `=>` é chamada de *lambda de expressão*.</span><span class="sxs-lookup"><span data-stu-id="3315c-124">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="3315c-125">Os lambdas de expressão são usados amplamente na construção de [árvores de expressão](../../programming-guide/concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="3315c-125">Expression lambdas are used extensively in the construction of [expression trees](../../programming-guide/concepts/expression-trees/index.md).</span></span> <span data-ttu-id="3315c-126">Uma expressão lambda retorna o resultado da expressão e tem o seguinte formato básico:</span><span class="sxs-lookup"><span data-stu-id="3315c-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="3315c-127">Os parênteses serão opcionais somente se o lambda tiver um parâmetro de entrada; caso contrário, eles serão obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="3315c-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="3315c-128">Especifique parâmetros de entrada zero com parênteses vazios:</span><span class="sxs-lookup"><span data-stu-id="3315c-128">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="3315c-129">Dois ou mais parâmetros de entrada são separados por vírgulas e envolvidos por parênteses:</span><span class="sxs-lookup"><span data-stu-id="3315c-129">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="3315c-130">Às vezes, é difícil ou impossível para o compilador inferir os tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="3315c-130">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="3315c-131">Você pode especificar os tipos de maneira explícita conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="3315c-131">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="3315c-132">Os tipos de parâmetro de entrada devem ser todos explícitos ou implícitos; caso contrário, ocorrerá o erro [CS0748](../../misc/cs0748.md) de compilador.</span><span class="sxs-lookup"><span data-stu-id="3315c-132">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="3315c-133">O corpo de um lambda de expressão pode consistir em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="3315c-133">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="3315c-134">No entanto, se você estiver criando árvores de expressão que serão avaliadas fora contexto do .NET Common Language Runtime, como no SQL Server, você não deverá usar chamadas de método em lambdas de expressão.</span><span class="sxs-lookup"><span data-stu-id="3315c-134">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="3315c-135">Os métodos não terão significado fora do contexto do .NET Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="3315c-135">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="3315c-136">Lambdas de instrução</span><span class="sxs-lookup"><span data-stu-id="3315c-136">Statement lambdas</span></span>

<span data-ttu-id="3315c-137">Um lambda de instrução lembra um lambda de expressão, exceto que as instruções estão incluídas entre chaves:</span><span class="sxs-lookup"><span data-stu-id="3315c-137">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="3315c-138">O corpo de uma instrução lambda pode consistir de qualquer número de instruções; no entanto, na prática, normalmente não há mais de duas ou três.</span><span class="sxs-lookup"><span data-stu-id="3315c-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="3315c-139">Os lambdas de instrução não podem ser usados para criar árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="3315c-139">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="3315c-140">Lambdas assíncronos</span><span class="sxs-lookup"><span data-stu-id="3315c-140">Async lambdas</span></span>

<span data-ttu-id="3315c-141">Você pode facilmente criar expressões e instruções lambda que incorporem processamento assíncrono, ao usar as palavras-chaves [async](../keywords/async.md) e [await](await.md).</span><span class="sxs-lookup"><span data-stu-id="3315c-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../keywords/async.md) and [await](await.md) keywords.</span></span> <span data-ttu-id="3315c-142">Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="3315c-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="3315c-143">Você pode adicionar o mesmo manipulador de eventos ao usar um lambda assíncrono.</span><span class="sxs-lookup"><span data-stu-id="3315c-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="3315c-144">Para adicionar esse manipulador, adicione um modificador `async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3315c-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="3315c-145">Para obter mais informações sobre como criar e usar métodos assíncronos, consulte [programação assíncrona com Async e Await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="3315c-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="3315c-146">Expressões lambda e tuplas</span><span class="sxs-lookup"><span data-stu-id="3315c-146">Lambda expressions and tuples</span></span>

<span data-ttu-id="3315c-147">A partir do C# 7.0, a linguagem C# fornece suporte interno para [tuplas](../builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="3315c-147">Starting with C# 7.0, the C# language provides built-in support for [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="3315c-148">Você pode fornecer uma tupla como um argumento para uma expressão lambda e a expressão lambda também pode retornar uma tupla.</span><span class="sxs-lookup"><span data-stu-id="3315c-148">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="3315c-149">Em alguns casos, o compilador do C# usa a inferência de tipos para determinar os tipos dos componentes da tupla.</span><span class="sxs-lookup"><span data-stu-id="3315c-149">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="3315c-150">Você pode definir uma tupla, colocando entre parênteses uma lista delimitada por vírgulas de seus componentes.</span><span class="sxs-lookup"><span data-stu-id="3315c-150">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="3315c-151">O exemplo a seguir usa a tupla com três componentes para passar uma sequência de números para uma expressão lambda, que dobra cada valor e retorna uma tupla com três componentes que contém o resultado das multiplicações.</span><span class="sxs-lookup"><span data-stu-id="3315c-151">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="3315c-152">Normalmente, os campos de uma tupla são nomeados `Item1` , `Item2` etc. No entanto, você pode definir uma tupla com componentes nomeados, como faz o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3315c-152">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="3315c-153">Para obter mais informações sobre tuplas C#, consulte [tipos de tupla](../../language-reference/builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="3315c-153">For more information about C# tuples, see [Tuple types](../../language-reference/builtin-types/value-tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="3315c-154">Lambdas com os operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="3315c-154">Lambdas with the standard query operators</span></span>

<span data-ttu-id="3315c-155">O LINQ to Objects, entre outras implementações, tem um parâmetro de entrada cujo tipo faz parte da família de delegados genéricos <xref:System.Func%601>.</span><span class="sxs-lookup"><span data-stu-id="3315c-155">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="3315c-156">Esses delegados usam parâmetros de tipo para definir o número e o tipo de parâmetros de entrada e o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="3315c-156">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="3315c-157">delegados `Func` são muito úteis para encapsular expressões definidas pelo usuário aplicadas a cada elemento em um conjunto de dados de origem.</span><span class="sxs-lookup"><span data-stu-id="3315c-157">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="3315c-158">Por exemplo, considere o seguinte tipo delegado <xref:System.Func%602>:</span><span class="sxs-lookup"><span data-stu-id="3315c-158">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="3315c-159">O delegado pode ser instanciado como um `Func<int, bool>`, em que `int` é um parâmetro de entrada e `bool` é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="3315c-159">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="3315c-160">O valor de retorno é sempre especificado no último parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="3315c-160">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="3315c-161">Por exemplo, `Func<int, string, bool>` define um delegado com dois parâmetros de entrada, `int` e `string`, e um tipo de retorno de `bool`.</span><span class="sxs-lookup"><span data-stu-id="3315c-161">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="3315c-162">O delegado `Func` a seguir, quando é invocado, retornará um valor booliano que indica se o parâmetro de entrada é ou não igual a cinco:</span><span class="sxs-lookup"><span data-stu-id="3315c-162">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="3315c-163">Você também pode fornecer uma expressão lambda quando o tipo de argumento é um <xref:System.Linq.Expressions.Expression%601>. Por exemplo, nos operadores de consulta padrão que são definidos no tipo <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="3315c-163">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="3315c-164">Quando você especifica um argumento <xref:System.Linq.Expressions.Expression%601>, o lambda é compilado em uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="3315c-164">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="3315c-165">O exemplo a seguir usa o operador padrão de consulta <xref:System.Linq.Enumerable.Count%2A>:</span><span class="sxs-lookup"><span data-stu-id="3315c-165">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="3315c-166">O compilador pode inferir o tipo de parâmetro de entrada ou você também pode especificá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="3315c-166">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="3315c-167">Essa expressão lambda em particular conta esses inteiros (`n`) que, quando dividida por dois, tem um resto 1.</span><span class="sxs-lookup"><span data-stu-id="3315c-167">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="3315c-168">O exemplo a seguir gera uma sequência que contém todos os elementos da matriz `numbers` que precedem o 9, porque esse é o primeiro número na sequência que não satisfaz a condição:</span><span class="sxs-lookup"><span data-stu-id="3315c-168">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="3315c-169">O exemplo a seguir especifica vários parâmetros de entrada, colocando-os entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="3315c-169">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="3315c-170">O método retorna todos os elementos na matriz `numbers` até encontrar um número cujo valor seja inferior à sua posição ordinal na matriz:</span><span class="sxs-lookup"><span data-stu-id="3315c-170">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="3315c-171">Inferência de tipos em expressões lambda</span><span class="sxs-lookup"><span data-stu-id="3315c-171">Type inference in lambda expressions</span></span>

<span data-ttu-id="3315c-172">Ao escrever lambdas, você geralmente não precisa especificar um tipo para os parâmetros de entrada porque o compilador pode inferir o tipo com base no corpo do lambda, nos tipos de parâmetro e em outros fatores, conforme descrito na especificação da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="3315c-172">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="3315c-173">Para a maioria dos operadores de consulta padrão, a primeira entrada é o tipo dos elementos na sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="3315c-173">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="3315c-174">Se você estiver consultando um `IEnumerable<Customer>`, a variável de entrada será inferida para ser um objeto `Customer`, o que significa que você terá acesso aos seus métodos e propriedades:</span><span class="sxs-lookup"><span data-stu-id="3315c-174">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="3315c-175">As regras gerais para a inferência de tipos para lambdas são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="3315c-175">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="3315c-176">O lambda deve conter o mesmo número de parâmetros do tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="3315c-176">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="3315c-177">Cada parâmetro de entrada no lambda deve ser implicitamente conversível em seu parâmetro delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="3315c-177">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="3315c-178">O valor de retorno do lambda (se houver) deve ser implicitamente conversível para o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="3315c-178">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="3315c-179">Observe que as expressões lambda em si não têm um tipo porque o sistema de tipo comum não possui nenhum conceito intrínseco de "expressão lambda."</span><span class="sxs-lookup"><span data-stu-id="3315c-179">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="3315c-180">No entanto, às vezes é conveniente falar informalmente do "tipo" de uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="3315c-180">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="3315c-181">Nesses casos, o tipo se refere ao tipo delegado ou tipo <xref:System.Linq.Expressions.Expression> ao qual a expressão lambda é convertida.</span><span class="sxs-lookup"><span data-stu-id="3315c-181">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="3315c-182">Captura de variáveis externas e escopo variável em expressões lambda</span><span class="sxs-lookup"><span data-stu-id="3315c-182">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="3315c-183">Os lambdas pode fazer referência a *variáveis externas*.</span><span class="sxs-lookup"><span data-stu-id="3315c-183">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="3315c-184">Essas são as variáveis que estão no escopo do método que define a expressão lambda ou no escopo do tipo que contém a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="3315c-184">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="3315c-185">As variáveis que são capturadas dessa forma são armazenadas para uso na expressão lambda mesmo que de alguma outra forma elas saíssem do escopo e fossem coletadas como lixo.</span><span class="sxs-lookup"><span data-stu-id="3315c-185">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="3315c-186">Uma variável externa deve ser definitivamente atribuída para que possa ser consumida em uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="3315c-186">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="3315c-187">O exemplo a seguir demonstra estas regras:</span><span class="sxs-lookup"><span data-stu-id="3315c-187">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="3315c-188">As seguintes regras se aplicam ao escopo variável em expressões lambda:</span><span class="sxs-lookup"><span data-stu-id="3315c-188">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="3315c-189">Uma variável capturada não será coletada do lixo até que o delegado que faz referência a ela se qualifique para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3315c-189">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="3315c-190">As variáveis introduzidas em uma expressão lambda não são visíveis no método delimitador.</span><span class="sxs-lookup"><span data-stu-id="3315c-190">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="3315c-191">Uma expressão lambda não pode capturar um parâmetro [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md) ou [out](../keywords/out-parameter-modifier.md) diretamente de um método delimitador.</span><span class="sxs-lookup"><span data-stu-id="3315c-191">A lambda expression cannot directly capture an [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md), or [out](../keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="3315c-192">Uma instrução [return](../keywords/return.md) em uma expressão lambda não faz com que o método delimitador retorne.</span><span class="sxs-lookup"><span data-stu-id="3315c-192">A [return](../keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="3315c-193">Uma expressão lambda não pode conter uma instrução [goto](../keywords/goto.md), [break](../keywords/break.md) ou [continue](../keywords/continue.md) se o destino daquela instrução de salto estiver fora do bloco da expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="3315c-193">A lambda expression cannot contain a [goto](../keywords/goto.md), [break](../keywords/break.md), or [continue](../keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="3315c-194">Também será um erro ter uma instrução de salto fora do bloco da expressão lambda se o destino estiver dentro do bloco.</span><span class="sxs-lookup"><span data-stu-id="3315c-194">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3315c-195">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3315c-195">C# language specification</span></span>

<span data-ttu-id="3315c-196">Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3315c-196">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="3315c-197">Capítulo do livro em destaque</span><span class="sxs-lookup"><span data-stu-id="3315c-197">Featured book chapter</span></span>

<span data-ttu-id="3315c-198">[Expressões lambda, eventos e delegados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="3315c-198">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3315c-199">Confira também</span><span class="sxs-lookup"><span data-stu-id="3315c-199">See also</span></span>

- [<span data-ttu-id="3315c-200">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3315c-200">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3315c-201">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="3315c-201">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="3315c-202">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="3315c-202">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="3315c-203">Árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="3315c-203">Expression Trees</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="3315c-204">Funções locais vs. expressões lambda</span><span class="sxs-lookup"><span data-stu-id="3315c-204">Local functions vs. lambda expressions</span></span>](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="3315c-205">Exemplos de C# do Visual Studio 2008 (veja os arquivos de exemplo de consultas LINQ e programa XQuery)</span><span class="sxs-lookup"><span data-stu-id="3315c-205">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
