---
title: Comparações de valor
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: e424dd58cada8cda250554a4a8870e1900d0fa7d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085965"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="7d182-102">Comparações de valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d182-102">Value Comparisons (Visual Basic)</span></span>

<span data-ttu-id="7d182-103">Operadores de comparação podem ser usados para construir expressões que comparam os valores de variáveis numéricas.</span><span class="sxs-lookup"><span data-stu-id="7d182-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="7d182-104">Essas expressões retornam um `Boolean` valor com base em se a comparação é verdadeira ou falsa.</span><span class="sxs-lookup"><span data-stu-id="7d182-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="7d182-105">Exemplos de tal expressão são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="7d182-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="7d182-106">A primeira expressão é avaliada como `True` , porque 45 é maior que 26.</span><span class="sxs-lookup"><span data-stu-id="7d182-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="7d182-107">O segundo exemplo é avaliado como `False` , porque 26 não é maior que 45.</span><span class="sxs-lookup"><span data-stu-id="7d182-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="7d182-108">Você também pode comparar expressões numéricas dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="7d182-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="7d182-109">As expressões que você compara podem ser expressões complexas, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d182-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="7d182-110">A expressão complexa anterior inclui literais, variáveis e chamadas de função.</span><span class="sxs-lookup"><span data-stu-id="7d182-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="7d182-111">As expressões em ambos os lados do operador de comparação são avaliadas e os valores resultantes são comparados usando o `>=` operador de comparação.</span><span class="sxs-lookup"><span data-stu-id="7d182-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="7d182-112">Se o valor da expressão no lado esquerdo for maior ou igual ao valor da expressão à direita, a expressão inteira será avaliada como `True` ; caso contrário, ela será avaliada como `False` .</span><span class="sxs-lookup"><span data-stu-id="7d182-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="7d182-113">As expressões que comparam valores são mais comumente usadas em `If...Then` construções, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d182-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="7d182-114">O `=` sinal é um operador de comparação, bem como um operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="7d182-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="7d182-115">Quando usado como um operador de comparação, ele avalia se o valor à esquerda é igual ao valor à direita, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d182-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="7d182-116">Você também pode usar uma expressão de comparação em qualquer lugar `Boolean` que um valor for necessário, como em uma `If` instrução,, `While` `Loop` ou `ElseIf` , ou ao atribuir ou passar um valor para uma `Boolean` variável.</span><span class="sxs-lookup"><span data-stu-id="7d182-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="7d182-117">No exemplo a seguir, o valor retornado pela expressão de comparação é atribuído a uma `Boolean` variável.</span><span class="sxs-lookup"><span data-stu-id="7d182-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="7d182-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="7d182-118">See also</span></span>

- [<span data-ttu-id="7d182-119">Expressões booleanas</span><span class="sxs-lookup"><span data-stu-id="7d182-119">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="7d182-120">Operadores e expressões</span><span class="sxs-lookup"><span data-stu-id="7d182-120">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="7d182-121">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d182-121">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="7d182-122">Como calcular valores numéricos</span><span class="sxs-lookup"><span data-stu-id="7d182-122">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="7d182-123">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d182-123">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
