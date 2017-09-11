---
title: "Operador () (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1b0a683880f0791ee69ea5971756d104323b4303
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="0bafb-102">Operador () (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0bafb-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="0bafb-103">Além de serem usados para especificar a ordem das operações em uma expressão, os parênteses são usados para realizar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="0bafb-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="0bafb-104">Especificar conversões ou conversões de tipo.</span><span class="sxs-lookup"><span data-stu-id="0bafb-104">Specify casts, or type conversions.</span></span>  
  
     <span data-ttu-id="0bafb-105">[!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bafb-105">[!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]</span></span>  
  
2.  <span data-ttu-id="0bafb-106">Invocar métodos ou delegados.</span><span class="sxs-lookup"><span data-stu-id="0bafb-106">Invoke methods or delegates.</span></span>  
  
     <span data-ttu-id="0bafb-107">[!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bafb-107">[!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bafb-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0bafb-108">Remarks</span></span>  
 <span data-ttu-id="0bafb-109">Uma conversão invoca explicitamente o operador de conversão de um tipo para outro. A conversão falhará se nenhum operador de conversão desse tipo estiver definido.</span><span class="sxs-lookup"><span data-stu-id="0bafb-109">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="0bafb-110">Para definir um operador de conversão, consulte [explícita](../../../csharp/language-reference/keywords/explicit.md) e [implícita](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="0bafb-110">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="0bafb-111">O operador `()` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="0bafb-111">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="0bafb-112">Para obter mais informações, consulte [Conversões Cast e Conversões de Tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="0bafb-112">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="0bafb-113">Uma expressão de conversão pode levar a uma sintaxe ambígua.</span><span class="sxs-lookup"><span data-stu-id="0bafb-113">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="0bafb-114">Por exemplo, a expressão `(x)–y` poderia ser interpretada como uma expressão de conversão (uma conversão de –y para tipo x) ou como uma expressão aditiva combinada com uma expressão entre parênteses, que calcula o valor de x – y.</span><span class="sxs-lookup"><span data-stu-id="0bafb-114">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="0bafb-115">Para obter mais informações sobre a invocação de método, consulte [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="0bafb-115">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0bafb-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0bafb-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0bafb-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bafb-117">See Also</span></span>  
 <span data-ttu-id="0bafb-118">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bafb-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0bafb-119">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bafb-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="0bafb-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="0bafb-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

