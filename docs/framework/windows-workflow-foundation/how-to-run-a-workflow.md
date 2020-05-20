---
title: Como executar um fluxo de trabalho
description: Este artigo mostra como criar um host de fluxo de trabalho e executar o fluxo de trabalho definido em um artigo anterior nesta Windows Workflow Foundation série de tutoriais.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 86062dd5147e6e354833928fd98bd1f6b5de9114
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421495"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="45abe-103">Como executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45abe-103">How to: Run a Workflow</span></span>
<span data-ttu-id="45abe-104">Este tópico é uma continuação do tutorial de Introdução Windows Workflow Foundation e discute como criar um host de fluxo de trabalho e executar o fluxo de trabalho definido no tópico [como criar um fluxo](how-to-create-a-workflow.md) de trabalho anterior.</span><span class="sxs-lookup"><span data-stu-id="45abe-104">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="45abe-105">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="45abe-105">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="45abe-106">Para concluir este tópico, você deve primeiro concluir [como: criar uma atividade](how-to-create-an-activity.md) e [como criar um fluxo de trabalho](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="45abe-106">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
> <span data-ttu-id="45abe-107">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="45abe-107">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="45abe-108">Para criar o projeto de host de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45abe-108">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="45abe-109">Abra a solução do tópico [como: criar uma atividade](how-to-create-an-activity.md) anterior usando o Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="45abe-109">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="45abe-110">Clique com o botão direito do mouse na solução **WF45GettingStartedTutorial** em **Gerenciador de soluções** e selecione **Adicionar**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="45abe-110">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="45abe-111">Se a janela do **Gerenciador de Soluções** não abrir, selecione **Gerenciador de Soluções** no menu **Exibir**.</span><span class="sxs-lookup"><span data-stu-id="45abe-111">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="45abe-112">No nó **instalado** , selecione **Visual C#**, **fluxo de trabalho** (ou **Visual Basic**, fluxo de **trabalho**).</span><span class="sxs-lookup"><span data-stu-id="45abe-112">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="45abe-113">Dependendo da linguagem de programação que esteja configurada como linguagem primária no Visual Studio, o nó **Visual C#** ou **Visual Basic** poderá estar sob o nó **Outras Linguagens** no nó **Instalado**.</span><span class="sxs-lookup"><span data-stu-id="45abe-113">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="45abe-114">Certifique-se de que o **.NET Framework 4.5** esteja selecionado na lista suspensa de versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45abe-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="45abe-115">Selecione **aplicativo de console de fluxo de trabalho** na lista **fluxo de trabalho** .</span><span class="sxs-lookup"><span data-stu-id="45abe-115">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="45abe-116">Digite `NumberGuessWorkflowHost` na caixa **nome** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="45abe-116">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="45abe-117">Isso cria um aplicativo de fluxo de trabalho inicial com suporte básico de hospedagem de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-117">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="45abe-118">Esse código básico de hospedagem é modificado e usado para executar o aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-118">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="45abe-119">Clique com o botão direito do mouse no projeto **NumberGuessWorkflowHost** recém-adicionado no **Gerenciador de soluções** e selecione **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="45abe-119">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="45abe-120">Selecione **solução** na lista **Adicionar referência** , marque a caixa de seleção ao lado de **NumberGuessWorkflowActivities**e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="45abe-120">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="45abe-121">Clique com o botão direito do mouse em **Workflow1. XAML** em **Gerenciador de soluções** e escolha **excluir**.</span><span class="sxs-lookup"><span data-stu-id="45abe-121">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="45abe-122">Clique em **OK** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="45abe-122">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="45abe-123">Para modificar o código de hospedagem do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45abe-123">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="45abe-124">Clique duas vezes em **Program.cs** ou **Module1. vb** em **Gerenciador de soluções** para exibir o código.</span><span class="sxs-lookup"><span data-stu-id="45abe-124">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    > <span data-ttu-id="45abe-125">Se a janela do **Gerenciador de Soluções** não abrir, selecione **Gerenciador de Soluções** no menu **Exibir**.</span><span class="sxs-lookup"><span data-stu-id="45abe-125">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="45abe-126">Como esse projeto foi criado usando o modelo de **aplicativo do console de fluxo de trabalho** , **Program.cs** ou **Module1. vb** contém o código de hospedagem do fluxo de trabalho básico a seguir.</span><span class="sxs-lookup"><span data-stu-id="45abe-126">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     <span data-ttu-id="45abe-127">Esse código de hospedagem gerado usa <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="45abe-127">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="45abe-128"><xref:System.Activities.WorkflowInvoker> fornece uma maneira simples para chamar um fluxo de trabalho como se fosse uma chamada de método e pode ser usado somente para os fluxos de trabalho que não usam persistência.</span><span class="sxs-lookup"><span data-stu-id="45abe-128"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="45abe-129"><xref:System.Activities.WorkflowApplication> fornece um modelo mais avançado para executar fluxos de trabalho que incluem a notificação de eventos de ciclo de vida, o controle de execução, o reinício do indicador e a persistência.</span><span class="sxs-lookup"><span data-stu-id="45abe-129"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="45abe-130">Este exemplo usa indicadores e o <xref:System.Activities.WorkflowApplication> é usado para hospedar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-130">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="45abe-131">Adicione a seguinte `using` instrução ou **Imports** na parte superior do **Program.cs** ou **Module1. vb** abaixo das instruções **using** ou **Imports** existentes.</span><span class="sxs-lookup"><span data-stu-id="45abe-131">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="45abe-132">Substituir as linhas de código que usam <xref:System.Activities.WorkflowInvoker> com o código de hospedagem básica <xref:System.Activities.WorkflowApplication> a seguir.</span><span class="sxs-lookup"><span data-stu-id="45abe-132">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="45abe-133">Este código de hospedagem de exemplo demonstra as etapas básicas para hospedar e chamar um fluxo de trabalho, mas ainda não contém a funcionalidade para executar com êxito o fluxo de trabalho a partir deste tópico.</span><span class="sxs-lookup"><span data-stu-id="45abe-133">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="45abe-134">Nas etapas a seguir, esse código básico é modificado e os recursos adicionais são adicionados até que o aplicativo esteja concluído.</span><span class="sxs-lookup"><span data-stu-id="45abe-134">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="45abe-135">Substitua `Workflow1` esses exemplos pelo `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` ou `StateMachineNumberGuessWorkflow` , dependendo de qual fluxo de trabalho você concluiu na etapa anterior [como criar um fluxo de trabalho](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="45abe-135">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="45abe-136">Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-136">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="45abe-137">Esse código cria um <xref:System.Activities.WorkflowApplication>, assina três eventos do ciclo de vida de fluxo de trabalho, inicia o fluxo de trabalho com uma chamada para <xref:System.Activities.WorkflowApplication.Run%2A> e aguarda que o fluxo de trabalho seja concluído.</span><span class="sxs-lookup"><span data-stu-id="45abe-137">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="45abe-138">Quando o fluxo de trabalho estiver concluído, o <xref:System.Threading.AutoResetEvent> é definido e o aplicativo host é concluído.</span><span class="sxs-lookup"><span data-stu-id="45abe-138">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="45abe-139">Para definir argumentos de entrada de um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45abe-139">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="45abe-140">Adicione a seguinte instrução na parte superior de **Program.cs** ou **Module1. vb** abaixo das `using` instruções ou existentes `Imports` .</span><span class="sxs-lookup"><span data-stu-id="45abe-140">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="45abe-141">Substitua a linha de código que cria uma nova <xref:System.Activities.WorkflowApplication> pelo código a seguir que cria e passa um dicionário dos parâmetros para o fluxo de trabalho quando ele é criado.</span><span class="sxs-lookup"><span data-stu-id="45abe-141">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="45abe-142">Substitua `Workflow1` esses exemplos pelo `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` ou `StateMachineNumberGuessWorkflow` , dependendo de qual fluxo de trabalho você concluiu na etapa anterior [como criar um fluxo de trabalho](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="45abe-142">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="45abe-143">Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-143">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="45abe-144">Este dicionário contém um elemento com uma chave `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="45abe-144">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="45abe-145">As chaves do dicionário de entrada correspondem a argumentos de entrada na atividade raiz do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-145">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="45abe-146">`MaxNumber` é usado pelo fluxo de trabalho para determinar o limite superior para o número gerado aleatoriamente.</span><span class="sxs-lookup"><span data-stu-id="45abe-146">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="45abe-147">Para recuperar argumentos de saída de um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45abe-147">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="45abe-148">Modifique o manipulador <xref:System.Activities.WorkflowApplication.Completed%2A> para recuperar e exibir o número de sequências usadas pelo fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-148">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="45abe-149">Para retomar um indicador</span><span class="sxs-lookup"><span data-stu-id="45abe-149">To resume a bookmark</span></span>

1. <span data-ttu-id="45abe-150">Adicione o código a seguir na parte superior do método `Main` imediatamente após a instrução <xref:System.Threading.AutoResetEvent> existente.</span><span class="sxs-lookup"><span data-stu-id="45abe-150">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="45abe-151">Adicione o manipulador <xref:System.Activities.WorkflowApplication.Idle%2A> a seguir abaixo dos manipuladores existentes do ciclo de vida de fluxo de trabalho em `Main`.</span><span class="sxs-lookup"><span data-stu-id="45abe-151">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="45abe-152">Cada vez que o fluxo de trabalho se torna ocioso aguardando a próxima estimativa, esse manipulador é chamado e o `idleAction` <xref:System.Threading.AutoResetEvent> é definido.</span><span class="sxs-lookup"><span data-stu-id="45abe-152">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="45abe-153">O código na etapa a seguir usa `idleEvent` e `syncEvent` para determinar se o fluxo de trabalho está esperando o próximo palpite ou está concluído.</span><span class="sxs-lookup"><span data-stu-id="45abe-153">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="45abe-154">Neste exemplo, o aplicativo host usa eventos de redefinição automática nos manipuladores <xref:System.Activities.WorkflowApplication.Completed%2A> e de <xref:System.Activities.WorkflowApplication.Idle%2A> para sincronizar o aplicativo host com o progresso do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-154">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="45abe-155">Não é necessário bloquear e esperar que o fluxo de trabalho fique inativo antes de retomar um indicador, mas, nesse exemplo, os eventos de sincronização são necessários para que o host saiba se o fluxo de trabalho está concluído ou se está aguardando mais entrada do usuário usando o <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="45abe-155">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="45abe-156">Para obter mais informações, consulte [indicadores](bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="45abe-156">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="45abe-157">Remova a chamada para `WaitOne` e substitua-a pelo código para coletar entrada do usuário e retomar o <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="45abe-157">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="45abe-158">Remova a seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="45abe-158">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="45abe-159">Substitua-a pelo exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="45abe-159">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="to-build-and-run-the-application"></a><a name="BKMK_ToRunTheApplication"></a><span data-ttu-id="45abe-160">Para compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="45abe-160">To build and run the application</span></span>

1. <span data-ttu-id="45abe-161">Clique com o botão direito do mouse em **NumberGuessWorkflowHost** em **Gerenciador de soluções** e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="45abe-161">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="45abe-162">Pressione CTRL+F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45abe-162">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="45abe-163">Tente determinar o número no menor número de sequências possível.</span><span class="sxs-lookup"><span data-stu-id="45abe-163">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="45abe-164">Para testar o aplicativo com um dos outros estilos de fluxo de trabalho, substitua `Workflow1` no código que cria o <xref:System.Activities.WorkflowApplication> por `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow` ou `StateMachineNumberGuessWorkflow`, dependendo de qual estilo de fluxo de trabalho você deseja.</span><span class="sxs-lookup"><span data-stu-id="45abe-164">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="45abe-165">Para obter instruções sobre como adicionar persistência a um aplicativo de fluxo de trabalho, consulte o próximo tópico [como: criar e executar um fluxo de trabalho de longa execução](how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="45abe-165">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="45abe-166">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45abe-166">Example</span></span>
 <span data-ttu-id="45abe-167">O exemplo a seguir é a listagem de código completa para o método `Main`.</span><span class="sxs-lookup"><span data-stu-id="45abe-167">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="45abe-168">Substitua `Workflow1` esses exemplos pelo `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` ou `StateMachineNumberGuessWorkflow` , dependendo de qual fluxo de trabalho você concluiu na etapa anterior [como criar um fluxo de trabalho](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="45abe-168">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="45abe-169">Se você não substituir `Workflow1`, receberá erros de compilação quando tentar criar ou executar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="45abe-169">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="45abe-170">Veja também</span><span class="sxs-lookup"><span data-stu-id="45abe-170">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="45abe-171">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="45abe-171">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="45abe-172">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="45abe-172">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="45abe-173">Como criar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45abe-173">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="45abe-174">Como criar e executar um fluxo de trabalho de execução longa</span><span class="sxs-lookup"><span data-stu-id="45abe-174">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="45abe-175">Esperando entrada em um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="45abe-175">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="45abe-176">Hospedando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="45abe-176">Hosting Workflows</span></span>](hosting-workflows.md)
