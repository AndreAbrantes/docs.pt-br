---
title: 'Como: criar um fluxo de trabalho de fluxograma'
description: Este artigo descreve como criar um fluxo de trabalho que usa atividades internas e as atividades personalizadas do artigo anterior.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: f8e0703591629a72e0a8f6eeb05dd9d19c8c4c91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275821"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="76679-103">Como: criar um fluxo de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="76679-103">How to: Create a Flowchart Workflow</span></span>

<span data-ttu-id="76679-104">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="76679-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="76679-105">Este tópico percorre a criação de um fluxo de trabalho que usa atividades internas, como a <xref:System.Activities.Statements.Flowchart> atividade, e as atividades personalizadas do tópico [como criar uma atividade](how-to-create-an-activity.md) anterior.</span><span class="sxs-lookup"><span data-stu-id="76679-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="76679-106">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="76679-106">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76679-107">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="76679-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="76679-108">Para concluir este tópico, você deve primeiro concluir [como: criar uma atividade](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="76679-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76679-109">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="76679-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="76679-110">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="76679-110">To create the workflow</span></span>  
  
1. <span data-ttu-id="76679-111">Clique com o botão direito do mouse em **NumberGuessWorkflowActivities** em **Gerenciador de soluções** e selecione **Adicionar**, **novo item**.</span><span class="sxs-lookup"><span data-stu-id="76679-111">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="76679-112">No nó **itens comuns** **instalados**, selecione fluxo de **trabalho**.</span><span class="sxs-lookup"><span data-stu-id="76679-112">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="76679-113">Selecione **Atividade** na lista **Fluxo de Trabalho**.</span><span class="sxs-lookup"><span data-stu-id="76679-113">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="76679-114">Digite `FlowchartNumberGuessWorkflow` na caixa **nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="76679-114">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="76679-115">Arraste uma atividade de **fluxograma** da seção **fluxograma** da **caixa de ferramentas** e solte-a no rótulo **soltar atividade aqui** na superfície de design do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="76679-115">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="76679-116">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="76679-116">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="76679-117">Clique duas vezes em **FlowchartNumberGuessWorkflow. XAML** em **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, se ele ainda não estiver sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="76679-117">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="76679-118">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **argumentos** .</span><span class="sxs-lookup"><span data-stu-id="76679-118">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="76679-119">Clique em **Criar Argumento**.</span><span class="sxs-lookup"><span data-stu-id="76679-119">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="76679-120">Digite na `MaxNumber` caixa **nome** , selecione **em na** lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e pressione ENTER para salvar o argumento...</span><span class="sxs-lookup"><span data-stu-id="76679-120">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="76679-121">Clique em **Criar Argumento**.</span><span class="sxs-lookup"><span data-stu-id="76679-121">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="76679-122">Digite `Turns` na caixa de **nome** que está abaixo do argumento recém-adicionado `MaxNumber` , selecione **fora** na lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e, em seguida, pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="76679-122">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="76679-123">Clique em **Argumentos** no lado inferior esquerdo do designer de atividade para fechar o painel **Argumentos**.</span><span class="sxs-lookup"><span data-stu-id="76679-123">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="76679-124">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="76679-124">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="76679-125">Clique em **Criar Variável**.</span><span class="sxs-lookup"><span data-stu-id="76679-125">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="76679-126">Se nenhuma caixa **criar variável** for exibida, clique na <xref:System.Activities.Statements.Flowchart> atividade na superfície do designer de fluxo de trabalho para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="76679-126">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="76679-127">Digite `Guess` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="76679-127">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="76679-128">Clique em **Criar Variável**.</span><span class="sxs-lookup"><span data-stu-id="76679-128">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="76679-129">Digite `Target` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="76679-129">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="76679-130">Clique em **Variáveis** no lado inferior esquerdo do designer de atividade para fechar o painel **Variáveis**.</span><span class="sxs-lookup"><span data-stu-id="76679-130">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="76679-131">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="76679-131">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="76679-132">Arraste uma atividade **atribuir** da seção **primitivos** da caixa de **ferramentas** e focalize-a sobre o nó **inicial** , que está na parte superior do fluxograma.</span><span class="sxs-lookup"><span data-stu-id="76679-132">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="76679-133">Quando a atividade **assign** estiver sobre o nó **inicial** , três triângulos aparecerão em torno do nó **inicial** .</span><span class="sxs-lookup"><span data-stu-id="76679-133">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="76679-134">Descarte a atividade **atribuir** no triângulo que está diretamente abaixo do nó de **início** .</span><span class="sxs-lookup"><span data-stu-id="76679-134">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="76679-135">Isso vinculará os dois itens em conjunto e designará a atividade **atribuir** como a primeira atividade no fluxograma.</span><span class="sxs-lookup"><span data-stu-id="76679-135">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="76679-136">As atividades também podem ser indicadas como a atividade de início no fluxo de trabalho manualmente vinculando-as ao nó de origem.</span><span class="sxs-lookup"><span data-stu-id="76679-136">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="76679-137">Para fazer isso, passe o mouse sobre o nó **inicial** , clique em um dos retângulos que aparecem quando o mouse está sobre o nó **inicial** e arraste a linha de conexão para baixo até a atividade desejada e solte-a em um dos retângulos que aparecem.</span><span class="sxs-lookup"><span data-stu-id="76679-137">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="76679-138">Você também pode designar uma atividade como a atividade inicial clicando com o botão direito do mouse nela e escolhendo **definir como nó inicial**.</span><span class="sxs-lookup"><span data-stu-id="76679-138">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="76679-139">Digite `Target` na caixa **para** e a expressão a seguir na caixa **Inserir uma expressão C#** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="76679-139">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="76679-140">Se a janela da **Caixa de Ferramentas** não abrir, selecione **Caixa de Ferramentas** no menu **Exibir**.</span><span class="sxs-lookup"><span data-stu-id="76679-140">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="76679-141">Arraste uma atividade de **prompt** da seção **NumberGuessWorkflowActivities** da **caixa de ferramentas**, solte-a abaixo da atividade **atribuir** da etapa anterior e conecte a atividade de **prompt** à atividade **atribuir** .</span><span class="sxs-lookup"><span data-stu-id="76679-141">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="76679-142">Há três modos de conectar as duas atividades.</span><span class="sxs-lookup"><span data-stu-id="76679-142">There are three ways to connect the two activities.</span></span> <span data-ttu-id="76679-143">A primeira maneira é conectá-los à medida que você remove a atividade **prompt** no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="76679-143">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="76679-144">Conforme você está arrastando a atividade de **prompt** para o fluxo de trabalho, passe o mouse sobre a atividade **atribuir** e solte-a em um dos quatro triângulos que aparecem quando a atividade de **prompt** está sobre a atividade **atribuir** .</span><span class="sxs-lookup"><span data-stu-id="76679-144">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="76679-145">A segunda maneira é descartar a atividade de **prompt** no fluxo de trabalho no local desejado.</span><span class="sxs-lookup"><span data-stu-id="76679-145">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="76679-146">Em seguida, passe o mouse sobre a atividade **atribuir** e arraste um dos retângulos que aparece até a atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="76679-146">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="76679-147">Arraste o mouse para que a linha de conexão da atividade **atribuir** se conecte a um dos retângulos da atividade de **prompt** e, em seguida, solte o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="76679-147">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="76679-148">A terceira maneira é muito semelhante à primeira maneira, exceto que, em vez de arrastar a atividade **prompt** da **caixa de ferramentas**, você a arrasta de seu local na superfície de design do fluxo de trabalho, passa o mouse sobre a atividade **atribuir** e a solta em um dos triângulos que aparece.</span><span class="sxs-lookup"><span data-stu-id="76679-148">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="76679-149">Na **janela Propriedades** da atividade **prompt** , digite `"EnterGuess"` incluindo as aspas na caixa valor da propriedade **BookmarkName** .</span><span class="sxs-lookup"><span data-stu-id="76679-149">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="76679-150">Digite na `Guess` caixa valor da propriedade de **resultado** e digite a expressão a seguir na caixa de propriedade **texto** .</span><span class="sxs-lookup"><span data-stu-id="76679-150">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="76679-151">Se a **janela Propriedades** não for exibida, selecione **janela Propriedades** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="76679-151">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="76679-152">Arraste uma atividade **atribuir** da seção **primitivos** da caixa de **ferramentas** e conecte-a usando um dos métodos descritos na etapa anterior para que ela esteja abaixo da atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="76679-152">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="76679-153">Digite `Turns` na caixa **para** e `Turns + 1` na caixa **Inserir uma expressão C#**  ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="76679-153">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="76679-154">Arraste um **FlowDecision** da seção **fluxograma** da caixa de **ferramentas** e conecte-o abaixo da atividade **atribuir** .</span><span class="sxs-lookup"><span data-stu-id="76679-154">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="76679-155">Na **janela Propriedades**, digite a expressão a seguir na caixa valor da propriedade de **condição** .</span><span class="sxs-lookup"><span data-stu-id="76679-155">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="76679-156">Arraste outra atividade **FlowDecision** da **caixa de ferramentas** e solte-a abaixo da primeira.</span><span class="sxs-lookup"><span data-stu-id="76679-156">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="76679-157">Conecte as duas atividades arrastando do retângulo rotulado como **falso** na atividade **FlowDecision** superior para o retângulo na parte superior da segunda atividade **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="76679-157">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="76679-158">Se você não vir os rótulos **verdadeiro** e **falso** no **FlowDecision**, passe o mouse sobre o **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="76679-158">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="76679-159">Clique na segunda atividade **FlowDecision** para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="76679-159">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="76679-160">Na **janela Propriedades**, digite a expressão a seguir na caixa valor da propriedade de **condição** .</span><span class="sxs-lookup"><span data-stu-id="76679-160">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
10. <span data-ttu-id="76679-161">Arraste duas atividades **WriteLine** da seção **primitivas** da caixa de **ferramentas** e solte-as para que elas fiquem lado a lado abaixo das duas atividades **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="76679-161">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="76679-162">Conecte a ação **verdadeira** da atividade **FlowDecision** inferior à atividade **WriteLine** mais à esquerda e a ação **false** para a atividade **WriteLine** mais à direita.</span><span class="sxs-lookup"><span data-stu-id="76679-162">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="76679-163">Clique na atividade **WriteLine** mais à esquerda para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** na **janela Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="76679-163">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="76679-164">Conecte o **WriteLine** ao lado esquerdo da atividade de **prompt** que está acima dele.</span><span class="sxs-lookup"><span data-stu-id="76679-164">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="76679-165">Clique na atividade **WriteLine** mais à direita para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** na **janela Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="76679-165">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="76679-166">Conecte a atividade **WriteLine** ao lado direito da atividade de **prompt** acima dela.</span><span class="sxs-lookup"><span data-stu-id="76679-166">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="76679-167">O exemplo a seguir ilustra o fluxo de trabalho concluído.</span><span class="sxs-lookup"><span data-stu-id="76679-167">The following example illustrates the completed workflow.</span></span>  
  
     ![Diagrama que mostra um fluxograma de Windows Workflow Foundation concluído.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="76679-169">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="76679-169">To build the workflow</span></span>  
  
1. <span data-ttu-id="76679-170">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="76679-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="76679-171">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico [como: executar um fluxo de trabalho](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="76679-171">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="76679-172">Se você já tiver concluído a etapa [como executar um fluxo de trabalho](how-to-run-a-workflow.md) com um estilo diferente de fluxo de trabalho e desejar executá-lo usando o fluxo de trabalho de fluxograma nesta etapa, pule para a seção [para criar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [como executar um fluxo de trabalho](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="76679-172">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76679-173">Veja também</span><span class="sxs-lookup"><span data-stu-id="76679-173">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="76679-174">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="76679-174">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="76679-175">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="76679-175">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="76679-176">Guia de introdução ao tutorial</span><span class="sxs-lookup"><span data-stu-id="76679-176">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="76679-177">Como: criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="76679-177">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="76679-178">Como: executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="76679-178">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
