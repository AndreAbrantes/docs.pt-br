---
title: Tipos de RPC-gRPC para desenvolvedores do WCF
description: Uma revisão dos tipos de chamada de procedimento remoto com suporte pelo WCF e seus equivalentes no gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 58f097bac61395e6810155e8ae9a6bbf2219ec5e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503434"
---
# <a name="types-of-rpc"></a><span data-ttu-id="1612b-103">Tipos de RPC</span><span class="sxs-lookup"><span data-stu-id="1612b-103">Types of RPC</span></span>

<span data-ttu-id="1612b-104">Como desenvolvedor de Windows Communication Foundation (WCF), você provavelmente está acostumado a lidar com os seguintes tipos de RPC (chamada de procedimento remoto):</span><span class="sxs-lookup"><span data-stu-id="1612b-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="1612b-105">Solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="1612b-105">Request/reply</span></span>
- <span data-ttu-id="1612b-106">Duplex</span><span class="sxs-lookup"><span data-stu-id="1612b-106">Duplex:</span></span>
  - <span data-ttu-id="1612b-107">Duplex unidirecional com sessão</span><span class="sxs-lookup"><span data-stu-id="1612b-107">One-way duplex with session</span></span>
  - <span data-ttu-id="1612b-108">Full duplex com sessão</span><span class="sxs-lookup"><span data-stu-id="1612b-108">Full duplex with session</span></span>
- <span data-ttu-id="1612b-109">Unidirecional</span><span class="sxs-lookup"><span data-stu-id="1612b-109">One-way</span></span>

<span data-ttu-id="1612b-110">É possível mapear esses tipos de RPC razoavelmente naturalmente para os conceitos de gRPC existentes.</span><span class="sxs-lookup"><span data-stu-id="1612b-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="1612b-111">Este capítulo examinará cada uma dessas áreas por vez.</span><span class="sxs-lookup"><span data-stu-id="1612b-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="1612b-112">O [capítulo 5](migrate-wcf-to-grpc.md) irá explorar exemplos semelhantes em maior profundidade.</span><span class="sxs-lookup"><span data-stu-id="1612b-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="1612b-113">WCF</span><span class="sxs-lookup"><span data-stu-id="1612b-113">WCF</span></span> | <span data-ttu-id="1612b-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="1612b-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="1612b-115">Solicitação/resposta regular</span><span class="sxs-lookup"><span data-stu-id="1612b-115">Regular request/reply</span></span> | <span data-ttu-id="1612b-116">Unário</span><span class="sxs-lookup"><span data-stu-id="1612b-116">Unary</span></span> |
| <span data-ttu-id="1612b-117">Serviço duplex com sessão usando uma interface de retorno de chamada do cliente</span><span class="sxs-lookup"><span data-stu-id="1612b-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="1612b-118">Transmissão de servidor</span><span class="sxs-lookup"><span data-stu-id="1612b-118">Server streaming</span></span> |
| <span data-ttu-id="1612b-119">Serviço full duplex com sessão</span><span class="sxs-lookup"><span data-stu-id="1612b-119">Full duplex service with session</span></span> | <span data-ttu-id="1612b-120">Streaming bidirecional</span><span class="sxs-lookup"><span data-stu-id="1612b-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="1612b-121">Operações unidirecionais</span><span class="sxs-lookup"><span data-stu-id="1612b-121">One-way operations</span></span> | <span data-ttu-id="1612b-122">Streaming de cliente</span><span class="sxs-lookup"><span data-stu-id="1612b-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="1612b-123">Solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="1612b-123">Request/reply</span></span>

<span data-ttu-id="1612b-124">Para métodos simples de solicitação/resposta que levam e retornam pequenas quantidades de dados, use o padrão gRPC mais simples, o RPC unário.</span><span class="sxs-lookup"><span data-stu-id="1612b-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

