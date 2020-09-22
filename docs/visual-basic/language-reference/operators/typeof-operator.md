---
title: Operador TypeOf
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 0a01b49cf1e0bf9ad7b2ce541cee39cba83025ca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875309"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="57178-102">Operador TypeOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57178-102">TypeOf Operator (Visual Basic)</span></span>

<span data-ttu-id="57178-103">Verifica se o tipo de tempo de execução do resultado de uma expressão é compatível com tipo com o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="57178-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="57178-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57178-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="57178-105">Partes</span><span class="sxs-lookup"><span data-stu-id="57178-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="57178-106">Exibido.</span><span class="sxs-lookup"><span data-stu-id="57178-106">Returned.</span></span> <span data-ttu-id="57178-107">Um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="57178-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="57178-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="57178-108">Required.</span></span> <span data-ttu-id="57178-109">Qualquer expressão que seja avaliada como um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="57178-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="57178-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="57178-110">Required.</span></span> <span data-ttu-id="57178-111">Qualquer nome de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="57178-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57178-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="57178-112">Remarks</span></span>  

 <span data-ttu-id="57178-113">O `TypeOf` operador determina se o tipo de tempo de execução do `objectexpression` é compatível com `typename` .</span><span class="sxs-lookup"><span data-stu-id="57178-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="57178-114">A compatibilidade depende da categoria de tipo de `typename` .</span><span class="sxs-lookup"><span data-stu-id="57178-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="57178-115">A tabela a seguir mostra como a compatibilidade é determinada.</span><span class="sxs-lookup"><span data-stu-id="57178-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="57178-116">Categoria de tipo de `typename`</span><span class="sxs-lookup"><span data-stu-id="57178-116">Type category of `typename`</span></span>|<span data-ttu-id="57178-117">Critério de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="57178-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="57178-118">Classe</span><span class="sxs-lookup"><span data-stu-id="57178-118">Class</span></span>|<span data-ttu-id="57178-119">`objectexpression` é do tipo `typename` ou herda de `typename`</span><span class="sxs-lookup"><span data-stu-id="57178-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="57178-120">Estrutura</span><span class="sxs-lookup"><span data-stu-id="57178-120">Structure</span></span>|<span data-ttu-id="57178-121">`objectexpression` é do tipo `typename`</span><span class="sxs-lookup"><span data-stu-id="57178-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="57178-122">Interface</span><span class="sxs-lookup"><span data-stu-id="57178-122">Interface</span></span>|<span data-ttu-id="57178-123">`objectexpression` implementa `typename` ou herda de uma classe que implementa `typename`</span><span class="sxs-lookup"><span data-stu-id="57178-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="57178-124">Se o tipo de tempo de execução `objectexpression` atende ao critério de compatibilidade, `result` é `True` .</span><span class="sxs-lookup"><span data-stu-id="57178-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="57178-125">Caso contrário, `result` é `False`.</span><span class="sxs-lookup"><span data-stu-id="57178-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="57178-126">Se `objectexpression` for NULL, então `TypeOf` ... `Is` retorna `False` e... `IsNot` retorna `True` .</span><span class="sxs-lookup"><span data-stu-id="57178-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="57178-127">`TypeOf` é sempre usado com a `Is` palavra-chave para construir uma `TypeOf` expressão... `Is` ou com a `IsNot` palavra-chave para construir uma `TypeOf` expressão... `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="57178-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57178-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57178-128">Example</span></span>  

 <span data-ttu-id="57178-129">O exemplo a seguir usa `TypeOf` expressões... `Is` para testar a compatibilidade de tipo de duas variáveis de referência de objeto com vários tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="57178-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="57178-130">A variável `refInteger` tem um tipo de tempo de execução de `Integer` .</span><span class="sxs-lookup"><span data-stu-id="57178-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="57178-131">Ele é compatível com `Integer` , mas não com `Double` .</span><span class="sxs-lookup"><span data-stu-id="57178-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="57178-132">A variável `refForm` tem um tipo de tempo de execução de <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="57178-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="57178-133">Ele é compatível com <xref:System.Windows.Forms.Form> porque é seu tipo, com <xref:System.Windows.Forms.Control> porque <xref:System.Windows.Forms.Form> herda de <xref:System.Windows.Forms.Control> e com <xref:System.ComponentModel.IComponent> porque <xref:System.Windows.Forms.Form> herda de <xref:System.ComponentModel.Component> , que implementa <xref:System.ComponentModel.IComponent> .</span><span class="sxs-lookup"><span data-stu-id="57178-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="57178-134">No entanto, o `refForm` não é compatível com o <xref:System.Windows.Forms.Label> .</span><span class="sxs-lookup"><span data-stu-id="57178-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57178-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="57178-135">See also</span></span>

- [<span data-ttu-id="57178-136">Operador Is</span><span class="sxs-lookup"><span data-stu-id="57178-136">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="57178-137">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="57178-137">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="57178-138">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57178-138">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="57178-139">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57178-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="57178-140">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="57178-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="57178-141">Operadores e expressões</span><span class="sxs-lookup"><span data-stu-id="57178-141">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
