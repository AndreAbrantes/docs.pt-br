---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 94a8b43a891df9837925869e17fac4536a995264
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414266"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="6ad68-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ad68-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="6ad68-103">Faz com que o compilador trate a primeira ocorrência de um aviso como um erro.</span><span class="sxs-lookup"><span data-stu-id="6ad68-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ad68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ad68-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ad68-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="6ad68-105">Arguments</span></span>  
  
|<span data-ttu-id="6ad68-106">Termo</span><span class="sxs-lookup"><span data-stu-id="6ad68-106">Term</span></span>|<span data-ttu-id="6ad68-107">Definição</span><span class="sxs-lookup"><span data-stu-id="6ad68-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="6ad68-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="6ad68-108">+ &#124; -</span></span>|<span data-ttu-id="6ad68-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6ad68-109">Optional.</span></span> <span data-ttu-id="6ad68-110">Por padrão, `-warnaserror-` está em vigor; os avisos não impedem que o compilador produza um arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6ad68-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="6ad68-111">A opção `-warnaserror`, que é o mesmo que `-warnaserror+`, faz com que os avisos sejam tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="6ad68-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="6ad68-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6ad68-112">Optional.</span></span> <span data-ttu-id="6ad68-113">A lista delimitada por vírgulas dos números de identificação do aviso aos quais se aplica a opção `-warnaserror`.</span><span class="sxs-lookup"><span data-stu-id="6ad68-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="6ad68-114">Se nenhuma identificação de aviso for especificada, a opção `-warnaserror` se aplica a todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="6ad68-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ad68-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ad68-115">Remarks</span></span>  
 <span data-ttu-id="6ad68-116">A opção `-warnaserror` trata todos os avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="6ad68-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="6ad68-117">Quaisquer mensagens que normalmente seriam relatadas como avisos são, em vez disso, relatadas como erros.</span><span class="sxs-lookup"><span data-stu-id="6ad68-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="6ad68-118">O compilador relatará as ocorrências subsequentes do mesmo aviso como avisos.</span><span class="sxs-lookup"><span data-stu-id="6ad68-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="6ad68-119">Por padrão, `-warnaserror-` está em vigor, o que faz com que os avisos sejam apenas informativos.</span><span class="sxs-lookup"><span data-stu-id="6ad68-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="6ad68-120">A opção `-warnaserror`, que é o mesmo que `-warnaserror+`, faz com que os avisos sejam tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="6ad68-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="6ad68-121">Se você deseja que apenas avisos específicos sejam tratados como erros, pode especificar uma lista separada por vírgulas de números de aviso para serem tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="6ad68-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ad68-122">A opção `-warnaserror` não controla como os avisos são exibidos.</span><span class="sxs-lookup"><span data-stu-id="6ad68-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="6ad68-123">Use a opção [-nowarn](nowarn.md) para desativar os avisos.</span><span class="sxs-lookup"><span data-stu-id="6ad68-123">Use the [-nowarn](nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="6ad68-124">Para definir -warnaserror para tratar todos os avisos como erros no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ad68-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="6ad68-125">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="6ad68-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6ad68-126">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6ad68-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="6ad68-127">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="6ad68-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="6ad68-128">3. Certifique-se de que a caixa de seleção **desabilitar todos os avisos** esteja desmarcada.</span><span class="sxs-lookup"><span data-stu-id="6ad68-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="6ad68-129">4. Marque a caixa de seleção **tratar todos os avisos como erros** .</span><span class="sxs-lookup"><span data-stu-id="6ad68-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="6ad68-130">Para definir -warnaserror para tratar avisos específicos como erros no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ad68-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="6ad68-131">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="6ad68-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6ad68-132">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6ad68-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="6ad68-133">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="6ad68-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="6ad68-134">3. Certifique-se de que a caixa de seleção **desabilitar todos os avisos** esteja desmarcada.</span><span class="sxs-lookup"><span data-stu-id="6ad68-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="6ad68-135">4. Verifique se a caixa de seleção **tratar todos os avisos como erros** está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="6ad68-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="6ad68-136">5. Selecione o **erro** da coluna de **notificação** adjacente ao aviso que deve ser tratado como um erro.</span><span class="sxs-lookup"><span data-stu-id="6ad68-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ad68-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ad68-137">Example</span></span>  
 <span data-ttu-id="6ad68-138">O código a seguir compila `In.vb` e direciona o compilador para exibir um erro para a primeira ocorrência de cada aviso que ele encontre.</span><span class="sxs-lookup"><span data-stu-id="6ad68-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="6ad68-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ad68-139">Example</span></span>  
 <span data-ttu-id="6ad68-140">O código a seguir compila `T2.vb` e trata apenas o aviso de variáveis locais não utilizadas (42024) como um erro.</span><span class="sxs-lookup"><span data-stu-id="6ad68-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ad68-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="6ad68-141">See also</span></span>

- [<span data-ttu-id="6ad68-142">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ad68-142">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6ad68-143">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ad68-143">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="6ad68-144">Configurando avisos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ad68-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
