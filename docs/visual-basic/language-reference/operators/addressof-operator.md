---
title: Operador AddressOf (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
dev_langs:
- VB
helpviewer_keywords:
- AddressOf operator
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e29b7ae2a6f6040cfc8c6e0cd0c9eb055a6694e9
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="a7cf5-102">Operador AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7cf5-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="a7cf5-103">Cria uma instância delegada de procedimento que referencia o procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7cf5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7cf5-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="a7cf5-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a7cf5-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="a7cf5-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-106">Required.</span></span> <span data-ttu-id="a7cf5-107">Especifica o procedimento a ser referenciado pelo delegado de procedimento recém-criado.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7cf5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7cf5-108">Remarks</span></span>  
 <span data-ttu-id="a7cf5-109">O `AddressOf` operador cria um delegado de função que aponta para a função especificada por `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="a7cf5-110">Quando o procedimento especificado é que um método de instância, em seguida, o delegado de função refere-se a instância e o método.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="a7cf5-111">Em seguida, quando o delegado de função é chamado o método especificado da instância especificada é chamado.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="a7cf5-112">O `AddressOf` operador pode ser usado como o operando do construtor delegado ou pode ser usado em um contexto no qual o tipo do delegado pode ser determinado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7cf5-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7cf5-113">Example</span></span>  
 <span data-ttu-id="a7cf5-114">Este exemplo usa o `AddressOf` operador para designar um delegado para manipular o `Click` eventos de um botão.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 <span data-ttu-id="a7cf5-115">[!code-vb[VbVbalrDelegates n º&8;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7cf5-115">[!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7cf5-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7cf5-116">Example</span></span>  
 <span data-ttu-id="a7cf5-117">O exemplo a seguir usa o `AddressOf` operador para designar a função de inicialização para um thread.</span><span class="sxs-lookup"><span data-stu-id="a7cf5-117">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 <span data-ttu-id="a7cf5-118">[!code-vb[VbVbalrDelegates n º&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7cf5-118">[!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7cf5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7cf5-119">See Also</span></span>  
 <span data-ttu-id="a7cf5-120">[Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a7cf5-120">[Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="a7cf5-121"> [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a7cf5-121"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="a7cf5-122"> [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a7cf5-122"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="a7cf5-123"> [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="a7cf5-123"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span></span>

