---
title: Interpretando Expressões
description: Aprenda como escrever código para examinar a estrutura de um árvore de expressão.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: ea205d42b02ea7b38c04cb70d322329cf7c1d495
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004641"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="b27ff-103">Interpretando Expressões</span><span class="sxs-lookup"><span data-stu-id="b27ff-103">Interpreting Expressions</span></span>

[<span data-ttu-id="b27ff-104">Anterior – Executando expressões</span><span class="sxs-lookup"><span data-stu-id="b27ff-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="b27ff-105">Agora, vamos escrever código para examinar a estrutura de um *árvore de expressão*.</span><span class="sxs-lookup"><span data-stu-id="b27ff-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="b27ff-106">Cada nó em uma árvore de expressão será um objeto de uma classe derivada de `Expression`.</span><span class="sxs-lookup"><span data-stu-id="b27ff-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="b27ff-107">Esse design torna visitar todos os nós em uma árvore de expressão uma operação recursiva relativamente simples.</span><span class="sxs-lookup"><span data-stu-id="b27ff-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="b27ff-108">A estratégia geral é iniciar no nó raiz e determine que tipo de nó ele é.</span><span class="sxs-lookup"><span data-stu-id="b27ff-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="b27ff-109">Se o tipo de nó tiver filhos, visite os filhos recursivamente.</span><span class="sxs-lookup"><span data-stu-id="b27ff-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="b27ff-110">Em cada nó filho, repita o processo usado no nó raiz: determine o tipo e, se o tipo tiver filhos, visite cada um dos filhos.</span><span class="sxs-lookup"><span data-stu-id="b27ff-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="b27ff-111">Examinando uma expressão sem filhos</span><span class="sxs-lookup"><span data-stu-id="b27ff-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="b27ff-112">Vamos começar visitando cada nó em uma árvore de expressão simples.</span><span class="sxs-lookup"><span data-stu-id="b27ff-112">Let's start by visiting each node in a simple expression tree.</span></span>
<span data-ttu-id="b27ff-113">Este é o código que cria uma expressão constante e, em seguida, examina suas propriedades:</span><span class="sxs-lookup"><span data-stu-id="b27ff-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="b27ff-114">Isso imprimirá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b27ff-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="b27ff-115">Agora, vamos escrever o código que examinaria essa expressão e escrever algumas propriedades importantes sobre ele.</span><span class="sxs-lookup"><span data-stu-id="b27ff-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="b27ff-116">Este é o código:</span><span class="sxs-lookup"><span data-stu-id="b27ff-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="b27ff-117">Examinando uma expressão de adição simples</span><span class="sxs-lookup"><span data-stu-id="b27ff-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="b27ff-118">Vamos começar com o exemplo de adição da introdução desta seção.</span><span class="sxs-lookup"><span data-stu-id="b27ff-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="b27ff-119">Não estou usando `var` para declarar essa árvore de expressão, pois isso não é possível porque o lado direito da atribuição é de um tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="b27ff-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span>

<span data-ttu-id="b27ff-120">O nó raiz é um `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="b27ff-120">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="b27ff-121">Para obter o código interessante no lado direito do `=>` operador, você precisa encontrar um dos filhos do `LambdaExpression` ....</span><span class="sxs-lookup"><span data-stu-id="b27ff-121">In order to get the interesting code on the right-hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="b27ff-122">Faremos isso com todas as expressões nesta seção.</span><span class="sxs-lookup"><span data-stu-id="b27ff-122">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="b27ff-123">O nó pai nos ajudar a localizar o tipo de retorno do `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="b27ff-123">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="b27ff-124">Para examinar cada nó nesta expressão, precisaremos visitar recursivamente alguns nós.</span><span class="sxs-lookup"><span data-stu-id="b27ff-124">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="b27ff-125">Esta é uma primeira implementação simples:</span><span class="sxs-lookup"><span data-stu-id="b27ff-125">Here's a simple first implementation:</span></span>

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

<span data-ttu-id="b27ff-126">Este exemplo imprime a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b27ff-126">This sample prints the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

<span data-ttu-id="b27ff-127">Você vai notar que há muita repetição no exemplo de código acima.</span><span class="sxs-lookup"><span data-stu-id="b27ff-127">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="b27ff-128">Vamos limpar tudo isso e criar um visitante de nós de expressão com uma finalidade mais geral.</span><span class="sxs-lookup"><span data-stu-id="b27ff-128">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="b27ff-129">Para isso, precisaremos escrever um algoritmo recursivo.</span><span class="sxs-lookup"><span data-stu-id="b27ff-129">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="b27ff-130">Qualquer nó poderia ser de um tipo que pode ter filhos.</span><span class="sxs-lookup"><span data-stu-id="b27ff-130">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="b27ff-131">Qualquer nó que tem filhos exige que nós visitemos esses filhos e determinemos o que é esse nó.</span><span class="sxs-lookup"><span data-stu-id="b27ff-131">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="b27ff-132">Esta é a versão limpa que utiliza a recursão para visitar as operações de adição:</span><span class="sxs-lookup"><span data-stu-id="b27ff-132">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

<span data-ttu-id="b27ff-133">Esse algoritmo é a base de um algoritmo que pode visitar qualquer `LambdaExpression` arbitrário.</span><span class="sxs-lookup"><span data-stu-id="b27ff-133">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="b27ff-134">Há muitos buracos, ou seja, o código que criei apenas procura uma amostra muito pequena dos possíveis conjuntos de nós da árvore de expressão que ele pode encontrar.</span><span class="sxs-lookup"><span data-stu-id="b27ff-134">There are many holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="b27ff-135">No entanto, ainda é possível aprender bastante com o que ele produz.</span><span class="sxs-lookup"><span data-stu-id="b27ff-135">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="b27ff-136">(O caso padrão no método `Visitor.CreateFromExpression` imprime uma mensagem no console de erro quando um novo tipo de nó é encontrado.</span><span class="sxs-lookup"><span data-stu-id="b27ff-136">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="b27ff-137">Dessa forma, você sabe que precisa adicionar um novo tipo de expressão.)</span><span class="sxs-lookup"><span data-stu-id="b27ff-137">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="b27ff-138">Quando executa esse visitante na expressão de adição mostrada acima, você obtém a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b27ff-138">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="b27ff-139">Agora que criou uma implementação de visitante mais geral, você pode visitar e processar muitos tipos diferentes de expressões.</span><span class="sxs-lookup"><span data-stu-id="b27ff-139">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="b27ff-140">Examinando uma expressão de adição com vários níveis</span><span class="sxs-lookup"><span data-stu-id="b27ff-140">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="b27ff-141">Vamos testar um exemplo mais complicado, mas ainda limitar os tipos de nó somente à adição:</span><span class="sxs-lookup"><span data-stu-id="b27ff-141">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="b27ff-142">Antes de executar isso no algoritmo de visitante, tente pensar no que poderia ser a saída.</span><span class="sxs-lookup"><span data-stu-id="b27ff-142">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="b27ff-143">Lembre-se de que o operador `+` é um *operador binário*: ele deve ter dois filhos, que representam os operandos esquerdo e direito.</span><span class="sxs-lookup"><span data-stu-id="b27ff-143">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="b27ff-144">Há várias maneiras possíveis de construir uma árvore que podem ser corretas:</span><span class="sxs-lookup"><span data-stu-id="b27ff-144">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="b27ff-145">Você pode ver a separação em duas possíveis respostas para realçar a mais promissora.</span><span class="sxs-lookup"><span data-stu-id="b27ff-145">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="b27ff-146">A primeira representa expressões *associativas à direita*.</span><span class="sxs-lookup"><span data-stu-id="b27ff-146">The first represents *right associative* expressions.</span></span> <span data-ttu-id="b27ff-147">A segunda representa expressões *associativas à esquerda*.</span><span class="sxs-lookup"><span data-stu-id="b27ff-147">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="b27ff-148">A vantagem desses dois formatos é que o formato pode ser dimensionado para qualquer número arbitrário de expressões de adição.</span><span class="sxs-lookup"><span data-stu-id="b27ff-148">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span>

<span data-ttu-id="b27ff-149">Se você executar essa expressão por meio do visitante, verá essa saída, verificando se a expressão de adição simples é a *associação à esquerda*.</span><span class="sxs-lookup"><span data-stu-id="b27ff-149">If you do run this expression through the visitor, you will see this output, verifying that the simple addition expression is *left associative*.</span></span>

<span data-ttu-id="b27ff-150">Para executar esse exemplo e ver a árvore de expressão completa, eu precise fazer uma alteração na árvore de expressão de origem.</span><span class="sxs-lookup"><span data-stu-id="b27ff-150">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="b27ff-151">Quando a árvore de expressão contém todas as constantes, a árvore resultante contém apenas o valor constante de `10`.</span><span class="sxs-lookup"><span data-stu-id="b27ff-151">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="b27ff-152">O compilador executa toda a adição e reduz a expressão a sua forma mais simples.</span><span class="sxs-lookup"><span data-stu-id="b27ff-152">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="b27ff-153">Simplesmente adicionar uma variável à expressão é suficiente para ver a árvore original:</span><span class="sxs-lookup"><span data-stu-id="b27ff-153">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="b27ff-154">Crie um visitante para essa soma e execute o visitante; você verá esta saída:</span><span class="sxs-lookup"><span data-stu-id="b27ff-154">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

<span data-ttu-id="b27ff-155">Você também pode executar qualquer um dos outros exemplos pelo código visitante e ver que árvore ele representa.</span><span class="sxs-lookup"><span data-stu-id="b27ff-155">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="b27ff-156">Veja um exemplo da expressão `sum3` acima (com um parâmetro adicional para impedir que o compilador calcule a constante):</span><span class="sxs-lookup"><span data-stu-id="b27ff-156">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="b27ff-157">Esta é a saída do visitante:</span><span class="sxs-lookup"><span data-stu-id="b27ff-157">Here's the output from the visitor:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="b27ff-158">Observe que os parênteses não fazem parte da saída.</span><span class="sxs-lookup"><span data-stu-id="b27ff-158">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="b27ff-159">Não há nenhum nó na árvore de expressão que representa os parênteses na expressão de entrada.</span><span class="sxs-lookup"><span data-stu-id="b27ff-159">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="b27ff-160">A estrutura de árvore de expressão contém todas as informações necessárias para comunicar a precedência.</span><span class="sxs-lookup"><span data-stu-id="b27ff-160">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="b27ff-161">Estendendo deste exemplo</span><span class="sxs-lookup"><span data-stu-id="b27ff-161">Extending from this sample</span></span>

<span data-ttu-id="b27ff-162">O exemplo lida apenas com as árvores de expressão mais rudimentares.</span><span class="sxs-lookup"><span data-stu-id="b27ff-162">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="b27ff-163">O código que você viu nesta seção só lida com inteiros constantes e com o operador `+` binário.</span><span class="sxs-lookup"><span data-stu-id="b27ff-163">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="b27ff-164">Como um exemplo final, vamos atualizar o visitante para lidar com uma expressão mais complicada.</span><span class="sxs-lookup"><span data-stu-id="b27ff-164">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="b27ff-165">Vamos fazer com que ele funcione para isto:</span><span class="sxs-lookup"><span data-stu-id="b27ff-165">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="b27ff-166">Este código representa uma possível implementação da função *fatorial* matemática.</span><span class="sxs-lookup"><span data-stu-id="b27ff-166">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="b27ff-167">A maneira como escrevi este código destaca duas limitações da criação de árvores de expressão atribuindo expressões lambda a Expressões.</span><span class="sxs-lookup"><span data-stu-id="b27ff-167">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="b27ff-168">Primeiro, lambdas de instrução não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="b27ff-168">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="b27ff-169">Isso significa que eu não posso usar loops, blocos, instruções if/else e outras estruturas de controle comuns em C#.</span><span class="sxs-lookup"><span data-stu-id="b27ff-169">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="b27ff-170">Estou limitado ao uso de expressões.</span><span class="sxs-lookup"><span data-stu-id="b27ff-170">I'm limited to using expressions.</span></span> <span data-ttu-id="b27ff-171">Em segundo lugar, não posso chamar recursivamente a mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="b27ff-171">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="b27ff-172">Eu poderia se ela já fosse um delegado, mas não posso chamá-la em sua forma de árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="b27ff-172">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="b27ff-173">Na seção sobre a [criação de árvores de expressão](expression-trees-building.md), você aprenderá técnicas para superar essas limitações.</span><span class="sxs-lookup"><span data-stu-id="b27ff-173">In the section on [building expression trees](expression-trees-building.md), you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="b27ff-174">Nesta expressão, você encontrará todos esses tipos de nós:</span><span class="sxs-lookup"><span data-stu-id="b27ff-174">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="b27ff-175">Igual (expressão binária)</span><span class="sxs-lookup"><span data-stu-id="b27ff-175">Equal (binary expression)</span></span>
2. <span data-ttu-id="b27ff-176">Multiplicar (expressão binária)</span><span class="sxs-lookup"><span data-stu-id="b27ff-176">Multiply (binary expression)</span></span>
3. <span data-ttu-id="b27ff-177">Condicional (a expressão ?</span><span class="sxs-lookup"><span data-stu-id="b27ff-177">Conditional (the ?</span></span> <span data-ttu-id="b27ff-178">:)</span><span class="sxs-lookup"><span data-stu-id="b27ff-178">: expression)</span></span>
4. <span data-ttu-id="b27ff-179">Expressão de chamada de método (chamar `Range()` e `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="b27ff-179">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="b27ff-180">Uma maneira de modificar o algoritmo do visitante é continuar executando-o e escrever o tipo de nó toda vez que você atingir sua cláusula `default`.</span><span class="sxs-lookup"><span data-stu-id="b27ff-180">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="b27ff-181">Após algumas iterações, você terá cisto todos os nós potenciais.</span><span class="sxs-lookup"><span data-stu-id="b27ff-181">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="b27ff-182">Então, você tem tudo de que você precisa.</span><span class="sxs-lookup"><span data-stu-id="b27ff-182">Then, you have all you need.</span></span> <span data-ttu-id="b27ff-183">O resultado seria algo semelhante a:</span><span class="sxs-lookup"><span data-stu-id="b27ff-183">The result would be something like this:</span></span>

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

<span data-ttu-id="b27ff-184">O ConditionalVisitor e o MethodCallVisitor processam esses dois nós:</span><span class="sxs-lookup"><span data-stu-id="b27ff-184">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

<span data-ttu-id="b27ff-185">E a saída da árvore de expressão seria:</span><span class="sxs-lookup"><span data-stu-id="b27ff-185">And the output for the expression tree would be:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a><span data-ttu-id="b27ff-186">Estendendo a biblioteca de exemplo</span><span class="sxs-lookup"><span data-stu-id="b27ff-186">Extending the Sample Library</span></span>

<span data-ttu-id="b27ff-187">Os exemplos nesta seção mostram as principais técnicas para visitar e examinar nós em uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="b27ff-187">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="b27ff-188">Eu encobri várias ações de que talvez você precise para nos concentrarmos nas tarefas principais de visitar e acessar nós em uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="b27ff-188">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span>

<span data-ttu-id="b27ff-189">Primeiro, os visitantes lidam somente com constantes que são números inteiros.</span><span class="sxs-lookup"><span data-stu-id="b27ff-189">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="b27ff-190">Os valores das constantes podem ser de qualquer outro tipo numérico e a linguagem C# dá suporte a conversões e promoções entre esses tipos.</span><span class="sxs-lookup"><span data-stu-id="b27ff-190">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="b27ff-191">Uma versão mais robusta desse código espelharia todos esses recursos.</span><span class="sxs-lookup"><span data-stu-id="b27ff-191">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="b27ff-192">Até o último exemplo reconhece um subconjunto dos tipos de nó possíveis.</span><span class="sxs-lookup"><span data-stu-id="b27ff-192">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="b27ff-193">Você ainda poderá alimentá-lo com muitas expressões que o fariam falhar.</span><span class="sxs-lookup"><span data-stu-id="b27ff-193">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="b27ff-194">Uma implementação completa está incluída no .NET Standard com o nome <xref:System.Linq.Expressions.ExpressionVisitor> e pode lidar com todos os tipos de nó possíveis.</span><span class="sxs-lookup"><span data-stu-id="b27ff-194">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="b27ff-195">Por fim, a biblioteca usada neste artigo foi desenvolvida para demonstração e aprendizado.</span><span class="sxs-lookup"><span data-stu-id="b27ff-195">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="b27ff-196">Ela não está otimizada.</span><span class="sxs-lookup"><span data-stu-id="b27ff-196">It's not optimized.</span></span> <span data-ttu-id="b27ff-197">Eu o escrevi para tornar as estruturas usadas claras e destacar as técnicas usadas para visitar os nós e analisar o que está lá.</span><span class="sxs-lookup"><span data-stu-id="b27ff-197">I wrote it to make the structures used clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="b27ff-198">Uma implementação de produção dedicaria mais atenção ao desempenho do que eu dediquei.</span><span class="sxs-lookup"><span data-stu-id="b27ff-198">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="b27ff-199">Mesmo com essas limitações, você deve estar bem no processo de escrever algoritmos que leem e entendem árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="b27ff-199">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="b27ff-200">Próximo – Compilando expressões</span><span class="sxs-lookup"><span data-stu-id="b27ff-200">Next -- Building Expressions</span></span>](expression-trees-building.md)