<span data-ttu-id="1612b-125">Como você pode ver, a implementação de um método de serviço RPC unário gRPC é semelhante à implementação de uma operação do WCF.</span><span class="sxs-lookup"><span data-stu-id="1612b-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="1612b-126">A diferença é que, com gRPC, você substitui um método de classe base em vez de implementar uma interface.</span><span class="sxs-lookup"><span data-stu-id="1612b-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="1612b-127">No servidor, os métodos de base gRPC sempre retornam <xref:System.Threading.Tasks.Task%601>, embora o cliente forneça métodos assíncronos e de bloqueio para chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="1612b-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="1612b-128">WCF duplex, uma maneira para o cliente</span><span class="sxs-lookup"><span data-stu-id="1612b-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="1612b-129">Os aplicativos WCF (com determinadas associações) podem criar uma conexão persistente entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="1612b-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="1612b-130">O servidor pode enviar dados de forma assíncrona para o cliente até que a conexão seja fechada, usando uma *interface de retorno de chamada* especificada na propriedade <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1612b-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="1612b-131">os serviços gRPCs fornecem funcionalidade semelhante com fluxos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1612b-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="1612b-132">Os fluxos não são mapeados *exatamente* para os serviços do WCF duplex em termos de implementação, mas você pode obter os mesmos resultados.</span><span class="sxs-lookup"><span data-stu-id="1612b-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="1612b-133">streaming de gRPC</span><span class="sxs-lookup"><span data-stu-id="1612b-133">gRPC streaming</span></span>

<span data-ttu-id="1612b-134">o gRPC dá suporte à criação de fluxos persistentes do cliente para o servidor e do servidor para o cliente.</span><span class="sxs-lookup"><span data-stu-id="1612b-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="1612b-135">Ambos os tipos de fluxo podem estar ativos simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="1612b-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="1612b-136">Essa capacidade é chamada de streaming bidirecional.</span><span class="sxs-lookup"><span data-stu-id="1612b-136">This ability is called bidirectional streaming.</span></span> 

<span data-ttu-id="1612b-137">Você pode usar fluxos para mensagens arbitrárias e assíncronas ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="1612b-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="1612b-138">Ou você pode usá-los para passar grandes conjuntos de altos que são muito grandes para gerar e enviar em uma única solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="1612b-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="1612b-139">O exemplo a seguir mostra um RPC de streaming de servidor.</span><span class="sxs-lookup"><span data-stu-id="1612b-139">The following example shows a server-streaming RPC.</span></span>

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

<span data-ttu-id="1612b-140">Esse fluxo de servidor pode ser consumido de um aplicativo cliente, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="1612b-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> <span data-ttu-id="1612b-141">As RPCs de streaming de servidor são úteis para serviços de estilo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="1612b-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="1612b-142">Eles também são úteis para o envio de conjuntos de grandes volumes quando seriam ineficientes ou impossíveis de criar todo o conjunto de linhas na memória.</span><span class="sxs-lookup"><span data-stu-id="1612b-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="1612b-143">No entanto, as respostas de streaming não são tão rápidas quanto enviar `repeated` campos em uma única mensagem.</span><span class="sxs-lookup"><span data-stu-id="1612b-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="1612b-144">Como regra, o streaming não deve ser usado para pequenos conjuntos de valores.</span><span class="sxs-lookup"><span data-stu-id="1612b-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="1612b-145">Diferenças do WCF</span><span class="sxs-lookup"><span data-stu-id="1612b-145">Differences from WCF</span></span>

