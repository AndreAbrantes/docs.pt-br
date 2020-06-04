---
title: '* Operador'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: f1a7653fb3006ab3c9736ec168a8c5ea028f4763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409304"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="5f4f2-102">Operador \* (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f4f2-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="5f4f2-103">Multiplica dois números.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f4f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f4f2-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="5f4f2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5f4f2-105">Parts</span></span>  
  
|<span data-ttu-id="5f4f2-106">Termo</span><span class="sxs-lookup"><span data-stu-id="5f4f2-106">Term</span></span>|<span data-ttu-id="5f4f2-107">Definição</span><span class="sxs-lookup"><span data-stu-id="5f4f2-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="5f4f2-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-108">Required.</span></span> <span data-ttu-id="5f4f2-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="5f4f2-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-110">Required.</span></span> <span data-ttu-id="5f4f2-111">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="5f4f2-112">Result</span><span class="sxs-lookup"><span data-stu-id="5f4f2-112">Result</span></span>  
 <span data-ttu-id="5f4f2-113">O resultado é o produto do `number1` e do `number2` .</span><span class="sxs-lookup"><span data-stu-id="5f4f2-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="5f4f2-114">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="5f4f2-114">Supported Types</span></span>  
 <span data-ttu-id="5f4f2-115">Todos os tipos numéricos, incluindo os tipos de ponto flutuante e não assinados e `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="5f4f2-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f4f2-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f4f2-116">Remarks</span></span>  
 <span data-ttu-id="5f4f2-117">O tipo de dados do resultado depende dos tipos dos operandos.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="5f4f2-118">A tabela a seguir mostra como o tipo de dados do resultado é determinado.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="5f4f2-119">Tipos de dados do operando</span><span class="sxs-lookup"><span data-stu-id="5f4f2-119">Operand data types</span></span>|<span data-ttu-id="5f4f2-120">Tipo de dados de resultado</span><span class="sxs-lookup"><span data-stu-id="5f4f2-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="5f4f2-121">Ambas as expressões são tipos de dados integral ([SByte](../data-types/sbyte-data-type.md), [byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULONG](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="5f4f2-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="5f4f2-122">Um tipo de dados numérico apropriado para os tipos de dados do `number1` e do `number2` .</span><span class="sxs-lookup"><span data-stu-id="5f4f2-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="5f4f2-123">Consulte as tabelas "aritmética de inteiros" em [tipos de dados de resultados do operador](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="5f4f2-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="5f4f2-124">As duas expressões são [decimal](../data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="5f4f2-124">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="5f4f2-125">Ambas as expressões são [únicas](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="5f4f2-125">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="5f4f2-126">Uma das expressões é um tipo de dados de ponto flutuante ( `Single` ou [duplo](../data-types/double-data-type.md)), mas não ambos `Single` (Observe que `Decimal` não é um tipo de dados de ponto flutuante)</span><span class="sxs-lookup"><span data-stu-id="5f4f2-126">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="5f4f2-127">Se uma expressão for avaliada como [Nothing](../nothing.md), ela será tratada como zero.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-127">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5f4f2-128">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="5f4f2-128">Overloading</span></span>  
 <span data-ttu-id="5f4f2-129">O `*` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5f4f2-130">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5f4f2-131">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5f4f2-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f4f2-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f4f2-132">Example</span></span>  
 <span data-ttu-id="5f4f2-133">Este exemplo usa o `*` operador para multiplicar dois números.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="5f4f2-134">O resultado é o produto dos dois operandos.</span><span class="sxs-lookup"><span data-stu-id="5f4f2-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5f4f2-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="5f4f2-135">See also</span></span>

- [<span data-ttu-id="5f4f2-136">Operador \* =</span><span class="sxs-lookup"><span data-stu-id="5f4f2-136">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="5f4f2-137">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="5f4f2-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="5f4f2-138">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f4f2-138">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="5f4f2-139">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="5f4f2-139">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="5f4f2-140">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f4f2-140">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
