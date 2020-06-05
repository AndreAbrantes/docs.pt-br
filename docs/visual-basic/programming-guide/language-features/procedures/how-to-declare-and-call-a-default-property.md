---
title: Como declarar e chamar uma propriedade padrão
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 4de5d94a94e764d1fc543ffae41b00a9bb729c94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388148"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="b776d-102">Como declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b776d-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="b776d-103">Uma *propriedade padrão* é uma classe ou propriedade de estrutura que seu código pode acessar sem especificá-la.</span><span class="sxs-lookup"><span data-stu-id="b776d-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="b776d-104">Ao chamar o código, uma classe ou estrutura, mas não uma propriedade, e o contexto permite acesso a uma propriedade, Visual Basic resolve o acesso a essa classe ou propriedade padrão da estrutura, se houver.</span><span class="sxs-lookup"><span data-stu-id="b776d-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="b776d-105">Uma classe ou estrutura pode ter no máximo uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="b776d-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="b776d-106">No entanto, você pode sobrecarregar uma propriedade padrão e ter mais de uma versão dela.</span><span class="sxs-lookup"><span data-stu-id="b776d-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="b776d-107">Para obter mais informações, consulte [padrão](../../../language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="b776d-107">For more information, see [Default](../../../language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="b776d-108">Para declarar uma propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="b776d-108">To declare a default property</span></span>  
  
1. <span data-ttu-id="b776d-109">Declare a propriedade da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="b776d-109">Declare the property in the normal way.</span></span> <span data-ttu-id="b776d-110">Não especifique a `Shared` `Private` palavra-chave ou.</span><span class="sxs-lookup"><span data-stu-id="b776d-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="b776d-111">Inclua a `Default` palavra-chave na declaração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b776d-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="b776d-112">Especifique pelo menos um parâmetro para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="b776d-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="b776d-113">Você não pode definir uma propriedade padrão que não leve pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="b776d-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="b776d-114">Para chamar uma propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="b776d-114">To call a default property</span></span>  
  
1. <span data-ttu-id="b776d-115">Declare uma variável da classe ou do tipo de estrutura que o contém.</span><span class="sxs-lookup"><span data-stu-id="b776d-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="b776d-116">Use o nome da variável sozinha em uma expressão em que você normalmente incluiria o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="b776d-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="b776d-117">Siga o nome da variável com uma lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="b776d-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="b776d-118">Uma propriedade padrão deve receber pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="b776d-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="b776d-119">Para recuperar o valor da propriedade padrão, use o nome da variável, com uma lista de argumentos, em uma expressão ou após o sinal de igual ( `=` ) em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="b776d-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="b776d-120">Para definir o valor da propriedade padrão, use o nome da variável, com uma lista de argumentos no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="b776d-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="b776d-121">Você sempre pode especificar o nome da propriedade padrão junto com o nome da variável, assim como faria para acessar qualquer outra propriedade.</span><span class="sxs-lookup"><span data-stu-id="b776d-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="b776d-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b776d-122">Example</span></span>  
 <span data-ttu-id="b776d-123">O exemplo a seguir declara uma propriedade padrão em uma classe.</span><span class="sxs-lookup"><span data-stu-id="b776d-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="b776d-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b776d-124">Example</span></span>  
 <span data-ttu-id="b776d-125">O exemplo a seguir demonstra como chamar a propriedade default `myProperty` na classe `class1` .</span><span class="sxs-lookup"><span data-stu-id="b776d-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="b776d-126">As três instruções de atribuição armazenam valores em `myProperty` e a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada lê os valores.</span><span class="sxs-lookup"><span data-stu-id="b776d-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="b776d-127">O uso mais comum de uma propriedade padrão é a <xref:Microsoft.VisualBasic.Collection.Item%2A> propriedade em várias classes de coleção.</span><span class="sxs-lookup"><span data-stu-id="b776d-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b776d-128">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b776d-128">Robust Programming</span></span>  
 <span data-ttu-id="b776d-129">As propriedades padrão podem resultar em uma pequena redução em caracteres de código-fonte, mas podem tornar seu código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="b776d-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="b776d-130">Se o código de chamada não estiver familiarizado com sua classe ou estrutura, quando ele fizer uma referência ao nome da classe ou da estrutura, ele não poderá ter certeza se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="b776d-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="b776d-131">Isso pode levar a erros de compilador ou erros de lógica de tempo de execução sutis.</span><span class="sxs-lookup"><span data-stu-id="b776d-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="b776d-132">Você pode, de certa forma, reduzir a chance de erros de propriedade padrão sempre usando a [instrução Option Strict](../../../language-reference/statements/option-strict-statement.md) para definir a verificação de tipo de compilador como `On` .</span><span class="sxs-lookup"><span data-stu-id="b776d-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="b776d-133">Se você estiver planejando usar uma classe ou estrutura predefinida em seu código, você deve determinar se ela tem uma propriedade padrão e, em caso afirmativo, qual é seu nome.</span><span class="sxs-lookup"><span data-stu-id="b776d-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="b776d-134">Devido a essas desvantagens, você deve considerar não definir propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="b776d-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="b776d-135">Para legibilidade de código, você também deve considerar sempre referir-se a todas as propriedades explicitamente, até mesmo propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="b776d-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b776d-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="b776d-136">See also</span></span>

- [<span data-ttu-id="b776d-137">Procedimentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="b776d-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b776d-138">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="b776d-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b776d-139">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="b776d-139">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="b776d-140">Default</span><span class="sxs-lookup"><span data-stu-id="b776d-140">Default</span></span>](../../../language-reference/modifiers/default.md)
- [<span data-ttu-id="b776d-141">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b776d-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="b776d-142">Como criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="b776d-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="b776d-143">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="b776d-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="b776d-144">Como chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="b776d-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="b776d-145">Como inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="b776d-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="b776d-146">Como obter um valor a partir de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="b776d-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
