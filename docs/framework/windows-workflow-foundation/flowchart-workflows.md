---
title: Fluxos de trabalho do fluxograma
description: Este artigo descreve a atividade FlowChart, que normalmente é usada para implementar fluxos de trabalho não sequenciais no Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: ce0661653a1d50b3f7264246b810faabbd12bf5f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419909"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="8e922-103">Fluxos de trabalho do fluxograma</span><span class="sxs-lookup"><span data-stu-id="8e922-103">Flowchart Workflows</span></span>

<span data-ttu-id="8e922-104">Um fluxograma é um paradigma conhecido para criar programas.</span><span class="sxs-lookup"><span data-stu-id="8e922-104">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="8e922-105">A atividade do fluxograma é normalmente usada para implementar fluxos de trabalho não-sequenciais, mas pode ser usada para fluxos de trabalho sequenciais se nenhum nó de `FlowDecision` é usado.</span><span class="sxs-lookup"><span data-stu-id="8e922-105">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="8e922-106">Estrutura de fluxo de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="8e922-106">Flowchart workflow structure</span></span>

 <span data-ttu-id="8e922-107">Uma atividade do fluxograma é uma atividade que contém uma coleção de atividades a ser executadas.</span><span class="sxs-lookup"><span data-stu-id="8e922-107">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="8e922-108">Os fluxogramas também contêm os elementos de controle de fluxo como <xref:System.Activities.Statements.FlowDecision> e <xref:System.Activities.Statements.FlowSwitch%601> que a execução direta entre atividades contidas base nos valores das variáveis.</span><span class="sxs-lookup"><span data-stu-id="8e922-108">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="8e922-109">Tipos de nós de fluxo</span><span class="sxs-lookup"><span data-stu-id="8e922-109">Types of flow nodes</span></span>

 <span data-ttu-id="8e922-110">Os diferentes tipos de elementos são usados dependendo do tipo de controle de fluxo necessária quando o elemento é executado.</span><span class="sxs-lookup"><span data-stu-id="8e922-110">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="8e922-111">Os tipos de elementos fluxograma incluem:</span><span class="sxs-lookup"><span data-stu-id="8e922-111">Types of flowchart elements include:</span></span>

- <span data-ttu-id="8e922-112">`FlowStep` - modelos uma etapa de execução no fluxograma.</span><span class="sxs-lookup"><span data-stu-id="8e922-112">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="8e922-113">`FlowDecision` - ramificações de execução com base em uma condição boolean, semelhante a <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="8e922-113">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="8e922-114">`FlowSwitch` – ramificações de execução com base em uma opção exclusivo, semelhante a <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="8e922-114">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="8e922-115">Cada link tem uma propriedade de `Action` que define <xref:System.Activities.ActivityAction> que pode ser usado para executar atividades filhos, e uma ou mais propriedades de `Next` que definem que elemento ou elementos a executar quando o elemento atual concluir a execução.</span><span class="sxs-lookup"><span data-stu-id="8e922-115">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="8e922-116">Criando uma sequência de atividade básica com um nó FlowStep</span><span class="sxs-lookup"><span data-stu-id="8e922-116">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="8e922-117">Para modelar uma sequência básica em duas atividades que executam por sua vez, o elemento de `FlowStep` é usado.</span><span class="sxs-lookup"><span data-stu-id="8e922-117">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="8e922-118">No exemplo a seguir, dois elementos de `FlowStep` são usados para executar em ordem duas atividades.</span><span class="sxs-lookup"><span data-stu-id="8e922-118">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

```xml
<Flowchart>
  <FlowStep>
    <Assign DisplayName="Get Name">
      <Assign.To>
        <OutArgument x:TypeArguments="x:String">[result]</OutArgument>
      </Assign.To>
      <Assign.Value>
        <InArgument x:TypeArguments="x:String">["User"]</InArgument>
      </Assign.Value>
    </Assign>
    <FlowStep.Next>
      <FlowStep>
        <WriteLine Text="Hello, " & [result]/>
      </FlowStep>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="8e922-119">Criando um fluxograma condicional com um nó FlowDecision</span><span class="sxs-lookup"><span data-stu-id="8e922-119">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="8e922-120">Para modelar um nó condicional de fluxo em um fluxo de trabalho do fluxograma (ou seja, para criar um link que funciona como o símbolo de decisão de um fluxograma tradicional), um nó de <xref:System.Activities.Statements.FlowDecision> é usado.</span><span class="sxs-lookup"><span data-stu-id="8e922-120">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="8e922-121">A propriedade de <xref:System.Activities.Statements.FlowDecision.Condition%2A> do nó é definida como uma expressão que define a condição, e as propriedades de <xref:System.Activities.Statements.FlowDecision.True%2A> e de <xref:System.Activities.Statements.FlowDecision.False%2A> são definidas para as instâncias de <xref:System.Activities.Statements.FlowNode> a ser executadas se a expressão avaliada como `true` ou a `false`.</span><span class="sxs-lookup"><span data-stu-id="8e922-121">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="8e922-122">O exemplo a seguir mostra como definir um fluxo de trabalho que usa um nó de <xref:System.Activities.Statements.FlowDecision> .</span><span class="sxs-lookup"><span data-stu-id="8e922-122">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

```xml
<Flowchart>
  <FlowStep>
    <Read Result="[s]"/>
    <FlowStep.Next>
      <FlowDecision>
        <IsEmpty Input="[s]" />
        <FlowDecision.True>
          <FlowStep>
            <Write Text="Empty"/>
          </FlowStep>
        </FlowDecision.True>
        <FlowDecision.False>
          <FlowStep>
            <Write Text="Non-Empty"/>
          </FlowStep>
        </FlowDecision.False>
      </FlowDecision>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="8e922-123">Criando um comutador exclusivo com um nó FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="8e922-123">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="8e922-124">Para modelar um fluxograma na qual o caminho selecionado é exclusivo com base em um valor correspondente, o nó de <xref:System.Activities.Statements.FlowSwitch%601> é usado.</span><span class="sxs-lookup"><span data-stu-id="8e922-124">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="8e922-125">A propriedade de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> é definida como <xref:System.Activities.Activity%601> com um parâmetro de tipo de <xref:System.Object> que define o valor para coincidir com opções.</span><span class="sxs-lookup"><span data-stu-id="8e922-125">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="8e922-126">A propriedade de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> define um dicionário de chaves e objetos de <xref:System.Activities.Statements.FlowNode> a correspondência com a expressão condicional, e um conjunto de objetos de <xref:System.Activities.Statements.FlowNode> que definem como a execução deve fluxo se os casos dados correspondem a expressão condicional.</span><span class="sxs-lookup"><span data-stu-id="8e922-126">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="8e922-127"><xref:System.Activities.Statements.FlowSwitch%601> também define uma propriedade de <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> que define como a execução deve fluxo se nenhum caso corresponde a expressão da condição.</span><span class="sxs-lookup"><span data-stu-id="8e922-127">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="8e922-128">O exemplo a seguir demonstra como definir um fluxo de trabalho que usa um elemento de <xref:System.Activities.Statements.FlowSwitch%601> .</span><span class="sxs-lookup"><span data-stu-id="8e922-128">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

```xml
<Flowchart>
  <FlowSwitch>
    <FlowStep x:Key="Red">
      <WriteRed/>
    </FlowStep>
    <FlowStep x:Key="Blue">
      <WriteBlue/>
    </FlowStep>
    <FlowStep x:Key="Green">
      <WriteGreen/>
    </FlowStep>
  </FlowSwitch>
</Flowchart>
```
