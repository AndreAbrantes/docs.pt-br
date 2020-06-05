---
title: Como definir várias versões de um procedimento
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 870a18dbf3a7e28b7d7b612e853beeec6908cf6f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387927"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="433e3-102">Como definir várias versões de um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="433e3-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="433e3-103">Você pode definir um procedimento em várias versões *sobrecarregando* -a, usando o mesmo nome, mas uma lista de parâmetros diferente para cada versão.</span><span class="sxs-lookup"><span data-stu-id="433e3-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="433e3-104">A finalidade do sobrecarregamento é definir várias versões de um procedimento bem relacionadas sem precisar diferenciá-las por nome.</span><span class="sxs-lookup"><span data-stu-id="433e3-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="433e3-105">Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="433e3-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="433e3-106">Para definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="433e3-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="433e3-107">Grave uma `Sub` `Function` instrução de declaração ou para cada versão do procedimento que você deseja definir.</span><span class="sxs-lookup"><span data-stu-id="433e3-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="433e3-108">Use o mesmo nome de procedimento em cada declaração.</span><span class="sxs-lookup"><span data-stu-id="433e3-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="433e3-109">Preceda a `Sub` `Function` palavra-chave ou em cada declaração com a palavra-chave [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="433e3-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="433e3-110">Opcionalmente, você pode omitir `Overloads` as declarações, mas se você incluí-las em qualquer uma das declarações, deverá incluí-las em cada declaração.</span><span class="sxs-lookup"><span data-stu-id="433e3-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="433e3-111">Seguindo cada instrução de declaração, escreva o código do procedimento para lidar com o caso específico em que o código de chamada fornece argumentos correspondentes à lista de parâmetros da versão.</span><span class="sxs-lookup"><span data-stu-id="433e3-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="433e3-112">Você não precisa testar quais parâmetros o código de chamada forneceu.</span><span class="sxs-lookup"><span data-stu-id="433e3-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="433e3-113">Visual Basic passa o controle para a versão correspondente do procedimento.</span><span class="sxs-lookup"><span data-stu-id="433e3-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="433e3-114">Encerre cada versão do procedimento com a `End Sub` instrução ou `End Function` conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="433e3-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="433e3-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="433e3-115">Example</span></span>  
 <span data-ttu-id="433e3-116">O exemplo a seguir define um `Sub` procedimento para lançar uma transação em relação ao saldo do cliente.</span><span class="sxs-lookup"><span data-stu-id="433e3-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="433e3-117">Ele usa a `Overloads` palavra-chave para definir duas versões do procedimento, uma que aceita o cliente pelo nome e a outra por número da conta.</span><span class="sxs-lookup"><span data-stu-id="433e3-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="433e3-118">O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer` e, em seguida, usar a mesma instrução de chamada em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="433e3-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="433e3-119">Para obter informações sobre como chamar essas versões do `post` procedimento, consulte [como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="433e3-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="433e3-120">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="433e3-120">Compile the code</span></span>  
 <span data-ttu-id="433e3-121">Verifique se cada uma de suas versões sobrecarregadas tem o mesmo nome de procedimento, mas uma lista de parâmetros diferente.</span><span class="sxs-lookup"><span data-stu-id="433e3-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433e3-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="433e3-122">See also</span></span>

- [<span data-ttu-id="433e3-123">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="433e3-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="433e3-124">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="433e3-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="433e3-125">Solucionando problemas de procedimentos</span><span class="sxs-lookup"><span data-stu-id="433e3-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="433e3-126">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="433e3-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="433e3-127">Como sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="433e3-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="433e3-128">Considerações sobre procedimentos de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="433e3-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="433e3-129">Resolução de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="433e3-129">Overload Resolution</span></span>](./overload-resolution.md)
