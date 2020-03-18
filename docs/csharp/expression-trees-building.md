---
title: Criando árvores de expressão
description: Saiba mais sobre técnicas de criação de árvores de expressão.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c93eb16ebf2ff66dc0162afb6841f2cadfce174e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146041"
---
# <a name="building-expression-trees"></a><span data-ttu-id="23eba-103">Criando árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="23eba-103">Building Expression Trees</span></span>

[<span data-ttu-id="23eba-104">Anterior – Interpretando expressões</span><span class="sxs-lookup"><span data-stu-id="23eba-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="23eba-105">Todas as árvores de expressão que você viu até agora foram criadas pelo compilador C#.</span><span class="sxs-lookup"><span data-stu-id="23eba-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="23eba-106">Tudo que eu tive que fazer foi criar uma expressão lambda que foi atribuída a uma variável tipada como um `Expression<Func<T>>` ou algum tipo semelhante.</span><span class="sxs-lookup"><span data-stu-id="23eba-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="23eba-107">Essa não é a única maneira de criar uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="23eba-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="23eba-108">Para muitos cenários, você pode descobrir que precisa criar uma expressão na memória em runtime.</span><span class="sxs-lookup"><span data-stu-id="23eba-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="23eba-109">Criar árvores de expressão é complicado pelo fato de que essas árvores de expressão são imutáveis.</span><span class="sxs-lookup"><span data-stu-id="23eba-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="23eba-110">Ser imutável significa que você precisa criar a árvore de folhas até a raiz.</span><span class="sxs-lookup"><span data-stu-id="23eba-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="23eba-111">As APIs que você usará para criar as árvores de expressão refletem esse fato: os métodos que você usará para criar um nó usam todos os seus filhos como argumentos.</span><span class="sxs-lookup"><span data-stu-id="23eba-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="23eba-112">Vejamos alguns exemplos para mostrar as técnicas a você.</span><span class="sxs-lookup"><span data-stu-id="23eba-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="23eba-113">Criando nós</span><span class="sxs-lookup"><span data-stu-id="23eba-113">Creating Nodes</span></span>

<span data-ttu-id="23eba-114">Vamos começar de forma relativamente simples mais uma vez.</span><span class="sxs-lookup"><span data-stu-id="23eba-114">Let's start relatively simply again.</span></span> <span data-ttu-id="23eba-115">Vamos usar a expressão de adição com que tenho trabalhado durante essas seções:</span><span class="sxs-lookup"><span data-stu-id="23eba-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="23eba-116">Para construir essa árvore de expressão, você precisará criar os nós de folha.</span><span class="sxs-lookup"><span data-stu-id="23eba-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="23eba-117">Os nós de folha são constantes, de modo que você pode usar o método `Expression.Constant` para criar os nós:</span><span class="sxs-lookup"><span data-stu-id="23eba-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="23eba-118">Em seguida, você criará a expressão de adição:</span><span class="sxs-lookup"><span data-stu-id="23eba-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="23eba-119">Depois que tiver a expressão de adição, você pode criar a expressão lambda:</span><span class="sxs-lookup"><span data-stu-id="23eba-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="23eba-120">Essa é uma expressão lambda muito simples, pois não contém argumentos.</span><span class="sxs-lookup"><span data-stu-id="23eba-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="23eba-121">Posteriormente nesta seção, você verá como mapear argumentos para parâmetros e criar expressões mais complicadas.</span><span class="sxs-lookup"><span data-stu-id="23eba-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="23eba-122">Para expressões que são simples como essa, você pode combinar todas as chamadas em uma única instrução:</span><span class="sxs-lookup"><span data-stu-id="23eba-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="23eba-123">Criando uma árvore</span><span class="sxs-lookup"><span data-stu-id="23eba-123">Building a Tree</span></span>

<span data-ttu-id="23eba-124">Estes são os conceitos básicos da criação de uma árvore de expressão na memória.</span><span class="sxs-lookup"><span data-stu-id="23eba-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="23eba-125">Árvores mais complexas geralmente significam mais tipos de nó e mais nós na árvore.</span><span class="sxs-lookup"><span data-stu-id="23eba-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="23eba-126">Vamos percorrer mais um exemplo e mostrar dois outros tipos de nó que você normalmente criará quando criar árvores de expressão: os nós de argumento e os nós de chamada de método.</span><span class="sxs-lookup"><span data-stu-id="23eba-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="23eba-127">Vamos criar uma árvore de expressão para criar esta expressão:</span><span class="sxs-lookup"><span data-stu-id="23eba-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="23eba-128">Você começará criando expressões de parâmetro para `x` e `y`:</span><span class="sxs-lookup"><span data-stu-id="23eba-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="23eba-129">A criação de expressões de multiplicação e adição segue o padrão que você já viu:</span><span class="sxs-lookup"><span data-stu-id="23eba-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="23eba-130">Em seguida, você precisa criar uma expressão de chamada de método para a chamada para `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="23eba-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="23eba-131">Depois, por fim, você coloca a chamada de método em uma expressão lambda e define os argumentos para a expressão lambda:</span><span class="sxs-lookup"><span data-stu-id="23eba-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="23eba-132">Neste exemplo mais complicado, você verá mais algumas técnicas de que frequentemente precisará para criar árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="23eba-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="23eba-133">Primeiro, você precisa criar os objetos que representam parâmetros ou variáveis locais antes de usá-los.</span><span class="sxs-lookup"><span data-stu-id="23eba-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="23eba-134">Após ter criado esses objetos, você pode usá-los em sua árvore de expressão quando for necessário.</span><span class="sxs-lookup"><span data-stu-id="23eba-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="23eba-135">Depois, você precisa usar um subconjunto das APIs de reflexão para criar um objeto `MethodInfo` para que possa criar uma árvore de expressão para acessar esse método.</span><span class="sxs-lookup"><span data-stu-id="23eba-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="23eba-136">Você deve se limitar ao subconjunto das APIs de reflexão que estão disponíveis na plataforma do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23eba-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="23eba-137">Mais uma vez, essas técnicas se estenderão a outras árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="23eba-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="23eba-138">Criando código profundamente</span><span class="sxs-lookup"><span data-stu-id="23eba-138">Building Code In Depth</span></span>

<span data-ttu-id="23eba-139">Você não fica limitado ao que pode criar usando essas APIs.</span><span class="sxs-lookup"><span data-stu-id="23eba-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="23eba-140">No entanto, quanto mais complicada for a árvore de expressão que você quer criar, mais difícil ser;a gerenciar e ler o código.</span><span class="sxs-lookup"><span data-stu-id="23eba-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="23eba-141">Vamos criar uma árvore de expressão que é o equivalente a este código:</span><span class="sxs-lookup"><span data-stu-id="23eba-141">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="23eba-142">Acima, observe que eu não criei a árvore de expressão, apenas o delegado.</span><span class="sxs-lookup"><span data-stu-id="23eba-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="23eba-143">Usando a classe `Expression`, não é possível criar lambdas de instrução.</span><span class="sxs-lookup"><span data-stu-id="23eba-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="23eba-144">Este é o código que é necessário para criar a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="23eba-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="23eba-145">Ele é complicado pelo fato de que não há uma API para criar um loop `while`. Em vez disso, você precisa criar um loop que contém um teste condicional e um destino para o rótulo para interromper o loop.</span><span class="sxs-lookup"><span data-stu-id="23eba-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="23eba-146">O código para criar a árvore de expressão para a função fatorial é bem mais longo, mais complicado e está cheio de rótulos e instruções de interrupção, bem como outros elementos que gostamos de evitar em nossas tarefas de codificação cotidianas.</span><span class="sxs-lookup"><span data-stu-id="23eba-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="23eba-147">Para esta seção, também atualizei o código de visitante para visitar cada nó nessa árvore de expressão e gravar informações sobre os nós que são criados neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="23eba-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="23eba-148">Você pode [exibir ou baixar o código de exemplo](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) no repositório dotnet/docs do GitHub.</span><span class="sxs-lookup"><span data-stu-id="23eba-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="23eba-149">Experimente por conta própria criando e executando os exemplos.</span><span class="sxs-lookup"><span data-stu-id="23eba-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="23eba-150">Para obter instruções de download, consulte [Exemplos e tutoriais](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="23eba-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="23eba-151">Examinando as APIs</span><span class="sxs-lookup"><span data-stu-id="23eba-151">Examining the APIs</span></span>

<span data-ttu-id="23eba-152">As APIs de árvore de expressão são algumas das mais difíceis de navegar no .NET Core, mas não tem problema.</span><span class="sxs-lookup"><span data-stu-id="23eba-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="23eba-153">Sua finalidade é uma tarefa bastante complexa: escrever código que gera código em runtime.</span><span class="sxs-lookup"><span data-stu-id="23eba-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="23eba-154">Eles são necessariamente complicadas para fornecer um equilíbrio entre dar suporte a todas as estruturas de controle disponíveis na linguagem C# e manter a área de superfície das APIs tão pequena quanto for razoável.</span><span class="sxs-lookup"><span data-stu-id="23eba-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="23eba-155">Esse equilíbrio significa que muitas estruturas de controle são representadas não por seus constructos em C#, mas por constructos que representam a lógica subjacente que o compilador gera desses constructos de nível superior.</span><span class="sxs-lookup"><span data-stu-id="23eba-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="23eba-156">Além disso, no momento, há expressões de C# que não podem ser criadas diretamente usando os métodos de classe `Expression`.</span><span class="sxs-lookup"><span data-stu-id="23eba-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="23eba-157">Em geral, esses serão os operadores e expressões mais novos adicionadas no C# 5 e no C# 6.</span><span class="sxs-lookup"><span data-stu-id="23eba-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="23eba-158">(Por exemplo, expressões `async` não podem ser criadas e o novo operador `?.` não pode ser criado diretamente.)</span><span class="sxs-lookup"><span data-stu-id="23eba-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="23eba-159">Próximo – Traduzindo expressões</span><span class="sxs-lookup"><span data-stu-id="23eba-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
