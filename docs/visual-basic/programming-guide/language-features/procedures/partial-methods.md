---
title: Métodos parciais
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 61a1398ba7de8dab005fa1e9efa13dc2ba18cc3c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364117"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="45754-102">Métodos parciais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45754-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="45754-103">Os métodos parciais permitem que os desenvolvedores insiram lógica personalizada no código.</span><span class="sxs-lookup"><span data-stu-id="45754-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="45754-104">Normalmente, o código faz parte de uma classe gerada pelo designer.</span><span class="sxs-lookup"><span data-stu-id="45754-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="45754-105">Os métodos parciais são definidos em uma classe parcial que é criada por um gerador de código e são comumente usadas para fornecer notificações de que algo foi alterado.</span><span class="sxs-lookup"><span data-stu-id="45754-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="45754-106">Eles permitem que o desenvolvedor especifique o comportamento personalizado em resposta à alteração.</span><span class="sxs-lookup"><span data-stu-id="45754-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="45754-107">O designer do gerador de código define apenas a assinatura do método e uma ou mais chamadas para o método.</span><span class="sxs-lookup"><span data-stu-id="45754-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="45754-108">Os desenvolvedores podem então fornecer implementações para o método se desejarem personalizar o comportamento do código gerado.</span><span class="sxs-lookup"><span data-stu-id="45754-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="45754-109">Quando nenhuma implementação é fornecida, as chamadas para o método são removidas pelo compilador, resultando em nenhuma sobrecarga adicional de desempenho.</span><span class="sxs-lookup"><span data-stu-id="45754-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="45754-110">Declaração</span><span class="sxs-lookup"><span data-stu-id="45754-110">Declaration</span></span>  
 <span data-ttu-id="45754-111">O código gerado marca a definição de um método parcial colocando a palavra-chave `Partial` no início da linha de assinatura.</span><span class="sxs-lookup"><span data-stu-id="45754-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="45754-112">A definição deve atender às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="45754-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="45754-113">O método deve ser um `Sub` , não um `Function` .</span><span class="sxs-lookup"><span data-stu-id="45754-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="45754-114">O corpo do método deve ser deixado vazio.</span><span class="sxs-lookup"><span data-stu-id="45754-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="45754-115">O modificador de acesso deve ser `Private` .</span><span class="sxs-lookup"><span data-stu-id="45754-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="45754-116">Implementação</span><span class="sxs-lookup"><span data-stu-id="45754-116">Implementation</span></span>  
 <span data-ttu-id="45754-117">A implementação consiste principalmente em preencher o corpo do método parcial.</span><span class="sxs-lookup"><span data-stu-id="45754-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="45754-118">A implementação normalmente está em uma classe parcial separada da definição e é escrita por um desenvolvedor que deseja estender o código gerado.</span><span class="sxs-lookup"><span data-stu-id="45754-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="45754-119">O exemplo anterior duplica a assinatura na declaração exatamente, mas as variações são possíveis.</span><span class="sxs-lookup"><span data-stu-id="45754-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="45754-120">Em particular, outros modificadores podem ser adicionados, como `Overloads` ou `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="45754-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="45754-121">Somente um `Overrides` modificador é permitido.</span><span class="sxs-lookup"><span data-stu-id="45754-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="45754-122">Para obter mais informações sobre modificadores de método, consulte [sub Statement](../../../language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="45754-122">For more information about method modifiers, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="45754-123">Uso</span><span class="sxs-lookup"><span data-stu-id="45754-123">Use</span></span>  
 <span data-ttu-id="45754-124">Você chama um método parcial como você chamaria qualquer outro `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="45754-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="45754-125">Se o método tiver sido implementado, os argumentos serão avaliados e o corpo do método será executado.</span><span class="sxs-lookup"><span data-stu-id="45754-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="45754-126">No entanto, lembre-se de que a implementação de um método parcial é opcional.</span><span class="sxs-lookup"><span data-stu-id="45754-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="45754-127">Se o método não for implementado, uma chamada para ele não terá efeito e as expressões passadas como argumentos para o método não serão avaliadas.</span><span class="sxs-lookup"><span data-stu-id="45754-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45754-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45754-128">Example</span></span>  
 <span data-ttu-id="45754-129">Em um arquivo chamado Product. designer. vb, defina uma `Product` classe que tenha uma `Quantity` propriedade.</span><span class="sxs-lookup"><span data-stu-id="45754-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="45754-130">Em um arquivo chamado Product. vb, forneça uma implementação para o `QuantityChanged` .</span><span class="sxs-lookup"><span data-stu-id="45754-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="45754-131">Por fim, no método principal de um projeto, declare uma `Product` instância e forneça um valor inicial para sua `Quantity` propriedade.</span><span class="sxs-lookup"><span data-stu-id="45754-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="45754-132">Será exibida uma caixa de mensagem que exibe esta mensagem:</span><span class="sxs-lookup"><span data-stu-id="45754-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="45754-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="45754-133">See also</span></span>

- [<span data-ttu-id="45754-134">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="45754-134">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="45754-135">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="45754-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="45754-136">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="45754-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="45754-137">Parcial</span><span class="sxs-lookup"><span data-stu-id="45754-137">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="45754-138">Geração de código em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="45754-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="45754-139">Adicionando a lógica de negócios usando métodos parciais</span><span class="sxs-lookup"><span data-stu-id="45754-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