<span data-ttu-id="1612b-146">Um serviço do WCF duplex usa uma interface de retorno de chamada do cliente que pode ter vários métodos.</span><span class="sxs-lookup"><span data-stu-id="1612b-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="1612b-147">Um serviço do gRPC Server-streaming só pode enviar mensagens por um único fluxo.</span><span class="sxs-lookup"><span data-stu-id="1612b-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="1612b-148">Se você precisar de vários métodos, use um tipo de mensagem com [qualquer campo ou um campo](protobuf-any-oneof.md) para enviar mensagens diferentes e escreva o código no cliente para tratá-los.</span><span class="sxs-lookup"><span data-stu-id="1612b-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="1612b-149">No WCF, a classe [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) com a sessão é mantida ativa até que a conexão seja fechada.</span><span class="sxs-lookup"><span data-stu-id="1612b-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="1612b-150">Vários métodos podem ser chamados dentro da sessão.</span><span class="sxs-lookup"><span data-stu-id="1612b-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="1612b-151">No gRPC, a `Task` que o método de implementação retorna não deve ser concluída até que a conexão seja fechada.</span><span class="sxs-lookup"><span data-stu-id="1612b-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="1612b-152">Operações unidirecionais do WCF e streaming de cliente gRPC</span><span class="sxs-lookup"><span data-stu-id="1612b-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="1612b-153">O WCF fornece operações unidirecionais (marcadas com `[OperationContract(IsOneWay = true)]`) que retornam uma confirmação específica de transporte.</span><span class="sxs-lookup"><span data-stu-id="1612b-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="1612b-154">os métodos de serviço gRPC sempre retornam uma resposta, mesmo se estiverem vazios.</span><span class="sxs-lookup"><span data-stu-id="1612b-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="1612b-155">O cliente deve sempre esperar essa resposta.</span><span class="sxs-lookup"><span data-stu-id="1612b-155">The client should always await that response.</span></span> <span data-ttu-id="1612b-156">Para o estilo "acionar e esquecer" de mensagens no gRPC, você pode criar um serviço de streaming de cliente.</span><span class="sxs-lookup"><span data-stu-id="1612b-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="1612b-157">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="1612b-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="1612b-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="1612b-158">ThingLogService.cs</span></span>

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a><span data-ttu-id="1612b-159">Exemplo de cliente ThingLog</span><span class="sxs-lookup"><span data-stu-id="1612b-159">ThingLog client example</span></span>

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

<span data-ttu-id="1612b-160">Você pode usar RPCs de streaming de cliente para mensagens de incêndio e esquecer, conforme mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1612b-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="1612b-161">Você também pode usá-los para enviar grandes conjuntos de volumes para o servidor.</span><span class="sxs-lookup"><span data-stu-id="1612b-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="1612b-162">O mesmo aviso sobre o desempenho se aplica: para conjuntos de valores menores, use `repeated` campos em mensagens regulares.</span><span class="sxs-lookup"><span data-stu-id="1612b-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="1612b-163">Serviços Full duplex do WCF</span><span class="sxs-lookup"><span data-stu-id="1612b-163">WCF full-duplex services</span></span>

<span data-ttu-id="1612b-164">A associação duplex do WCF dá suporte a várias operações unidirecionais na interface do serviço e na interface de retorno de chamada do cliente.</span><span class="sxs-lookup"><span data-stu-id="1612b-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="1612b-165">Esse suporte permite conversas contínuas entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="1612b-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="1612b-166">o gRPC dá suporte a algo semelhante com RPCs de streaming bidirecional, em que ambos os parâmetros são marcados com o modificador de `stream`.</span><span class="sxs-lookup"><span data-stu-id="1612b-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="1612b-167">chat. proto</span><span class="sxs-lookup"><span data-stu-id="1612b-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="1612b-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="1612b-168">ChatterService.cs</span></span>

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

<span data-ttu-id="1612b-169">No exemplo anterior, você pode ver que o método de implementação recebe um fluxo de solicitação (`IAsyncStreamReader<MessageRequest>`) e um fluxo de resposta (`IServerStreamWriter<MessageResponse>`).</span><span class="sxs-lookup"><span data-stu-id="1612b-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="1612b-170">O método pode ler e gravar mensagens até que a conexão seja fechada.</span><span class="sxs-lookup"><span data-stu-id="1612b-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="1612b-171">Cliente informativo</span><span class="sxs-lookup"><span data-stu-id="1612b-171">Chatter client</span></span>

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
><span data-ttu-id="1612b-172">[Anterior](wcf-bindings.md)
>[Próximo](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="1612b-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
