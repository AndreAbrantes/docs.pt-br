---
title: Assinando eventos
description: Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Entenda os detalhes de publicação e assinatura de eventos de integração.
ms.date: 01/30/2020
ms.openlocfilehash: 426dcebe175e9db9a02bcdb2f21ad039154a7bda
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888209"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="71e3e-103">Assinando eventos</span><span class="sxs-lookup"><span data-stu-id="71e3e-103">Subscribing to events</span></span>

<span data-ttu-id="71e3e-104">A primeira etapa para usar o barramento de eventos é fazer com que os microsserviços assinem os eventos que eles desejam receber.</span><span class="sxs-lookup"><span data-stu-id="71e3e-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="71e3e-105">Isso deve ser feito nos microsserviços destinatários.</span><span class="sxs-lookup"><span data-stu-id="71e3e-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="71e3e-106">O código simples a seguir mostra o que cada destinatário de microsserviço precisa implementar ao iniciar o serviço (ou seja, a classe `Startup`) para assinar os eventos que precisa.</span><span class="sxs-lookup"><span data-stu-id="71e3e-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="71e3e-107">Nesse caso, o microsserviço `basket-api` precisa assinar as mensagens `ProductPriceChangedIntegrationEvent` e `OrderStartedIntegrationEvent`.</span><span class="sxs-lookup"><span data-stu-id="71e3e-107">In this case, the `basket-api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="71e3e-108">Por exemplo, ao assinar `ProductPriceChangedIntegrationEvent` o evento, isso torna o microserviço da cesta ciente de qualquer alteração no preço do produto e permite que ele avise o usuário sobre a alteração se esse produto estiver na cesta do usuário.</span><span class="sxs-lookup"><span data-stu-id="71e3e-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user's basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="71e3e-109">Depois que esse código for executado, o microsserviço assinante escutará por meio de canais RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="71e3e-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="71e3e-110">Quando qualquer mensagem do tipo ProductPriceChangedIntegrationEvent chegar, o código invocará o manipulador de eventos, que será passado a ele e processará o evento.</span><span class="sxs-lookup"><span data-stu-id="71e3e-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="71e3e-111">Publicando eventos por meio do barramento de eventos</span><span class="sxs-lookup"><span data-stu-id="71e3e-111">Publishing events through the event bus</span></span>

<span data-ttu-id="71e3e-112">Por fim, o remetente da mensagem (microsserviço de origem) publica os eventos de integração com um código semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="71e3e-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="71e3e-113">(Este é um exemplo simplificado que não leva em conta a atômicaidade.) Você implementaria código semelhante sempre que um evento deve ser propagado em vários microsserviços, geralmente logo após o cometimento de dados ou transações do microserviço de origem.</span><span class="sxs-lookup"><span data-stu-id="71e3e-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="71e3e-114">Primeiro, o objeto de implementação do barramento de eventos (baseado no RabbitMQ ou em um barramento de serviço) seria injetado no construtor do controlador, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="71e3e-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

<span data-ttu-id="71e3e-115">Em seguida, você usá-lo a partir dos métodos do seu controlador, como no método UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="71e3e-115">Then you use it from your controller's methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("items")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

