---
title: Criação de atividade de fluxo de trabalho usando a classe de atividades
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 21f1c8b1249d41029fa7a19360e96ad866c823a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293838"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="edabe-102">Criação de atividade de fluxo de trabalho usando a classe de atividades</span><span class="sxs-lookup"><span data-stu-id="edabe-102">Workflow Activity Authoring Using the Activity Class</span></span>

<span data-ttu-id="edabe-103">A maneira mais básica de criar uma atividade usando Windows Workflow Foundation (WF) no [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] é criar uma classe que herda de <xref:System.Activities.Activity> que cria a funcionalidade montando atividades personalizadas ou atividades da [biblioteca de atividades interna](net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="edabe-103">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="edabe-104">Este tópico demonstra como criar uma atividade duas mensagens que grava no console.</span><span class="sxs-lookup"><span data-stu-id="edabe-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="edabe-105">Para criar uma atividade personalizado utilizando o designer de atividades</span><span class="sxs-lookup"><span data-stu-id="edabe-105">To create a custom Activity using the activity designer</span></span>

1. <span data-ttu-id="edabe-106">Abra o Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="edabe-106">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="edabe-107">Arquivo, Selecione Novo, Projeto.</span><span class="sxs-lookup"><span data-stu-id="edabe-107">Select File, New, Project.</span></span> <span data-ttu-id="edabe-108">Selecione **fluxo de trabalho 4,0** em **Visual C#** na janela **tipos de projeto** e selecione o nó **v2010** .</span><span class="sxs-lookup"><span data-stu-id="edabe-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="edabe-109">Selecione **biblioteca de atividades** na janela **modelos** .</span><span class="sxs-lookup"><span data-stu-id="edabe-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="edabe-110">Nomeie o novo projeto HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="edabe-110">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="edabe-111">Abra a nova atividade.</span><span class="sxs-lookup"><span data-stu-id="edabe-111">Open the new activity.</span></span>  <span data-ttu-id="edabe-112">Arraste uma atividade de <xref:System.Activities.Statements.Sequence> da caixa de ferramentas para a superfície de designer.</span><span class="sxs-lookup"><span data-stu-id="edabe-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>

4. <span data-ttu-id="edabe-113">Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> na atividade de <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="edabe-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="edabe-114">Insira `"Hello World"` (com aspas) no campo de **texto** .</span><span class="sxs-lookup"><span data-stu-id="edabe-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>

5. <span data-ttu-id="edabe-115">Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> de segundo na atividade de <xref:System.Activities.Statements.Sequence> , abaixo da primeira.</span><span class="sxs-lookup"><span data-stu-id="edabe-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="edabe-116">Insira `"Goodbye"` (com aspas) no campo de **texto** .</span><span class="sxs-lookup"><span data-stu-id="edabe-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
