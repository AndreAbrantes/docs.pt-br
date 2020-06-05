---
title: Instrução Option Explicit
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: a352df0323cfeca1ea0e206ae45c3f85a2cd7da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404363"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="74969-102">Instrução Option Explicit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74969-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="74969-103">Força a declaração explícita de todas as variáveis em um arquivo ou permite declarações implícitas de variáveis.</span><span class="sxs-lookup"><span data-stu-id="74969-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74969-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74969-104">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="74969-105">Partes</span><span class="sxs-lookup"><span data-stu-id="74969-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="74969-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="74969-106">Optional.</span></span> <span data-ttu-id="74969-107">Habilita a `Option Explicit` verificação.</span><span class="sxs-lookup"><span data-stu-id="74969-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="74969-108">Se `On` ou `Off` não for especificado, o padrão será `On` .</span><span class="sxs-lookup"><span data-stu-id="74969-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="74969-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="74969-109">Optional.</span></span> <span data-ttu-id="74969-110">Desabilita a `Option Explicit` verificação.</span><span class="sxs-lookup"><span data-stu-id="74969-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74969-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="74969-111">Remarks</span></span>  
 <span data-ttu-id="74969-112">Quando `Option Explicit On` ou `Option Explicit` aparece em um arquivo, você deve declarar explicitamente todas as variáveis usando as `Dim` `ReDim` instruções ou.</span><span class="sxs-lookup"><span data-stu-id="74969-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="74969-113">Se você tentar usar um nome de variável não declarado, ocorrerá um erro no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="74969-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="74969-114">A `Option Explicit Off` instrução permite a declaração implícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="74969-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="74969-115">Se usado, a instrução `Option Explicit` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="74969-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74969-116">`Option Explicit`A configuração como `Off` geralmente não é uma prática recomendada.</span><span class="sxs-lookup"><span data-stu-id="74969-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="74969-117">Você poderia digitar incorretamente um nome de variável em um ou mais locais, o que levaria a resultados inesperados na execução do programa.</span><span class="sxs-lookup"><span data-stu-id="74969-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="74969-118">Quando uma instrução Option Explicit não está presente</span><span class="sxs-lookup"><span data-stu-id="74969-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="74969-119">Se o código-fonte não contiver uma `Option Explicit` instrução, a configuração **Option Explicit** na [página Compile, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) será usada.</span><span class="sxs-lookup"><span data-stu-id="74969-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="74969-120">Se o compilador de linha de comando for usado, a opção de compilador [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) será usada.</span><span class="sxs-lookup"><span data-stu-id="74969-120">If the command-line compiler is used, the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="74969-121">Para definir a opção Explicit no IDE</span><span class="sxs-lookup"><span data-stu-id="74969-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="74969-122">Em **Gerenciador de soluções**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="74969-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="74969-123">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="74969-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="74969-124">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="74969-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="74969-125">Defina o valor na caixa **Option Explicit** .</span><span class="sxs-lookup"><span data-stu-id="74969-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="74969-126">Quando você cria um novo projeto, a **opção configuração explícita** na guia **Compilar** é definida como a **opção configuração explícita** na caixa de diálogo **padrões do VB** .</span><span class="sxs-lookup"><span data-stu-id="74969-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="74969-127">Para acessar a caixa de diálogo **padrões do VB** , no menu **ferramentas** , clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="74969-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="74969-128">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="74969-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="74969-129">A configuração padrão inicial em **padrões do VB** é `On` .</span><span class="sxs-lookup"><span data-stu-id="74969-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="74969-130">Para definir a opção Explicit na linha de comando</span><span class="sxs-lookup"><span data-stu-id="74969-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="74969-131">Inclua a opção de compilador [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) no comando **Vbc** .</span><span class="sxs-lookup"><span data-stu-id="74969-131">Include the [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74969-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74969-132">Example</span></span>  
 <span data-ttu-id="74969-133">O exemplo a seguir usa a `Option Explicit` instrução para forçar a declaração explícita de todas as variáveis.</span><span class="sxs-lookup"><span data-stu-id="74969-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="74969-134">A tentativa de usar uma variável não declarada causa um erro no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="74969-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="74969-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="74969-135">See also</span></span>

- [<span data-ttu-id="74969-136">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="74969-136">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="74969-137">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="74969-137">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="74969-138">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="74969-138">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="74969-139">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="74969-139">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="74969-140">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="74969-140">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="74969-141">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="74969-141">-optionexplicit</span></span>](../../reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="74969-142">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="74969-142">-optionstrict</span></span>](../../reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="74969-143">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="74969-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
