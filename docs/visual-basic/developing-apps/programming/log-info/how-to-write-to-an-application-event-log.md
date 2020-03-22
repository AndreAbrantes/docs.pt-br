---
title: Como gravar em um log de eventos do aplicativo
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352042"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="b8e0d-102">Como gravar em um log de eventos do aplicativo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8e0d-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="b8e0d-103">É possível usar os objetos `My.Application.Log` e `My.Log` para gravar informações sobre eventos que ocorrem em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="b8e0d-104">Este exemplo mostra como configurar um ouvinte de log de eventos. Assim, `My.Application.Log` grava informações de rastreamento no log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="b8e0d-105">Não é possível gravar no log de segurança.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-105">You cannot write to the Security log.</span></span> <span data-ttu-id="b8e0d-106">Para gravar no log do sistema, é necessário ser um membro do LocalSystem ou ter uma conta Administrador.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="b8e0d-107">Para exibir um log de eventos, é possível usar o **Gerenciador de Servidores** ou o **Visualizador de Eventos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="b8e0d-108">Para obter mais informações, consulte [Eventos ETW no .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="b8e0d-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="b8e0d-109">Para adicionar e configurar o ouvinte de log de eventos</span><span class="sxs-lookup"><span data-stu-id="b8e0d-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="b8e0d-110">Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="b8e0d-111">\- ou –</span><span class="sxs-lookup"><span data-stu-id="b8e0d-111">\- or -</span></span>

    <span data-ttu-id="b8e0d-112">Se não houver nenhum arquivo app.config,</span><span class="sxs-lookup"><span data-stu-id="b8e0d-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="b8e0d-113">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="b8e0d-114">Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="b8e0d-115">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-115">Click **Add**.</span></span>

2. <span data-ttu-id="b8e0d-116">Localize a seção `<listeners>` no arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="b8e0d-117">Localize a seção `<listeners>` na seção `<source>` com o atributo de nome "DefaultSource", aninhado na seção `<system.diagnostics>`, aninhada na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="b8e0d-118">Adicione esse elemento a essa seção `<listeners>`:</span><span class="sxs-lookup"><span data-stu-id="b8e0d-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="b8e0d-119">Localize a seção `<sharedListeners>`, na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="b8e0d-120">Adicione esse elemento a essa seção `<sharedListeners>`:</span><span class="sxs-lookup"><span data-stu-id="b8e0d-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="b8e0d-121">Substitua `APPLICATION_NAME` pelo nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b8e0d-122">Normalmente, um aplicativo grava somente erros no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="b8e0d-123">Para obter informações sobre filtragem de saída de log, consulte [Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="b8e0d-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="b8e0d-124">Para gravar informações de evento em um log de eventos</span><span class="sxs-lookup"><span data-stu-id="b8e0d-124">To write event information to the event log</span></span>

<span data-ttu-id="b8e0d-125">Use o método `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` para gravar informações no log de eventos.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="b8e0d-126">Para obter mais informações, consulte [Como: Gravar mensagens de log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) e [Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="b8e0d-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="b8e0d-127">Depois de configurar o ouvinte de log de eventos para um assembly, ele receberá todas as mensagens que `My.Application.Log` grava desse assembly.</span><span class="sxs-lookup"><span data-stu-id="b8e0d-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8e0d-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8e0d-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="b8e0d-129">Trabalhando com logs de aplicativo</span><span class="sxs-lookup"><span data-stu-id="b8e0d-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="b8e0d-130">Como registrar em log as exceções</span><span class="sxs-lookup"><span data-stu-id="b8e0d-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="b8e0d-131">Instruções passo a passo: determinando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="b8e0d-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
