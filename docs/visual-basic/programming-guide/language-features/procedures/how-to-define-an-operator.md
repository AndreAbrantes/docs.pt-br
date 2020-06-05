---
title: Como definir um operador
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 49b9c8d1a6db56a56b50c16b4a6bb5b928df6c7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388031"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="29bed-102">Como definir um operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29bed-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="29bed-103">Se você tiver definido uma classe ou estrutura, poderá definir o comportamento de um operador padrão (como `*` , `<>` ou `And` ) quando um ou ambos os operandos forem do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="29bed-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="29bed-104">Defina o operador padrão como um procedimento de operador dentro da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="29bed-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="29bed-105">Todos os procedimentos de operador devem ser `Public` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="29bed-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="29bed-106">A definição de um operador em uma classe ou estrutura também é chamada de *sobrecarga* do operador.</span><span class="sxs-lookup"><span data-stu-id="29bed-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29bed-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29bed-107">Example</span></span>  
 <span data-ttu-id="29bed-108">O exemplo a seguir define o `+` operador para uma estrutura chamada `height` .</span><span class="sxs-lookup"><span data-stu-id="29bed-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="29bed-109">A estrutura usa alturas medidas em pés e polegadas.</span><span class="sxs-lookup"><span data-stu-id="29bed-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="29bed-110">Uma *polegada* é de 2,54 centímetros e um *pé* é de 12 polegadas.</span><span class="sxs-lookup"><span data-stu-id="29bed-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="29bed-111">Para garantir valores normalizados (polegadas < 12,0), o construtor executa aritmética de *módulo* 12.</span><span class="sxs-lookup"><span data-stu-id="29bed-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="29bed-112">O `+` operador usa o construtor para gerar valores normalizados.</span><span class="sxs-lookup"><span data-stu-id="29bed-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="29bed-113">Você pode testar a estrutura `height` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="29bed-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="29bed-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="29bed-114">See also</span></span>

- [<span data-ttu-id="29bed-115">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="29bed-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="29bed-116">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="29bed-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="29bed-117">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="29bed-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="29bed-118">Como usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="29bed-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="29bed-119">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="29bed-119">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="29bed-120">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="29bed-120">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="29bed-121">Como: Declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="29bed-121">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="29bed-122">Operador Mod</span><span class="sxs-lookup"><span data-stu-id="29bed-122">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)
