---
title: "Determinando a duração da operação de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c96aa6752feca637f89ed309d1a5c87cea4a3a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="bba2c-102">Determinando a duração da operação de serviço</span><span class="sxs-lookup"><span data-stu-id="bba2c-102">Determining service operation duration</span></span>
<span data-ttu-id="bba2c-103">Se o rastreamento analítico é habilitado em um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplicativo, a duração da execução de uma operação de serviço pode facilmente ser determinada examinando o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="bba2c-103">If analytic tracing is enabled in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="bba2c-104">Este tópico demonstra como determinar a quantidade de tempo para concluir uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="bba2c-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="bba2c-105">Determinando a duração de execução de operação de serviço</span><span class="sxs-lookup"><span data-stu-id="bba2c-105">Determining service operation execution duration</span></span>  
  
1.  <span data-ttu-id="bba2c-106">Abra o Visualizador de eventos clicando **iniciar**, **executar**e digitando `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="bba2c-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="bba2c-107">Se você ainda não ativou o rastreamento analítico, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor de aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="bba2c-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="bba2c-108">Selecione **exibição**, **Mostrar analítica e Logs de depuração**.</span><span class="sxs-lookup"><span data-stu-id="bba2c-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="bba2c-109">Clique com botão direito **analítico** e selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="bba2c-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="bba2c-110">Deixe o Visualizador de eventos aberto para que os rastreamentos podem ser exibidos depois que a operação de serviço é executada.</span><span class="sxs-lookup"><span data-stu-id="bba2c-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3.  <span data-ttu-id="bba2c-111">Em seguida, abra um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplicativo que inclui um projeto de serviço e um projeto de cliente que interage com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="bba2c-111">Next, open a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="bba2c-112">Você pode criar um aplicativo desse tipo, seguindo o [Tutorial de Introdução](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="bba2c-112">You can create such an application by following the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  <span data-ttu-id="bba2c-113">Se você tiver o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] exemplos instalados, você pode abrir o [Introdução](../../../../../docs/framework/wcf/samples/getting-started-sample.md), que contém o projeto completo criado no tutorial.</span><span class="sxs-lookup"><span data-stu-id="bba2c-113">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="bba2c-114">Execute o aplicativo de servidor pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="bba2c-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="bba2c-115">Executar o aplicativo cliente clicando no **cliente** projeto e selecionando **depurar**, **iniciar uma nova instância**.</span><span class="sxs-lookup"><span data-stu-id="bba2c-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5.  <span data-ttu-id="bba2c-116">No Visualizador de eventos, atualize o log analítico e classifique os eventos por ID do evento.</span><span class="sxs-lookup"><span data-stu-id="bba2c-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="bba2c-117">Procure eventos com ID de evento [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span><span class="sxs-lookup"><span data-stu-id="bba2c-117">Look for events with Event ID [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span></span>  <span data-ttu-id="bba2c-118">Esses eventos mostram quais operações foram concluídas e qual foi a duração da operação.</span><span class="sxs-lookup"><span data-stu-id="bba2c-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="bba2c-119">O evento a seguir mostra a duração de uma operação de adição.</span><span class="sxs-lookup"><span data-stu-id="bba2c-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
