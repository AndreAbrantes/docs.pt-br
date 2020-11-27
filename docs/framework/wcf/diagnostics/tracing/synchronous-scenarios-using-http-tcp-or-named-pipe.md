---
title: Cenários síncronos utilizando HTTP, TCP ou pipe nomeado
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 906bceadf56d82570b41cfbb2c96e4b89d595d02
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274433"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="a3770-102">Cenários síncronos utilizando HTTP, TCP ou pipe nomeado</span><span class="sxs-lookup"><span data-stu-id="a3770-102">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>

<span data-ttu-id="a3770-103">Este tópico descreve as atividades e transferências para diferentes cenários de solicitação/resposta síncronas, com um cliente de thread único, usando HTTP, TCP ou pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="a3770-103">This topic describes the activities and transfers for different synchronous request/reply scenarios, with a single-threaded client, using HTTP, TCP or named pipe.</span></span> <span data-ttu-id="a3770-104">Consulte [cenários assíncronos usando http, TCP ou pipe nomeado](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) para obter mais informações sobre solicitações multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="a3770-104">See [Asynchronous Scenarios using HTTP, TCP, or Named-Pipe](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) for more information on multi-threaded requests.</span></span>  
  
## <a name="synchronous-requestreply-without-errors"></a><span data-ttu-id="a3770-105">Solicitação/resposta síncrona sem erros</span><span class="sxs-lookup"><span data-stu-id="a3770-105">Synchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="a3770-106">Esta seção descreve as atividades e transferências para um cenário de solicitação/resposta síncrona válido, com um cliente de thread único.</span><span class="sxs-lookup"><span data-stu-id="a3770-106">This section describes the activities and transfers for a valid synchronous request/reply scenario, with single-threaded client.</span></span>  
  
### <a name="client"></a><span data-ttu-id="a3770-107">Cliente</span><span class="sxs-lookup"><span data-stu-id="a3770-107">Client</span></span>  
  
#### <a name="establishing-communication-with-service-endpoint"></a><span data-ttu-id="a3770-108">Estabelecendo comunicação com o ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a3770-108">Establishing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="a3770-109">Um cliente é construído e aberto.</span><span class="sxs-lookup"><span data-stu-id="a3770-109">A client is constructed and opened.</span></span> <span data-ttu-id="a3770-110">Para cada uma dessas etapas, a atividade de ambiente (A) é transferida para uma atividade "cliente de construção" (B) e "Open Client" (C), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a3770-110">For each of these steps, the ambient activity (A) is transferred to a "Construct Client" (B) and "Open Client" (C) activity respectively.</span></span> <span data-ttu-id="a3770-111">Para cada atividade sendo transferida para o, a atividade de ambiente é suspensa até que haja uma transferência de volta, ou seja, até que o código de ServiceModel seja executado.</span><span class="sxs-lookup"><span data-stu-id="a3770-111">For each activity being transferred to, the ambient activity is suspended until there is a transfer back, that is, until ServiceModel code is executed.</span></span>  
  
#### <a name="making-a-request-to-service-endpoint"></a><span data-ttu-id="a3770-112">Fazendo uma solicitação para o ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a3770-112">Making a Request to Service Endpoint</span></span>  

 <span data-ttu-id="a3770-113">A atividade ambiente é transferida para uma atividade "processAction" (D).</span><span class="sxs-lookup"><span data-stu-id="a3770-113">The ambient activity is transferred to a "ProcessAction" (D) activity.</span></span> <span data-ttu-id="a3770-114">Nessa atividade, uma mensagem de solicitação é enviada e uma mensagem de resposta é recebida.</span><span class="sxs-lookup"><span data-stu-id="a3770-114">Within this activity, a request message is sent, and a response message is received.</span></span> <span data-ttu-id="a3770-115">A atividade termina quando o controle retorna ao código do usuário.</span><span class="sxs-lookup"><span data-stu-id="a3770-115">The activity ends when control returns to user code.</span></span> <span data-ttu-id="a3770-116">Como essa é uma solicitação síncrona, a atividade de ambiente suspende até que o controle seja retornado.</span><span class="sxs-lookup"><span data-stu-id="a3770-116">Because this is a synchronous request, the ambient activity suspends until control returns.</span></span>  
  
#### <a name="closing-communication-with-service-endpoint"></a><span data-ttu-id="a3770-117">Fechando a comunicação com o ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a3770-117">Closing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="a3770-118">A atividade de fechamento do cliente (I) é criada a partir da atividade ambiente.</span><span class="sxs-lookup"><span data-stu-id="a3770-118">The client's close activity (I) is created from the ambient activity.</span></span> <span data-ttu-id="a3770-119">Isso é idêntico ao novo e aberto.</span><span class="sxs-lookup"><span data-stu-id="a3770-119">This is identical to new and open.</span></span>  
  
