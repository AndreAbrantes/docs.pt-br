---
title: Como sobrecarregar um procedimento que usa um número indefinido de parâmetros
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: ddff8c8cd82593b7d89fb0847e56123c287e364b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387875"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="85cac-102">Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85cac-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="85cac-103">Se um procedimento tiver um parâmetro [ParamArray](../../../language-reference/modifiers/paramarray.md) , você não poderá definir uma versão sobrecarregada usando uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="85cac-103">If a procedure has a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="85cac-104">Para obter mais informações, consulte "sobrecargas implícitas para um parâmetro ParamArray" em [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="85cac-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="85cac-105">Para sobrecarregar um procedimento que usa um número variável de parâmetros</span><span class="sxs-lookup"><span data-stu-id="85cac-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="85cac-106">Verifique se o procedimento e a chamada lógica de código se beneficia de versões sobrecarregadas mais do que de um `ParamArray` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="85cac-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="85cac-107">Consulte "sobrecargas e ParamArrays" em [Considerações sobre os procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="85cac-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="85cac-108">Determine quais números de valores fornecidos o procedimento deve aceitar na parte variável da lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="85cac-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="85cac-109">Isso pode incluir o caso de nenhum valor e pode incluir o caso de uma única matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="85cac-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="85cac-110">Para cada número aceitável de valores fornecidos, grave uma `Sub` `Function` instrução de declaração ou que define a lista de parâmetros correspondente.</span><span class="sxs-lookup"><span data-stu-id="85cac-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="85cac-111">Não use o `Optional` ou a `ParamArray` palavra-chave nessa versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="85cac-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="85cac-112">Em cada declaração, preceda a `Sub` `Function` palavra-chave ou com as [sobrecargas](../../../language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="85cac-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="85cac-113">Após cada declaração, escreva o código do procedimento que deve ser executado quando o código de chamada fornecer valores correspondentes à lista de parâmetros da declaração.</span><span class="sxs-lookup"><span data-stu-id="85cac-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="85cac-114">Encerre cada procedimento com a `End Sub` `End Function` instrução ou conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="85cac-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85cac-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85cac-115">Example</span></span>  
 <span data-ttu-id="85cac-116">O exemplo a seguir mostra um procedimento definido com um parâmetro [ParamArray](../../../language-reference/modifiers/paramarray.md) e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="85cac-116">The following example shows a procedure defined with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="85cac-117">Não é possível sobrecarregar esse procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="85cac-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="85cac-118">No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="85cac-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="85cac-119">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="85cac-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="85cac-120">O código nas versões sobrecarregadas não tem que testar se o código de chamada forneceu um ou mais valores para o `ParamArray` parâmetro, ou se for, quantos.</span><span class="sxs-lookup"><span data-stu-id="85cac-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="85cac-121">Visual Basic passa o controle para a versão que corresponde à lista de argumentos de chamada.</span><span class="sxs-lookup"><span data-stu-id="85cac-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="85cac-122">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="85cac-122">Compile the code</span></span>  
 <span data-ttu-id="85cac-123">Como um procedimento com um `ParamArray` parâmetro é equivalente a um conjunto de versões sobrecarregadas, não é possível sobrecarregar esse procedimento com uma lista de parâmetros correspondente a qualquer uma dessas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="85cac-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="85cac-124">Para obter mais informações, consulte [Considerações sobre sobrecarga de procedimentos](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="85cac-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="85cac-125">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="85cac-125">.NET Framework Security</span></span>  
 <span data-ttu-id="85cac-126">Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de sobreexecutar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85cac-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="85cac-127">Se você aceitar uma matriz de parâmetros, deverá testar o comprimento da matriz que o código de chamada passou e tomar as medidas apropriadas se for muito grande para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85cac-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85cac-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="85cac-128">See also</span></span>

- [<span data-ttu-id="85cac-129">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="85cac-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="85cac-130">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="85cac-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="85cac-131">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="85cac-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="85cac-132">Matrizes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="85cac-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="85cac-133">Sobrecarga de procedimento</span><span class="sxs-lookup"><span data-stu-id="85cac-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="85cac-134">Solucionando problemas de procedimentos</span><span class="sxs-lookup"><span data-stu-id="85cac-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="85cac-135">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="85cac-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="85cac-136">Como chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="85cac-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="85cac-137">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="85cac-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="85cac-138">Resolução de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="85cac-138">Overload Resolution</span></span>](./overload-resolution.md)
