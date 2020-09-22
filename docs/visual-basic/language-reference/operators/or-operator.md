---
title: Operador Or
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: f6cfd1073ada42aa2db8be9b14c81319bc0db294
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874754"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="17715-102">Operador Or (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17715-102">Or Operator (Visual Basic)</span></span>

<span data-ttu-id="17715-103">Executa uma disjunção lógica em duas `Boolean` expressões ou uma disjunção bit a bit em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="17715-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17715-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17715-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="17715-105">Partes</span><span class="sxs-lookup"><span data-stu-id="17715-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="17715-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="17715-106">Required.</span></span> <span data-ttu-id="17715-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="17715-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="17715-108">Para `Boolean` comparação, `result` é a disjunção lógica inclusiva de dois `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="17715-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="17715-109">No caso de operações bit-ais, `result` é um valor numérico que representa a disjunção de bits inclusiva de dois padrões de bit numérico.</span><span class="sxs-lookup"><span data-stu-id="17715-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="17715-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="17715-110">Required.</span></span> <span data-ttu-id="17715-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="17715-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="17715-112">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="17715-112">Required.</span></span> <span data-ttu-id="17715-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="17715-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17715-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="17715-114">Remarks</span></span>  

 <span data-ttu-id="17715-115">Para `Boolean` comparação, `result` é `False` se e somente se for `expression1` e `expression2` for avaliado como `False` .</span><span class="sxs-lookup"><span data-stu-id="17715-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="17715-116">A tabela a seguir ilustra como o `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="17715-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="17715-117">Se `expression1` for </span><span class="sxs-lookup"><span data-stu-id="17715-117">If `expression1` is</span></span>|<span data-ttu-id="17715-118">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="17715-118">And `expression2` is</span></span>|<span data-ttu-id="17715-119">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="17715-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="17715-120">Em uma `Boolean` comparação, o `Or` operador sempre avalia as duas expressões, o que pode incluir fazer chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="17715-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="17715-121">O [Operador OrElse](orelse-operator.md) executa o *curto-circuito*, o que significa que `expression1` , se for `True` , `expression2` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="17715-121">The [OrElse Operator](orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="17715-122">No caso de operações bit-a-bit, o `Or` operador executa uma comparação de bits com posição idêntica em duas expressões numéricas e define o bit correspondente de `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="17715-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="17715-123">Se o bit in `expression1` for</span><span class="sxs-lookup"><span data-stu-id="17715-123">If bit in `expression1` is</span></span>|<span data-ttu-id="17715-124">E o bit in `expression2` é</span><span class="sxs-lookup"><span data-stu-id="17715-124">And bit in `expression2` is</span></span>|<span data-ttu-id="17715-125">O bit em `result` é</span><span class="sxs-lookup"><span data-stu-id="17715-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="17715-126">1</span><span class="sxs-lookup"><span data-stu-id="17715-126">1</span></span>|<span data-ttu-id="17715-127">1</span><span class="sxs-lookup"><span data-stu-id="17715-127">1</span></span>|<span data-ttu-id="17715-128">1</span><span class="sxs-lookup"><span data-stu-id="17715-128">1</span></span>|  
|<span data-ttu-id="17715-129">1</span><span class="sxs-lookup"><span data-stu-id="17715-129">1</span></span>|<span data-ttu-id="17715-130">0</span><span class="sxs-lookup"><span data-stu-id="17715-130">0</span></span>|<span data-ttu-id="17715-131">1</span><span class="sxs-lookup"><span data-stu-id="17715-131">1</span></span>|  
|<span data-ttu-id="17715-132">0</span><span class="sxs-lookup"><span data-stu-id="17715-132">0</span></span>|<span data-ttu-id="17715-133">1</span><span class="sxs-lookup"><span data-stu-id="17715-133">1</span></span>|<span data-ttu-id="17715-134">1</span><span class="sxs-lookup"><span data-stu-id="17715-134">1</span></span>|  
|<span data-ttu-id="17715-135">0</span><span class="sxs-lookup"><span data-stu-id="17715-135">0</span></span>|<span data-ttu-id="17715-136">0</span><span class="sxs-lookup"><span data-stu-id="17715-136">0</span></span>|<span data-ttu-id="17715-137">0</span><span class="sxs-lookup"><span data-stu-id="17715-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="17715-138">Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem ser colocadas entre parênteses para garantir a execução</span><span class="sxs-lookup"><span data-stu-id="17715-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="17715-139">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="17715-139">Data Types</span></span>  

 <span data-ttu-id="17715-140">Se os operandos contiverem uma `Boolean` expressão e uma expressão numérica, Visual Basic converterá a `Boolean` expressão em um valor numérico (– 1 para `True` e 0 para `False` ) e executará uma operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="17715-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="17715-141">Para uma `Boolean` comparação, o tipo de dados do resultado é `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="17715-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="17715-142">Para uma comparação de bits, o tipo de dados de resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2` .</span><span class="sxs-lookup"><span data-stu-id="17715-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="17715-143">Consulte a tabela "comparações relacionais e de bits-bit" em [tipos de dados de resultados do operador](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="17715-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="17715-144">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="17715-144">Overloading</span></span>  

 <span data-ttu-id="17715-145">O `Or` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="17715-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="17715-146">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="17715-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="17715-147">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="17715-147">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17715-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17715-148">Example</span></span>  

 <span data-ttu-id="17715-149">O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica inclusiva em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="17715-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="17715-150">O resultado é um `Boolean` valor que representa se uma das duas expressões é `True` .</span><span class="sxs-lookup"><span data-stu-id="17715-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="17715-151">O exemplo anterior produz resultados de `True` , `True` , e `False` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="17715-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17715-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17715-152">Example</span></span>  

 <span data-ttu-id="17715-153">O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica inclusiva em bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="17715-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="17715-154">O bit no padrão de resultado será definido se qualquer um dos bits correspondentes nos operandos for definido como 1.</span><span class="sxs-lookup"><span data-stu-id="17715-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="17715-155">O exemplo anterior produz resultados de 10, 14 e 14, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="17715-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17715-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="17715-156">See also</span></span>

- [<span data-ttu-id="17715-157">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17715-157">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="17715-158">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17715-158">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="17715-159">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="17715-159">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="17715-160">Operador OrElse</span><span class="sxs-lookup"><span data-stu-id="17715-160">OrElse Operator</span></span>](orelse-operator.md)
- [<span data-ttu-id="17715-161">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17715-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