### <a name="server"></a><span data-ttu-id="a3770-120">Servidor</span><span class="sxs-lookup"><span data-stu-id="a3770-120">Server</span></span>  
  
#### <a name="setting-up-a-service-host"></a><span data-ttu-id="a3770-121">Configurando um host de serviço</span><span class="sxs-lookup"><span data-stu-id="a3770-121">Setting up a Service Host</span></span>  

 <span data-ttu-id="a3770-122">As atividades novas e abertas do ServiceHost (N e O) são criadas a partir da atividade de ambiente (M).</span><span class="sxs-lookup"><span data-stu-id="a3770-122">The ServiceHost’s new and open activities (N and O) are created from the ambient activity (M).</span></span>  
  
 <span data-ttu-id="a3770-123">Uma atividade de ouvinte (P) é criada a partir da abertura de um ServiceHost para cada ouvinte.</span><span class="sxs-lookup"><span data-stu-id="a3770-123">A listener activity (P) is created from opening a ServiceHost for each listener.</span></span> <span data-ttu-id="a3770-124">A atividade do ouvinte aguarda para receber e processar dados.</span><span class="sxs-lookup"><span data-stu-id="a3770-124">The listener activity waits to receive and process data.</span></span>  
  
#### <a name="receiving-data-on-the-wire"></a><span data-ttu-id="a3770-125">Recebendo dados na conexão</span><span class="sxs-lookup"><span data-stu-id="a3770-125">Receiving Data on the Wire</span></span>  

 <span data-ttu-id="a3770-126">Quando os dados chegam na transmissão, uma atividade "ReceiveBytes" será criada se ainda não existir (Q) para processar os dados recebidos.</span><span class="sxs-lookup"><span data-stu-id="a3770-126">When data arrives on the wire, a "ReceiveBytes" activity is created if it does not already exist (Q) to process the received data.</span></span> <span data-ttu-id="a3770-127">Essa atividade pode ser reutilizada para várias mensagens em uma conexão ou fila.</span><span class="sxs-lookup"><span data-stu-id="a3770-127">This activity can be reused for multiple messages within a connection or queue.</span></span>  
  
 <span data-ttu-id="a3770-128">A atividade ReceiveBytes inicia uma atividade de ProcessMessage (R) se tiver dados suficientes para formar uma mensagem de ação SOAP.</span><span class="sxs-lookup"><span data-stu-id="a3770-128">The ReceiveBytes activity launches a ProcessMessage activity (R) if it has enough data to form a SOAP action message.</span></span>  
  
 <span data-ttu-id="a3770-129">Na atividade de R, os cabeçalhos de mensagem são processados e o cabeçalho ActivityId é verificado.</span><span class="sxs-lookup"><span data-stu-id="a3770-129">In activity R, the message headers are processed, and the activityID header is verified.</span></span> <span data-ttu-id="a3770-130">Se esse cabeçalho estiver presente, a ID da atividade será definida como a atividade processAction; caso contrário, uma nova ID será criada.</span><span class="sxs-lookup"><span data-stu-id="a3770-130">If this header is present, the activity ID is set to the ProcessAction activity; otherwise, a new ID is created.</span></span>  
  
 <span data-ttu-id="a3770-131">As atividades processAction são criadas e sendo transferidas para o, quando a chamada é processada.</span><span class="sxs-lookup"><span data-stu-id="a3770-131">ProcessAction activity (S) is created and being transferred to, when the call is processed.</span></span> <span data-ttu-id="a3770-132">Essa atividade termina quando todo o processamento relacionado à mensagem de entrada é concluído, incluindo a execução do código do usuário (T) e o envio da mensagem de resposta, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="a3770-132">This activity ends when all processing related to the incoming message is completed, including executing user code (T) and sending the response message if applicable.</span></span>  
  
