---
title: Como usar componentes compatíveis com o padrão assíncrono baseado em evento
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 466c01dd44d217e466c520efba43a3a1d7bbf4c7
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="83e5f-102">Como usar componentes compatíveis com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="83e5f-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="83e5f-103">Muitos componentes oferecem a opção de executar seu trabalho de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="83e5f-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="83e5f-104">Os componentes <xref:System.Media.SoundPlayer> e <xref:System.Windows.Forms.PictureBox>, por exemplo, permite que você carregue sons e imagens "em segundo plano", enquanto o thread principal continua em execução sem interrupções.</span><span class="sxs-lookup"><span data-stu-id="83e5f-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="83e5f-105">Usar métodos assíncronos em uma classe que oferece suporte a [Visão geral do padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) pode ser tão simples quanto anexar um manipulador de eventos ao evento *MethodName***Completed** do componente, assim como você faria com qualquer outro evento.</span><span class="sxs-lookup"><span data-stu-id="83e5f-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's *MethodName***Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="83e5f-106">Quando você chama o método *MethodName***Async**, seu aplicativo continuará em execução sem interrupção até que o evento *MethodName***Completed** seja gerado.</span><span class="sxs-lookup"><span data-stu-id="83e5f-106">When you call the *MethodName***Async** method, your application will continue running without interruption until the *MethodName***Completed** event is raised.</span></span> <span data-ttu-id="83e5f-107">No manipulador de eventos, você pode examinar o parâmetro <xref:System.ComponentModel.AsyncCompletedEventArgs> para determinar se a operação assíncrona foi concluída com êxito ou se foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="83e5f-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="83e5f-108">Para saber mais sobre como usar manipuladores de evento, consulte [Visão geral dos manipuladores de evento](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="83e5f-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="83e5f-109">O procedimento a seguir mostra como usar o recurso de carregamento de imagem assíncrono de um controle <xref:System.Windows.Forms.PictureBox>.</span><span class="sxs-lookup"><span data-stu-id="83e5f-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="83e5f-110">Para ativar um controle PictureBox para carregar assincronamente uma imagem</span><span class="sxs-lookup"><span data-stu-id="83e5f-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1.  <span data-ttu-id="83e5f-111">Crie uma instância do componente <xref:System.Windows.Forms.PictureBox> no formulário.</span><span class="sxs-lookup"><span data-stu-id="83e5f-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2.  <span data-ttu-id="83e5f-112">Atribua um manipulador de eventos ao evento <xref:System.Windows.Forms.PictureBox.LoadCompleted>.</span><span class="sxs-lookup"><span data-stu-id="83e5f-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="83e5f-113">Verifique se ocorreu algum erro durante o download assíncrono aqui.</span><span class="sxs-lookup"><span data-stu-id="83e5f-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="83e5f-114">Verifique também o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="83e5f-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  <span data-ttu-id="83e5f-115">Adicione dois botões, chamados `loadButton` e `cancelLoadButton`, ao formulário.</span><span class="sxs-lookup"><span data-stu-id="83e5f-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="83e5f-116">Adicione <xref:System.Windows.Forms.Control.Click> manipuladores de eventos para iniciar e cancelar o download.</span><span class="sxs-lookup"><span data-stu-id="83e5f-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="83e5f-117">Execute seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="83e5f-117">Run your application.</span></span>  
  
     <span data-ttu-id="83e5f-118">Conforme o download da imagem prossegue, você pode mover o formulário livremente, minimizá-lo e maximizá-lo.</span><span class="sxs-lookup"><span data-stu-id="83e5f-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e5f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83e5f-119">See Also</span></span>  
 [<span data-ttu-id="83e5f-120">Como executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="83e5f-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="83e5f-121">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="83e5f-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="83e5f-122">NÃO ESTÁ NO BUILD: multithreading no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83e5f-122">NOT IN BUILD: Multithreading in Visual Basic</span></span>](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)
