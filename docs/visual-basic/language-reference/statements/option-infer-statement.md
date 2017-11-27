---
title: "Instrução Option Infer"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4634c198b5fc41a4834cbd3cd96f9d3f1863d09b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="option-infer-statement"></a><span data-ttu-id="ebfcb-102">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="ebfcb-102">Option Infer Statement</span></span>
<span data-ttu-id="ebfcb-103">Permite o uso de inferência de tipo local ao declarar variáveis.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfcb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebfcb-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="ebfcb-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ebfcb-105">Parts</span></span>  
  
|<span data-ttu-id="ebfcb-106">Termo</span><span class="sxs-lookup"><span data-stu-id="ebfcb-106">Term</span></span>|<span data-ttu-id="ebfcb-107">Definição</span><span class="sxs-lookup"><span data-stu-id="ebfcb-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="ebfcb-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-108">Optional.</span></span> <span data-ttu-id="ebfcb-109">Permite inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="ebfcb-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-110">Optional.</span></span> <span data-ttu-id="ebfcb-111">Desabilita inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebfcb-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebfcb-112">Remarks</span></span>  
 <span data-ttu-id="ebfcb-113">Para definir `Option Infer` em um arquivo, digite `Option Infer On` ou `Option Infer Off` na parte superior do arquivo, antes de qualquer outro código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="ebfcb-114">Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="ebfcb-115">Quando você define `Option Infer` para `On`, você pode declarar variáveis locais sem especificar explicitamente um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="ebfcb-116">O compilador infere o tipo de dados de uma variável do tipo de sua expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="ebfcb-117">Na ilustração a seguir, `Option Infer` está ativado.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="ebfcb-118">A variável na declaração `Dim someVar = 2` é declarada como um inteiro por inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="ebfcb-119">![Exibição do IntelliSense da declaração. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="ebfcb-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="ebfcb-120">IntelliSense quando o Option Infer está ligado</span><span class="sxs-lookup"><span data-stu-id="ebfcb-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="ebfcb-121">Na ilustração a seguir, o `Option Infer` está desativado.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="ebfcb-122">A variável na declaração `Dim someVar = 2` é declarada como um `Object` por inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="ebfcb-123">Neste exemplo, o **Option Strict** configuração é definida como **Off** no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ebfcb-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="ebfcb-124">![Exibição do IntelliSense da declaração. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="ebfcb-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="ebfcb-125">IntelliSense quando o Option Infer está desligado</span><span class="sxs-lookup"><span data-stu-id="ebfcb-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebfcb-126">Quando uma variável é declarada como um `Object`, o tipo de tempo de execução pode ser alterado enquanto o programa está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="ebfcb-127">executa operações chamadas *boxing* e *unboxing* para converter entre um `Object` e um tipo de valor, o que torna a execução mais lenta.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="ebfcb-128">Para obter informações sobre conversão boxing e unboxing, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebfcb-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="ebfcb-129">A inferência de tipo aplica-se no nível do procedimento e não fora de um procedimento em uma classe, estrutura, módulo ou interface.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="ebfcb-130">Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="ebfcb-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="ebfcb-131">Quando uma Instrução Option Infer Não Está Presente</span><span class="sxs-lookup"><span data-stu-id="ebfcb-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="ebfcb-132">Se o código-fonte não contém um `Option Infer` instrução, o **Option Infer** definição no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="ebfcb-133">Se o compilador de linha de comando é usado, o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador é usada.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="ebfcb-134">Para definir o Option Infer no IDE</span><span class="sxs-lookup"><span data-stu-id="ebfcb-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="ebfcb-135">No **Gerenciador de Soluções**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="ebfcb-136">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-136">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="ebfcb-137">Para obter mais informações, consulte [NIB: Gerenciando propriedades de projeto com o Designer de projeto](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="ebfcb-137">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="ebfcb-138">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-138">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="ebfcb-139">Definir o valor no **Option infer** caixa.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-139">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="ebfcb-140">Quando você cria um novo projeto, o **Option Infer** definição no **compilar** for definido como o **Option Infer** definindo no **padrões VB** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="ebfcb-141">Para acessar o **padrões VB** caixa de diálogo de **ferramentas** menu, clique em **opções**.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="ebfcb-142">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="ebfcb-143">A configuração inicial padrão na **padrões VB** é `On`.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-143">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="ebfcb-144">Para definir o Option Infer na linha de comando</span><span class="sxs-lookup"><span data-stu-id="ebfcb-144">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="ebfcb-145">Incluir o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador no **vbc** comando.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-145">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="ebfcb-146">Tipos de Dados e Valores Padrão</span><span class="sxs-lookup"><span data-stu-id="ebfcb-146">Default Data Types and Values</span></span>  
 <span data-ttu-id="ebfcb-147">A tabela a seguir descreve os resultados de várias combinações de especificar o tipo de dados e o inicializador em uma instrução `Dim`.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="ebfcb-148">Tipo de dados especificado?</span><span class="sxs-lookup"><span data-stu-id="ebfcb-148">Data type specified?</span></span>|<span data-ttu-id="ebfcb-149">Inicializador especificado?</span><span class="sxs-lookup"><span data-stu-id="ebfcb-149">Initializer specified?</span></span>|<span data-ttu-id="ebfcb-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebfcb-150">Example</span></span>|<span data-ttu-id="ebfcb-151">Resultado</span><span class="sxs-lookup"><span data-stu-id="ebfcb-151">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="ebfcb-152">Não</span><span class="sxs-lookup"><span data-stu-id="ebfcb-152">No</span></span>|<span data-ttu-id="ebfcb-153">Não</span><span class="sxs-lookup"><span data-stu-id="ebfcb-153">No</span></span>|`Dim qty`|<span data-ttu-id="ebfcb-154">Se o `Option Strict` estiver desativado (padrão), a variável é definida como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="ebfcb-155">Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="ebfcb-156">Não</span><span class="sxs-lookup"><span data-stu-id="ebfcb-156">No</span></span>|<span data-ttu-id="ebfcb-157">Sim</span><span class="sxs-lookup"><span data-stu-id="ebfcb-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="ebfcb-158">Se `Option Infer` estiver ativado (padrão), a variável usa o tipo de dados do inicializador.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="ebfcb-159">Consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="ebfcb-159">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="ebfcb-160">Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="ebfcb-161">Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="ebfcb-162">Sim</span><span class="sxs-lookup"><span data-stu-id="ebfcb-162">Yes</span></span>|<span data-ttu-id="ebfcb-163">Não</span><span class="sxs-lookup"><span data-stu-id="ebfcb-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="ebfcb-164">A variável é inicializada para o valor padrão para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="ebfcb-165">Para obter mais informações, consulte [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ebfcb-165">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="ebfcb-166">Sim</span><span class="sxs-lookup"><span data-stu-id="ebfcb-166">Yes</span></span>|<span data-ttu-id="ebfcb-167">Sim</span><span class="sxs-lookup"><span data-stu-id="ebfcb-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="ebfcb-168">Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ebfcb-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebfcb-169">Example</span></span>  
 <span data-ttu-id="ebfcb-170">Os exemplos a seguir demonstram como a instrução `Option Infer` habilita a inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ebfcb-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebfcb-171">Example</span></span>  
 <span data-ttu-id="ebfcb-172">O exemplo a seguir demonstra o tipo de tempo de execução pode ser diferente quando uma variável é identificada como um `Object`.</span><span class="sxs-lookup"><span data-stu-id="ebfcb-172">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ebfcb-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebfcb-173">See Also</span></span>  
 [<span data-ttu-id="ebfcb-174">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="ebfcb-174">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="ebfcb-175">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="ebfcb-175">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="ebfcb-176">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="ebfcb-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="ebfcb-177">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="ebfcb-177">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="ebfcb-178">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="ebfcb-178">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="ebfcb-179">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="ebfcb-179">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="ebfcb-180">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="ebfcb-180">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="ebfcb-181">Conversão boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="ebfcb-181">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