#### <a name="closing-a-service-host"></a><span data-ttu-id="a3770-133">Fechando um host de serviço</span><span class="sxs-lookup"><span data-stu-id="a3770-133">Closing a Service Host</span></span>  

 <span data-ttu-id="a3770-134">A atividade de fechamento do ServiceHost (Z) é criada a partir da atividade de ambiente.</span><span class="sxs-lookup"><span data-stu-id="a3770-134">The ServiceHost’s close activity (Z) is created from the ambient activity.</span></span>  
  
 ![Diagrama mostrando cenários síncronos: HTTP, TCP ou pipes nomeados.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 <span data-ttu-id="a3770-136">No \<A: name> , `A` é um símbolo de atalho que descreve a atividade no texto anterior e na tabela 3.</span><span class="sxs-lookup"><span data-stu-id="a3770-136">In \<A: name>, `A` is a shortcut symbol that describes the activity in the previous text and in table 3.</span></span> <span data-ttu-id="a3770-137">`Name` é um nome abreviado da atividade.</span><span class="sxs-lookup"><span data-stu-id="a3770-137">`Name` is a shortened name of the activity.</span></span>  
  
 <span data-ttu-id="a3770-138">Se `propagateActivity` = `true` , ação de processo no cliente e no serviço tiverem a mesma ID de atividade.</span><span class="sxs-lookup"><span data-stu-id="a3770-138">If `propagateActivity`=`true`, Process Action on both the client and service have the same activity ID.</span></span>  
  
## <a name="synchronous-requestreply-with-errors"></a><span data-ttu-id="a3770-139">Solicitação/resposta síncrona com erros</span><span class="sxs-lookup"><span data-stu-id="a3770-139">Synchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="a3770-140">A única diferença com o cenário anterior é que uma mensagem de falha SOAP é retornada como uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="a3770-140">The only difference with the previous scenario is that a SOAP fault message is returned as a response message.</span></span> <span data-ttu-id="a3770-141">Se `propagateActivity` = `true` , a ID da atividade da mensagem de solicitação será adicionada à mensagem de falha SOAP.</span><span class="sxs-lookup"><span data-stu-id="a3770-141">If `propagateActivity`=`true`, the activity ID of the request message is added to the SOAP fault message.</span></span>  
  
## <a name="synchronous-one-way-without-errors"></a><span data-ttu-id="a3770-142">One-Way síncrono sem erros</span><span class="sxs-lookup"><span data-stu-id="a3770-142">Synchronous One-Way without Errors</span></span>  

 <span data-ttu-id="a3770-143">A única diferença no primeiro cenário é que nenhuma mensagem é retornada ao servidor.</span><span class="sxs-lookup"><span data-stu-id="a3770-143">The only difference with the first scenario is that no message is returned to the server.</span></span> <span data-ttu-id="a3770-144">Para protocolos baseados em HTTP, um status (válido ou erro) ainda é retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="a3770-144">For HTTP-based protocols, a status (valid or error) is still returned to the client.</span></span> <span data-ttu-id="a3770-145">Isso ocorre porque HTTP é o único protocolo com uma semântica de solicitação-resposta que faz parte da pilha de protocolo do WCF.</span><span class="sxs-lookup"><span data-stu-id="a3770-145">This is because HTTP is the only protocol with a request-response semantics that is part of the WCF protocol stack.</span></span> <span data-ttu-id="a3770-146">Como o processamento TCP está oculto do WCF, nenhuma confirmação é enviada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="a3770-146">Because TCP processing is hidden from WCF, no acknowledgement is sent to the client.</span></span>  
  
## <a name="synchronous-one-way-with-errors"></a><span data-ttu-id="a3770-147">One-Way síncronos com erros</span><span class="sxs-lookup"><span data-stu-id="a3770-147">Synchronous One-Way with Errors</span></span>  

 <span data-ttu-id="a3770-148">Se ocorrer um erro durante o processamento da mensagem (p ou posterior), nenhuma notificação será retornada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="a3770-148">If an error occurs while processing the message (Q or beyond), no notification is returned to the client.</span></span> <span data-ttu-id="a3770-149">Isso é idêntico ao cenário "One-Way síncrono sem erros".</span><span class="sxs-lookup"><span data-stu-id="a3770-149">This is identical to the "Synchronous One-Way without Errors" scenario.</span></span> <span data-ttu-id="a3770-150">Você não deve usar um cenário de One-Way se quiser receber uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="a3770-150">You should not use a One-Way scenario if you want to receive an error message.</span></span>  
  
## <a name="duplex"></a><span data-ttu-id="a3770-151">Duplex</span><span class="sxs-lookup"><span data-stu-id="a3770-151">Duplex</span></span>  

 <span data-ttu-id="a3770-152">A diferença com os cenários anteriores é que o cliente atua como um serviço, no qual ele cria as atividades ReceiveBytes e ProcessMessage, semelhante aos cenários assíncronos.</span><span class="sxs-lookup"><span data-stu-id="a3770-152">The difference with the previous scenarios is that the client acts as a service, in which it creates the ReceiveBytes and ProcessMessage activities, similar to the Asynchronous scenarios.</span></span>