<span data-ttu-id="71e3e-116">Nesse caso, como o microsserviço de origem é um microsserviço CRUD simples, o código é colocado diretamente em um controlador de API Web.</span><span class="sxs-lookup"><span data-stu-id="71e3e-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="71e3e-117">Em microsserviços mais avançados, como ao usar abordagens de CQRS, ele pode ser implementado na classe `CommandHandler`, dentro do método `Handle()`.</span><span class="sxs-lookup"><span data-stu-id="71e3e-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="71e3e-118">Criando atomicidade e resiliência ao publicar no barramento de eventos</span><span class="sxs-lookup"><span data-stu-id="71e3e-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="71e3e-119">Ao publicar eventos de integração por meio de um sistema de mensagens distribuído como o barramento de eventos, surge o problema da atualização do banco de dados original e da publicação de um evento de forma atômica (ou seja, ambas as operações são concluídas ou nenhuma delas).</span><span class="sxs-lookup"><span data-stu-id="71e3e-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="71e3e-120">Por exemplo, no exemplo simplificado mostrado anteriormente, o código confirma os dados no banco de dados quando o preço do produto é alterado e, em seguida, publica uma mensagem ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="71e3e-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="71e3e-121">Inicialmente, pode parecer essencial que essas duas operações sejam executada atomicamente.</span><span class="sxs-lookup"><span data-stu-id="71e3e-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="71e3e-122">No entanto, se você estivesse usando uma transação distribuída que envolvesse o banco de dados e o agente de mensagens, assim como faria em sistemas mais antigos, como o [MSMQ (Enfileiramento de Mensagens da Microsoft)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), isso não seria recomendado pelos motivos descritos pelo [Teorema CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="71e3e-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="71e3e-123">Basicamente, você usa microsserviços para criar sistemas escalonáveis e altamente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="71e3e-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="71e3e-124">Simplificando um pouco, o teorema do CAP diz que você não pode construir um banco de dados (distribuído) (ou um microserviço que possua seu modelo) que esteja continuamente disponível, fortemente consistente *e* tolerante a qualquer partição.</span><span class="sxs-lookup"><span data-stu-id="71e3e-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that's continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="71e3e-125">Você deve escolher duas dessas três propriedades.</span><span class="sxs-lookup"><span data-stu-id="71e3e-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="71e3e-126">Em arquiteturas baseadas em microsserviços, você deve escolher disponibilidade e tolerância, e você deve desenfatizar uma forte consistência.</span><span class="sxs-lookup"><span data-stu-id="71e3e-126">In microservices-based architectures, you should choose availability and tolerance, and you should de-emphasize strong consistency.</span></span> <span data-ttu-id="71e3e-127">Portanto, na maioria dos aplicativos modernos baseados em microsserviços, geralmente não é interessante usar transações distribuídas no sistema de mensagens, como ao implementar [transações distribuídas](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) com base no DTC (Coordenador de Transações Distribuídas) do Windows com o [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="71e3e-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="71e3e-128">Vamos voltar à questão inicial e ao seu exemplo.</span><span class="sxs-lookup"><span data-stu-id="71e3e-128">Let's go back to the initial issue and its example.</span></span> <span data-ttu-id="71e3e-129">Se o serviço falhar após a atualização do banco de dados `_context.SaveChangesAsync()`(neste caso, logo após a linha de código com ), mas antes do evento de integração ser publicado, o sistema global pode se tornar inconsistente.</span><span class="sxs-lookup"><span data-stu-id="71e3e-129">If the service crashes after the database is updated (in this case, right after the line of code with `_context.SaveChangesAsync()`), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="71e3e-130">Isso pode ser crítico, dependendo da operação de negócios específica com a qual você está lidando.</span><span class="sxs-lookup"><span data-stu-id="71e3e-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="71e3e-131">Como mencionado anteriormente na seção de arquitetura, você pode ter várias abordagens para lidar com esse problema:</span><span class="sxs-lookup"><span data-stu-id="71e3e-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="71e3e-132">Usando o padrão [Event Sourcing](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing) completo.</span><span class="sxs-lookup"><span data-stu-id="71e3e-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="71e3e-133">Usando [mineração do log de transações](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="71e3e-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="71e3e-134">Usando o [padrão Outbox](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span><span class="sxs-lookup"><span data-stu-id="71e3e-134">Using the [Outbox pattern](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span></span> <span data-ttu-id="71e3e-135">Essa é uma tabela transacional para armazenar os eventos de integração (estendendo a transação local).</span><span class="sxs-lookup"><span data-stu-id="71e3e-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="71e3e-136">Neste cenário, o uso do padrão ES (Event Sourcing) completo é uma das melhores abordagens, se não for *a* melhor.</span><span class="sxs-lookup"><span data-stu-id="71e3e-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="71e3e-137">No entanto, em muitos cenários de aplicativo, pode ser impossível implementar um sistema completo de ES.</span><span class="sxs-lookup"><span data-stu-id="71e3e-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="71e3e-138">O ES significa o armazenamento somente dos eventos de domínio em seu banco de dados transacional, em vez de armazenar dados do estado atual.</span><span class="sxs-lookup"><span data-stu-id="71e3e-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="71e3e-139">Armazenar apenas os eventos de domínio pode ter grandes benefícios, como ter o histórico do sistema disponível e poder determinar o estado do sistema em qualquer momento no passado.</span><span class="sxs-lookup"><span data-stu-id="71e3e-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="71e3e-140">No entanto, implementar um sistema de ES completo exige que você refaça a arquitetura da maior parte do seu sistema e também pode apresentar muitas outras complexidades e requisitos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="71e3e-141">Por exemplo, vai ser interessante usar um banco de dados criado especificamente para fornecimento de eventos, como o [Event Store](https://eventstore.org/), ou um banco de dados orientado a documentos, como Azure Cosmos DB, MongoDB, Cassandra, CouchDB ou RavenDB.</span><span class="sxs-lookup"><span data-stu-id="71e3e-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="71e3e-142">O ES é uma ótima abordagem para esse problema, mas não é a solução mais fácil, a menos que você já esteja familiarizado com fornecimento de eventos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="71e3e-143">A opção de usar a mineração de log de transações inicialmente parece transparente.</span><span class="sxs-lookup"><span data-stu-id="71e3e-143">The option to use transaction log mining initially looks transparent.</span></span> <span data-ttu-id="71e3e-144">No entanto, para usar essa abordagem, o microsserviço deverá ser acoplado ao seu log de transações do RDBMS, como o log de transações do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="71e3e-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="71e3e-145">Isso provavelmente não é interessante.</span><span class="sxs-lookup"><span data-stu-id="71e3e-145">This is probably not desirable.</span></span> <span data-ttu-id="71e3e-146">Outra desvantagem é que as atualizações de baixo nível registradas no log de transações podem não estar no mesmo nível que seus eventos de integração de alto nível.</span><span class="sxs-lookup"><span data-stu-id="71e3e-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="71e3e-147">Nesse caso, o processo de engenharia reversa dessas operações do log de transações poderá ser difícil.</span><span class="sxs-lookup"><span data-stu-id="71e3e-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="71e3e-148">Uma abordagem equilibrada é uma combinação de uma tabela de banco de dados transacional e um padrão de ES simplificado.</span><span class="sxs-lookup"><span data-stu-id="71e3e-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="71e3e-149">Você pode usar um estado como "pronto para publicar o evento", que você define no evento original quando o compromete na tabela de eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="71e3e-149">You can use a state such as "ready to publish the event," which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="71e3e-150">Em seguida, você tenta publicar o evento no barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="71e3e-151">Se a ação de publicação-evento for bem sucedida, você inicia outra transação no serviço de origem e move o estado de "pronto para publicar o evento" para "evento já publicado".</span><span class="sxs-lookup"><span data-stu-id="71e3e-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from "ready to publish the event" to "event already published."</span></span>

<span data-ttu-id="71e3e-152">Se a ação de evento de publicação no ônibus de caso falhar, os dados ainda não serão inconsistentes dentro do microserviço de origem — ele ainda está marcado como "pronto para publicar o evento", e com relação ao resto dos serviços, ele eventualmente será consistente.</span><span class="sxs-lookup"><span data-stu-id="71e3e-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as "ready to publish the event," and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="71e3e-153">Você sempre fazer com que trabalhos em segundo plano verifiquem o estado das transações ou dos eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="71e3e-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="71e3e-154">Se o trabalho encontrar um evento no estado "pronto para publicar o evento", ele pode tentar republicar esse evento para o ônibus do evento.</span><span class="sxs-lookup"><span data-stu-id="71e3e-154">If the job finds an event in the "ready to publish the event" state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="71e3e-155">Observe que, com essa abordagem, você estará persistindo apenas os eventos de integração de cada microsserviço de origem e somente os eventos que você deseja comunicar para outros microsserviços ou sistemas externos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="71e3e-156">Por outro lado, em um sistema completo de ES, você também armazena todos os eventos de domínio.</span><span class="sxs-lookup"><span data-stu-id="71e3e-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="71e3e-157">Portanto, essa abordagem equilibrada é um sistema de ES simplificado.</span><span class="sxs-lookup"><span data-stu-id="71e3e-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="71e3e-158">Você precisa de uma lista de eventos de integração com seu estado atual ("pronto para publicar" versus "publicado").</span><span class="sxs-lookup"><span data-stu-id="71e3e-158">You need a list of integration events with their current state ("ready to publish" versus "published").</span></span> <span data-ttu-id="71e3e-159">Mas você só precisa implementar esses estados para os eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="71e3e-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="71e3e-160">E, nessa abordagem, não é necessário armazenar todos os dados de domínio como eventos no banco de dados transacional, como você faria em um sistema completo de ES.</span><span class="sxs-lookup"><span data-stu-id="71e3e-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="71e3e-161">Se já está usando um banco de dados relacional, você pode usar uma tabela transacional para armazenar eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="71e3e-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="71e3e-162">Para obter a atomicidade em seu aplicativo, você usa um processo de duas etapas com base nas transações locais.</span><span class="sxs-lookup"><span data-stu-id="71e3e-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="71e3e-163">Basicamente, você tem uma tabela IntegrationEvent no mesmo banco de dados em que estão as entidades de domínio.</span><span class="sxs-lookup"><span data-stu-id="71e3e-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="71e3e-164">Essa tabela funciona como um seguro para a obtenção de atomicidade, para que você inclua eventos de integração persistidos nas mesmas transações que estão confirmando seus dados de domínio.</span><span class="sxs-lookup"><span data-stu-id="71e3e-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="71e3e-165">Passo a passo, o processo é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="71e3e-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="71e3e-166">O aplicativo inicia uma transação de banco de dados local.</span><span class="sxs-lookup"><span data-stu-id="71e3e-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="71e3e-167">Em seguida, ele atualiza o estado das suas entidades de domínio e insere um evento na tabela de eventos de integração.</span><span class="sxs-lookup"><span data-stu-id="71e3e-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="71e3e-168">Por fim, ele confirma a transação, de modo que você obtenha a atomicidade desejada e</span><span class="sxs-lookup"><span data-stu-id="71e3e-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="71e3e-169">Você publica o evento de alguma forma (a seguir).</span><span class="sxs-lookup"><span data-stu-id="71e3e-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="71e3e-170">Ao implementar as etapas de publicação dos eventos, você tem estas opções:</span><span class="sxs-lookup"><span data-stu-id="71e3e-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="71e3e-171">Publicar o evento de integração logo após a confirmação da transação e usar outra transação local para marcar os eventos na tabela como sendo publicados.</span><span class="sxs-lookup"><span data-stu-id="71e3e-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="71e3e-172">Em seguida, usar a tabela apenas como um artefato para controlar os eventos de integração, em caso de problemas com os microsserviços remotos, e executar ações compensatórias com base nos eventos de integração armazenados.</span><span class="sxs-lookup"><span data-stu-id="71e3e-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="71e3e-173">Usar a tabela como um tipo de fila.</span><span class="sxs-lookup"><span data-stu-id="71e3e-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="71e3e-174">Um thread ou processo do aplicativo separado consulta a tabela de eventos de integração, publica os eventos no barramento de eventos e, em seguida, usa uma transação local para marcar os eventos como publicados.</span><span class="sxs-lookup"><span data-stu-id="71e3e-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="71e3e-175">A Figura 6-22 mostra a arquitetura da primeira dessas abordagens.</span><span class="sxs-lookup"><span data-stu-id="71e3e-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Diagrama da atônidade ao publicar sem um microserviço do trabalhador.](./media/subscribe-events/atomicity-publish-event-bus.png)

<span data-ttu-id="71e3e-177">**Figura 6-22**.</span><span class="sxs-lookup"><span data-stu-id="71e3e-177">**Figure 6-22**.</span></span> <span data-ttu-id="71e3e-178">Atomicidade ao publicar eventos no barramento de eventos</span><span class="sxs-lookup"><span data-stu-id="71e3e-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="71e3e-179">A abordagem ilustrada na Figura 6-22 não tem um microsserviço de trabalho adicional, que é responsável por verificar e confirmar o êxito dos eventos de integração publicados.</span><span class="sxs-lookup"><span data-stu-id="71e3e-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="71e3e-180">Em caso de falha, esse microsserviço de trabalho verificador adicional pode ler os eventos na tabela e publicá-los novamente, ou seja, repetir a etapa 2.</span><span class="sxs-lookup"><span data-stu-id="71e3e-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="71e3e-181">Em relação à segunda abordagem: você usa a tabela EventLog como uma fila e sempre usa um microsserviço de trabalho para publicar as mensagens.</span><span class="sxs-lookup"><span data-stu-id="71e3e-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="71e3e-182">Nesse caso, o processo é como o mostrado na Figura 6-23.</span><span class="sxs-lookup"><span data-stu-id="71e3e-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="71e3e-183">Ela mostra um microsserviço adicional, e a tabela é a única fonte durante a publicação de eventos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Diagrama da atônidade ao publicar com um microserviço do trabalhador.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

<span data-ttu-id="71e3e-185">**Figura 6-23**.</span><span class="sxs-lookup"><span data-stu-id="71e3e-185">**Figure 6-23**.</span></span> <span data-ttu-id="71e3e-186">Atomicidade ao publicar eventos no barramento de eventos com um microsserviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="71e3e-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="71e3e-187">Para simplificar, o exemplo eShopOnContainers usa a primeira abordagem (sem processos adicionais nem microsserviços verificadores) e o barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="71e3e-188">No entanto, a amostra eShopOnContainers não está lidando com todos os casos de falha possíveis.</span><span class="sxs-lookup"><span data-stu-id="71e3e-188">However, the eShopOnContainers sample is not handling all possible failure cases.</span></span> <span data-ttu-id="71e3e-189">Em um aplicativo real implantado na nuvem, você deve aceitar o fato de que os problemas surgirão eventualmente, e você deverá implementar essa lógica de verificação e reenvio.</span><span class="sxs-lookup"><span data-stu-id="71e3e-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="71e3e-190">O uso da tabela como uma fila pode ser mais eficiente do que a primeira abordagem se você tem essa tabela como uma única fonte de eventos ao publicá-los (com o trabalho) por meio do barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="71e3e-191">Implementando atomicidade ao publicar eventos de integração por meio do barramento de eventos</span><span class="sxs-lookup"><span data-stu-id="71e3e-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="71e3e-192">O código a seguir mostra como criar uma única transação que envolva vários objetos DbContext: um contexto relacionados aos dados originais que estão sendo atualizados e o segundo contexto relacionado à tabela IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="71e3e-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="71e3e-193">A transação no código de exemplo abaixo não será resiliente se as conexões com o banco de dados tiverem algum problema no momento em que o código estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="71e3e-193">The transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="71e3e-194">Isso pode ocorrer em sistemas baseados em nuvem, como o BD SQL do Azure, que pode mover bancos de dados entre servidores.</span><span class="sxs-lookup"><span data-stu-id="71e3e-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="71e3e-195">Para implementar transações resilientes em vários contextos, consulte a seção [Implementando conexões de SQL do Entity Framework Core resilientes](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) mais adiante, neste guia.</span><span class="sxs-lookup"><span data-stu-id="71e3e-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="71e3e-196">Para maior clareza, o exemplo a seguir mostra todo o processo em um único segmento de código.</span><span class="sxs-lookup"><span data-stu-id="71e3e-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="71e3e-197">No entanto, a implementação do eShopOnContainers é refatorada e divide essa lógica em várias classes para que seja mais fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="71e3e-197">However, the eShopOnContainers implementation is refactored and splits this logic into multiple classes so it's easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate)
{
  var catalogItem =
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id ==
                                                               productToUpdate.Id);
  if (catalogItem == null) return NotFound();

  bool raiseProductPriceChangedEvent = false;
  IntegrationEvent priceChangedEvent = null;

  if (catalogItem.Price != productToUpdate.Price)
          raiseProductPriceChangedEvent = true;

  if (raiseProductPriceChangedEvent) // Create event if price has changed
  {
      var oldPrice = catalogItem.Price;
      priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
                                                                  productToUpdate.Price,
                                                                  oldPrice);
  }
  // Update current product
  catalogItem = productToUpdate;

  // Just save the updated product if the Product's Price hasn't changed.
  if (!raiseProductPriceChangedEvent)
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
        // Achieving atomicity between original DB and the IntegrationEventLog
        // with a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
           _catalogContext.CatalogItems.Update(catalogItem);
           await _catalogContext.SaveChangesAsync();

           // Save to EventLog only if product price changed
           if(raiseProductPriceChangedEvent)
               await _integrationEventLogService.SaveEventAsync(priceChangedEvent);

           transaction.Commit();
        }

      // Publish the integration event through the event bus
      _eventBus.Publish(priceChangedEvent);

      _integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

<span data-ttu-id="71e3e-198">Depois que o evento de integração ProductPriceChangedIntegrationEvent é criado, a transação que armazena a operação de domínio original (atualizar o item de catálogo) também inclui a persistência do evento na tabela EventLog.</span><span class="sxs-lookup"><span data-stu-id="71e3e-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="71e3e-199">Isso faz com que ele se torne uma única transação, e sempre será possível verificar se as mensagens de evento foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="71e3e-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="71e3e-200">A tabela do log de eventos é atualizada atomicamente com a operação do banco de dados original, usando uma transação local no mesmo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="71e3e-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="71e3e-201">Se uma das operações falha, uma exceção é gerada e a transação reverte qualquer operação concluída, mantendo a consistência entre as operações de domínio e as mensagens de evento salvas na tabela.</span><span class="sxs-lookup"><span data-stu-id="71e3e-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="71e3e-202">Recebendo mensagens de assinaturas: manipuladores de eventos em microsserviços destinatários</span><span class="sxs-lookup"><span data-stu-id="71e3e-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="71e3e-203">Além da lógica de assinatura de evento, você precisa implementar o código interno para os manipuladores de eventos de integração (como um método de retorno de chamada).</span><span class="sxs-lookup"><span data-stu-id="71e3e-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="71e3e-204">O manipulador de eventos é o local em que você especifica o local em que as mensagens de eventos de um determinado tipo serão recebidas e processadas.</span><span class="sxs-lookup"><span data-stu-id="71e3e-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="71e3e-205">Primeiro, um manipulador de eventos recebe uma instância de evento do barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="71e3e-206">Em seguida, ele localiza o componente a ser processado, relacionado a esse evento de integração, propagando e persistindo o evento como uma alteração no estado no microsserviço destinatário.</span><span class="sxs-lookup"><span data-stu-id="71e3e-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="71e3e-207">Por exemplo, se um evento ProductPriceChanged se origina no microsserviço catálogo, ele é tratado no microsserviço carrinho de compras e também altera o estado nesse microsserviço destinatário de carrinho de compras, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="71e3e-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

<span data-ttu-id="71e3e-208">O manipulador de eventos deve verificar se o produto existe em qualquer uma das instâncias do carrinho de compras.</span><span class="sxs-lookup"><span data-stu-id="71e3e-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="71e3e-209">Ele também atualiza o preço do item para cada item de linha relacionado ao carrinho.</span><span class="sxs-lookup"><span data-stu-id="71e3e-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="71e3e-210">Por fim, ele cria um alerta sobre a alteração de preço, que será exibido para o usuário, conforme mostrado na Figura 6-24.</span><span class="sxs-lookup"><span data-stu-id="71e3e-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Captura de tela de um navegador mostrando a notificação de mudança de preço no carrinho do usuário.](./media/subscribe-events/display-item-price-change.png)

<span data-ttu-id="71e3e-212">**Figura 6-24**.</span><span class="sxs-lookup"><span data-stu-id="71e3e-212">**Figure 6-24**.</span></span> <span data-ttu-id="71e3e-213">Exibindo uma alteração de preço de item em um carrinho de compras, conforme comunicado pelos eventos de integração</span><span class="sxs-lookup"><span data-stu-id="71e3e-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="71e3e-214">Idempotência em eventos de mensagem de atualização</span><span class="sxs-lookup"><span data-stu-id="71e3e-214">Idempotency in update message events</span></span>

<span data-ttu-id="71e3e-215">Um aspecto importante dos eventos de mensagem de atualização é que uma falha em qualquer ponto da comunicação deverá fazer com que a mensagem seja repetida.</span><span class="sxs-lookup"><span data-stu-id="71e3e-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="71e3e-216">Caso contrário, uma tarefa em segundo plano poderá tentar publicar um evento que já tenha sido publicado, criando uma condição de corrida.</span><span class="sxs-lookup"><span data-stu-id="71e3e-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="71e3e-217">Certifique-se de que as atualizações são idempotentes ou que fornecem informações suficientes para garantir que você possa detectar uma duplicata, descartá-la e enviar de volta apenas uma resposta.</span><span class="sxs-lookup"><span data-stu-id="71e3e-217">Make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="71e3e-218">Conforme observado anteriormente, a idempotência significa que uma operação poderá ser executada várias vezes sem alterar o resultado.</span><span class="sxs-lookup"><span data-stu-id="71e3e-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="71e3e-219">Em um ambiente de sistema de mensagens, como ao comunicar eventos, um evento será idempotente se ele puder ser entregue várias vezes sem alterar o resultado para o microsserviço destinatário.</span><span class="sxs-lookup"><span data-stu-id="71e3e-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="71e3e-220">Isso pode ser necessário devido à natureza do evento em si ou devido à maneira como o sistema manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="71e3e-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="71e3e-221">A idempotência de mensagem é importante em qualquer aplicativo que use o sistema de mensagens, e não apenas em aplicativos que implementam o padrão do barramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="71e3e-222">Um exemplo de uma operação idempotente é uma instrução SQL que insere dados em uma tabela somente se os dados ainda não estiverem na tabela.</span><span class="sxs-lookup"><span data-stu-id="71e3e-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="71e3e-223">Não importa quantas vezes você executa essa instrução insert do SQL; o resultado será o mesmo: a tabela conterá esses dados.</span><span class="sxs-lookup"><span data-stu-id="71e3e-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="71e3e-224">Essa idempotência também poderá ser necessária ao lidar com mensagens se houver chances de que elas sejam enviadas e processadas mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="71e3e-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="71e3e-225">Por exemplo, se a lógica de repetição fizer com que um remetente envie exatamente a mesma mensagem mais de uma vez, você precisará verificar se ela é idempotente.</span><span class="sxs-lookup"><span data-stu-id="71e3e-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="71e3e-226">É possível projetar mensagens idempotentes.</span><span class="sxs-lookup"><span data-stu-id="71e3e-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="71e3e-227">Por exemplo, crie um evento que indica "definir o preço do produto como US$ 25" em vez de "adicionar US$ 5 ao preço do produto".</span><span class="sxs-lookup"><span data-stu-id="71e3e-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="71e3e-228">A primeira mensagem pode ser processada com segurança qualquer número de vezes e o resultado será o mesmo.</span><span class="sxs-lookup"><span data-stu-id="71e3e-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="71e3e-229">Isso não é válido para a segunda mensagem.</span><span class="sxs-lookup"><span data-stu-id="71e3e-229">That is not true for the second message.</span></span> <span data-ttu-id="71e3e-230">Mas, mesmo no primeiro caso, talvez não seja interessante processar o primeiro evento, porque o sistema também pode ter enviado um evento de alteração de preço mais recente, e o novo preço seria substituído.</span><span class="sxs-lookup"><span data-stu-id="71e3e-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="71e3e-231">Outro exemplo pode ser um evento concluído por ordem que é propagado para vários assinantes.</span><span class="sxs-lookup"><span data-stu-id="71e3e-231">Another example might be an order-completed event that's propagated to multiple subscribers.</span></span> <span data-ttu-id="71e3e-232">O aplicativo tem que garantir que as informações do pedido sejam atualizadas em outros sistemas apenas uma vez, mesmo que haja eventos de mensagens duplicadas para o mesmo evento concluído por ordem.</span><span class="sxs-lookup"><span data-stu-id="71e3e-232">The app has to make sure that order information is updated in other systems only once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="71e3e-233">É conveniente ter algum tipo de identidade por evento, para que você possa criar uma lógica que imponha que cada evento seja processado apenas uma vez em cada destinatário.</span><span class="sxs-lookup"><span data-stu-id="71e3e-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="71e3e-234">Alguns processamentos de mensagens são inerentemente idempotentes.</span><span class="sxs-lookup"><span data-stu-id="71e3e-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="71e3e-235">Por exemplo, se um sistema gerar miniaturas de imagem, não importará quantas vezes a mensagem sobre a miniatura gerada vai ser processada; o resultado será que as miniaturas foram geradas e elas serão sempre as mesmas.</span><span class="sxs-lookup"><span data-stu-id="71e3e-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="71e3e-236">Por outro lado, operações como chamar um gateway de pagamento para cobrar um cartão de crédito jamais poderão ser idempotentes.</span><span class="sxs-lookup"><span data-stu-id="71e3e-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="71e3e-237">Nesses casos, você precisa garantir que o processamento de uma mensagem várias vezes tenha o efeito que você espera.</span><span class="sxs-lookup"><span data-stu-id="71e3e-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="71e3e-238">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="71e3e-238">Additional resources</span></span>

- <span data-ttu-id="71e3e-239">**Honrando a idempotência da mensagem** </span><span class="sxs-lookup"><span data-stu-id="71e3e-239">**Honoring message idempotency** </span></span>\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="71e3e-240">Eliminando a duplicação de mensagens de eventos de integração</span><span class="sxs-lookup"><span data-stu-id="71e3e-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="71e3e-241">Você pode garantir que os eventos de mensagem sejam enviados e processados apenas uma vez por assinante em diferentes níveis.</span><span class="sxs-lookup"><span data-stu-id="71e3e-241">You can make sure that message events are sent and processed only once per subscriber at different levels.</span></span> <span data-ttu-id="71e3e-242">Uma maneira é usar um recurso de eliminação de duplicação oferecido pela infraestrutura do sistema de mensagens que você está usando.</span><span class="sxs-lookup"><span data-stu-id="71e3e-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="71e3e-243">Outra é implementar uma lógica personalizada no microsserviço de destino.</span><span class="sxs-lookup"><span data-stu-id="71e3e-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="71e3e-244">A melhor opção é ter validações no nível de transporte e no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="71e3e-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="71e3e-245">Eliminando a duplicação de eventos de mensagem no nível do EventHandler</span><span class="sxs-lookup"><span data-stu-id="71e3e-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="71e3e-246">Uma maneira de garantir que um evento seja processado apenas uma vez por qualquer receptor é implementando certa lógica ao processar os eventos de mensagem em manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="71e3e-246">One way to make sure that an event is processed only once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="71e3e-247">Por exemplo, essa é a abordagem usada no aplicativo eShopOnContainers, como você pode ver no [código-fonte da classe UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) quando recebe um evento de `UserCheckoutAcceptedIntegrationEvent` integração.</span><span class="sxs-lookup"><span data-stu-id="71e3e-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives a `UserCheckoutAcceptedIntegrationEvent` integration event.</span></span> <span data-ttu-id="71e3e-248">(Neste caso, `CreateOrderCommand` o é `IdentifiedCommand`embrulhado com `eventMsg.RequestId` um , usando o como um identificador, antes de enviá-lo para o manipulador de comando).</span><span class="sxs-lookup"><span data-stu-id="71e3e-248">(In this case, the `CreateOrderCommand` is wrapped with an `IdentifiedCommand`, using the `eventMsg.RequestId` as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="71e3e-249">Eliminando a duplicação de mensagens ao usar RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="71e3e-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="71e3e-250">Quando ocorrem falhas intermitentes na rede, as mensagens podem ser duplicadas e o destinatário da mensagem deve estar preparado para lidar com essas mensagens duplicadas.</span><span class="sxs-lookup"><span data-stu-id="71e3e-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="71e3e-251">Sempre que possível, os destinatários devem lidar com as mensagens de maneira idempotente, pois isso é melhor que tratá-las explicitamente com a eliminação de duplicação.</span><span class="sxs-lookup"><span data-stu-id="71e3e-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="71e3e-252">De acordo com a documentação do [RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Se uma mensagem for entregue a um consumidor e depois for remanerada (porque não foi reconhecida antes da conexão com o consumidor cair, por exemplo) então a RabbitMQ definirá a bandeira reentregue quando for entregue novamente (seja para o mesmo consumidor ou outra).</span><span class="sxs-lookup"><span data-stu-id="71e3e-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), "If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="71e3e-253">Se o sinalizador "reentregue" estiver definido, o receptor deve levar isso em conta, porque a mensagem já pode ter sido processada.</span><span class="sxs-lookup"><span data-stu-id="71e3e-253">If the "redelivered" flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="71e3e-254">Mas isso não é garantido; a mensagem pode nunca ter alcançado o destinatário depois de deixar o agente de mensagens, talvez por causa de problemas de rede.</span><span class="sxs-lookup"><span data-stu-id="71e3e-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="71e3e-255">Por outro lado, se a bandeira "reentregue" não for definida, é garantido que a mensagem não tenha sido enviada mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="71e3e-255">On the other hand, if the "redelivered" flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="71e3e-256">Portanto, o receptor precisa deduplicar mensagens ou processar mensagens de forma idempotente somente se a bandeira "reentregue" for definida na mensagem.</span><span class="sxs-lookup"><span data-stu-id="71e3e-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the "redelivered" flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="71e3e-257">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="71e3e-257">Additional resources</span></span>

- <span data-ttu-id="71e3e-258">**EShopOnContainers forked usando NServiceBus (Software Particular)** </span><span class="sxs-lookup"><span data-stu-id="71e3e-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="71e3e-259">**Mensagens orientadas a eventos** </span><span class="sxs-lookup"><span data-stu-id="71e3e-259">**Event Driven Messaging** </span></span>\
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- <span data-ttu-id="71e3e-260">**Jimmy Bogard. Refatoração para a resiliência: Avaliando o acoplamento** </span><span class="sxs-lookup"><span data-stu-id="71e3e-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="71e3e-261">**Publique-Inscreva-se canal** </span><span class="sxs-lookup"><span data-stu-id="71e3e-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="71e3e-262">**Comunicação entre contextos limitados** </span><span class="sxs-lookup"><span data-stu-id="71e3e-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="71e3e-263">**Consistência eventual** </span><span class="sxs-lookup"><span data-stu-id="71e3e-263">**Eventual Consistency** </span></span>\
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- <span data-ttu-id="71e3e-264">**Philip Brown. Estratégias para integrar contextos limitados** </span><span class="sxs-lookup"><span data-stu-id="71e3e-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="71e3e-265">**Chris Richardson. Desenvolvimento de Microserviços Transacionais Utilizando Agregados, Sourcing de Eventos e CQRS - Parte 2** </span><span class="sxs-lookup"><span data-stu-id="71e3e-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="71e3e-266">**Chris Richardson. Padrão de Sourcing de Eventos** </span><span class="sxs-lookup"><span data-stu-id="71e3e-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="71e3e-267">**Introdução ao Sourcing de Eventos** </span><span class="sxs-lookup"><span data-stu-id="71e3e-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="71e3e-268">**Banco de dados Event Store**.</span><span class="sxs-lookup"><span data-stu-id="71e3e-268">**Event Store database**.</span></span> <span data-ttu-id="71e3e-269">Site oficial.</span><span class="sxs-lookup"><span data-stu-id="71e3e-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="71e3e-270">**Patrick Nommensen. Gerenciamento de dados orientado a eventos para microserviços** </span><span class="sxs-lookup"><span data-stu-id="71e3e-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="71e3e-271">**Teorema do CAP** </span><span class="sxs-lookup"><span data-stu-id="71e3e-271">**The CAP Theorem** </span></span>\
    <https://en.wikipedia.org/wiki/CAP_theorem>

- <span data-ttu-id="71e3e-272">**O que é o Teorema de CAP?**</span><span class="sxs-lookup"><span data-stu-id="71e3e-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="71e3e-273">**Primer de consistência de dados** </span><span class="sxs-lookup"><span data-stu-id="71e3e-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="71e3e-274">**Rick Saling. O Teorema do CAP: Por que "Tudo é Diferente" com a Nuvem e internet** </span><span class="sxs-lookup"><span data-stu-id="71e3e-274">**Rick Saling. The CAP Theorem: Why "Everything is Different" with the Cloud and Internet** </span></span>\
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="71e3e-275">**Eric Brewer. CAP Doze anos depois: como as "regras" mudaram** </span><span class="sxs-lookup"><span data-stu-id="71e3e-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="71e3e-276">**Ônibus de Serviço Azure. Mensagens Intermediadas: Detecção de duplicatas**  </span><span class="sxs-lookup"><span data-stu-id="71e3e-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="71e3e-277">**Guia de Confiabilidade** (documentação do RabbitMQ) </span><span class="sxs-lookup"><span data-stu-id="71e3e-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> <span data-ttu-id="71e3e-278">[Próximo](rabbitmq-event-bus-development-test-environment.md)
> [anterior](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="71e3e-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
