---
title: Precedência de operador
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: b5649cd2a58fd8d300df58c563aebeed8976c4f5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874788"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="c341e-102">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c341e-102">Operator Precedence in Visual Basic</span></span>

<span data-ttu-id="c341e-103">Quando várias operações ocorrem em uma expressão, cada parte é avaliada e resolvida em uma ordem predeterminada chamada *prioridade do operador*.</span><span class="sxs-lookup"><span data-stu-id="c341e-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="c341e-104">Regras de precedência</span><span class="sxs-lookup"><span data-stu-id="c341e-104">Precedence Rules</span></span>

 <span data-ttu-id="c341e-105">Quando as expressões contêm operadores de mais de uma categoria, elas são avaliadas de acordo com as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="c341e-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="c341e-106">Os operadores aritméticos e de concatenação têm a ordem de precedência descrita na seção a seguir, e todos têm maior precedência do que os operadores de comparação, lógico e bit-a.</span><span class="sxs-lookup"><span data-stu-id="c341e-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="c341e-107">Todos os operadores de comparação têm precedência igual, e todos têm maior precedência do que os operadores lógicos e de bit-inteiro, mas precedência menor do que os operadores aritméticos e de concatenação.</span><span class="sxs-lookup"><span data-stu-id="c341e-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="c341e-108">Os operadores lógicos e bits de bit têm a ordem de precedência descrita na seção a seguir, e todos têm precedência mais baixa do que os operadores aritméticos, de concatenação e de comparação.</span><span class="sxs-lookup"><span data-stu-id="c341e-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="c341e-109">Os operadores com precedência igual são avaliados da esquerda para a direita na ordem em que aparecem na expressão.</span><span class="sxs-lookup"><span data-stu-id="c341e-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="c341e-110">Ordem de precedência</span><span class="sxs-lookup"><span data-stu-id="c341e-110">Precedence Order</span></span>

 <span data-ttu-id="c341e-111">Os operadores são avaliados na seguinte ordem de precedência:</span><span class="sxs-lookup"><span data-stu-id="c341e-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="c341e-112">Operador Await</span><span class="sxs-lookup"><span data-stu-id="c341e-112">Await Operator</span></span>

 <span data-ttu-id="c341e-113">Expressões</span><span class="sxs-lookup"><span data-stu-id="c341e-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="c341e-114">Operadores aritméticos e de concatenação</span><span class="sxs-lookup"><span data-stu-id="c341e-114">Arithmetic and Concatenation Operators</span></span>

 <span data-ttu-id="c341e-115">Exponenciação ( `^` )</span><span class="sxs-lookup"><span data-stu-id="c341e-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="c341e-116">Identidade e negação unários ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="c341e-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="c341e-117">Multiplicação e divisão de ponto flutuante ( `*` , `/` )</span><span class="sxs-lookup"><span data-stu-id="c341e-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="c341e-118">Divisão de inteiro ( `\` )</span><span class="sxs-lookup"><span data-stu-id="c341e-118">Integer division (`\`)</span></span>

 <span data-ttu-id="c341e-119">Aritmética modular ( `Mod` )</span><span class="sxs-lookup"><span data-stu-id="c341e-119">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="c341e-120">Adição e subtração ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="c341e-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="c341e-121">Concatenação de cadeia de caracteres ( `&` )</span><span class="sxs-lookup"><span data-stu-id="c341e-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="c341e-122">Deslocamento de bit aritmético ( `<<` , `>>` )</span><span class="sxs-lookup"><span data-stu-id="c341e-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="c341e-123">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="c341e-123">Comparison Operators</span></span>

 <span data-ttu-id="c341e-124">Todos os operadores de comparação ( `=` ,,,, `<>` `<` `<=` `>` , `>=` , `Is` , `IsNot` , `Like` , `TypeOf` ... `Is` )</span><span class="sxs-lookup"><span data-stu-id="c341e-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="c341e-125">Operadores lógicos e bit a bit</span><span class="sxs-lookup"><span data-stu-id="c341e-125">Logical and Bitwise Operators</span></span>

 <span data-ttu-id="c341e-126">Negação ( `Not` )</span><span class="sxs-lookup"><span data-stu-id="c341e-126">Negation (`Not`)</span></span>

 <span data-ttu-id="c341e-127">Conjunção ( `And` , `AndAlso` )</span><span class="sxs-lookup"><span data-stu-id="c341e-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="c341e-128">Disjunção inclusiva ( `Or` , `OrElse` )</span><span class="sxs-lookup"><span data-stu-id="c341e-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="c341e-129">Disjunção exclusiva ( `Xor` )</span><span class="sxs-lookup"><span data-stu-id="c341e-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="c341e-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="c341e-130">Comments</span></span>

 <span data-ttu-id="c341e-131">O `=` operador é apenas o operador de comparação de igualdade, não o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="c341e-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="c341e-132">O operador de concatenação de cadeia de caracteres ( `&` ) não é um operador aritmético, mas, na precedência, ele é agrupado com os operadores aritméticos.</span><span class="sxs-lookup"><span data-stu-id="c341e-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="c341e-133">Os `Is` `IsNot` operadores e são operadores de comparação de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="c341e-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="c341e-134">Eles não comparam os valores de dois objetos; Eles só verificam se duas variáveis de objeto se referem à mesma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="c341e-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="c341e-135">Capacidade de associação</span><span class="sxs-lookup"><span data-stu-id="c341e-135">Associativity</span></span>

 <span data-ttu-id="c341e-136">Quando os operadores de precedência igual aparecem juntos em uma expressão, por exemplo, multiplicação e divisão, o compilador avalia cada operação à medida que a encontra da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="c341e-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="c341e-137">O exemplo a seguir ilustra isto.</span><span class="sxs-lookup"><span data-stu-id="c341e-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="c341e-138">A primeira expressão avalia a divisão 96/8 (que resulta em 12) e, em seguida, a divisão 12/4, que resulta em três.</span><span class="sxs-lookup"><span data-stu-id="c341e-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="c341e-139">Como o compilador avalia as operações do `n1` da esquerda para a direita, a avaliação é a mesma quando essa ordem é indicada explicitamente para `n2` .</span><span class="sxs-lookup"><span data-stu-id="c341e-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="c341e-140">Ambos `n1` e `n2` têm um resultado de três.</span><span class="sxs-lookup"><span data-stu-id="c341e-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="c341e-141">Por outro lado, o `n3` tem um resultado de 48, porque os parênteses forçam o compilador a avaliar a 8/4 primeiro.</span><span class="sxs-lookup"><span data-stu-id="c341e-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="c341e-142">Devido a esse comportamento, os operadores são considerados *associativos à esquerda* no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c341e-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="c341e-143">Substituindo precedência e Associação</span><span class="sxs-lookup"><span data-stu-id="c341e-143">Overriding Precedence and Associativity</span></span>

 <span data-ttu-id="c341e-144">Você pode usar parênteses para forçar algumas partes de uma expressão a serem avaliadas antes de outras.</span><span class="sxs-lookup"><span data-stu-id="c341e-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="c341e-145">Isso pode substituir a ordem de precedência e a associação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="c341e-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="c341e-146">Visual Basic sempre executa operações que são colocadas entre parênteses antes das externas.</span><span class="sxs-lookup"><span data-stu-id="c341e-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="c341e-147">No entanto, entre parênteses, ele mantém precedência comum e associação, a menos que você use parênteses dentro dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="c341e-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="c341e-148">O exemplo a seguir ilustra isto.</span><span class="sxs-lookup"><span data-stu-id="c341e-148">The following example illustrates this.</span></span>

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a><span data-ttu-id="c341e-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="c341e-149">See also</span></span>

- [<span data-ttu-id="c341e-150">= Operador</span><span class="sxs-lookup"><span data-stu-id="c341e-150">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="c341e-151">Operador Is</span><span class="sxs-lookup"><span data-stu-id="c341e-151">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="c341e-152">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="c341e-152">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="c341e-153">Operador Like</span><span class="sxs-lookup"><span data-stu-id="c341e-153">Like Operator</span></span>](like-operator.md)
- [<span data-ttu-id="c341e-154">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="c341e-154">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="c341e-155">Operador Await</span><span class="sxs-lookup"><span data-stu-id="c341e-155">Await Operator</span></span>](await-operator.md)
- [<span data-ttu-id="c341e-156">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c341e-156">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="c341e-157">Operadores e expressões</span><span class="sxs-lookup"><span data-stu-id="c341e-157">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
