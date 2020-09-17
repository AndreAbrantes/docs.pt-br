---
title: Usando bancos de dados NoSQL como uma infraestrutura de persistência
description: Entenda o uso de bancos de dados NoSql em geral e Azure Cosmos DB em particular, como uma opção para implementar a persistência.
ms.date: 01/30/2020
ms.openlocfilehash: c4f9199b9e88a39581437eca340e92f4fd450003
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738795"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="9dc89-103">Usar bancos de dados NoSQL como infraestrutura de persistência</span><span class="sxs-lookup"><span data-stu-id="9dc89-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="9dc89-104">Ao usar bancos de dados NoSQL para a camada de dados da infraestrutura, normalmente, não se usa um ORM (mapeamento objeto-relacional) como o Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="9dc89-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="9dc89-105">Nesse caso, é possível usar a API fornecida pelo mecanismo NoSQL, como o Azure Cosmos DB, o MongoDB, o Cassandra, o RavenDB, o CouchDB ou as tabelas de Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="9dc89-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="9dc89-106">No entanto, ao usar um banco de dados NoSQL, principalmente um banco de dados orientado a documentos como o Azure Cosmos DB, o CouchDB ou o RavenDB, a maneira de criar o modelo com agregações de DDD é parcialmente semelhante à maneira de fazer isso no EF Core, em relação à identificação de raízes agregadas, classes de entidade filha e classes de objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="9dc89-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="9dc89-107">Mas, por fim, a seleção do banco de dados realmente afetará o design.</span><span class="sxs-lookup"><span data-stu-id="9dc89-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="9dc89-108">Ao usar um banco de dados orientado a documentos, você implementa uma agregação como um único documento serializado em JSON ou em outro formato.</span><span class="sxs-lookup"><span data-stu-id="9dc89-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="9dc89-109">No entanto, o uso do banco de dados é transparente do ponto de vista do código do modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="9dc89-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="9dc89-110">Ao usar um banco de dados NoSQL, você ainda está usando classes de entidade e classes de raiz de agregação, mas com maior flexibilidade do que ao usar o EF Core porque a persistência não é relacional.</span><span class="sxs-lookup"><span data-stu-id="9dc89-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="9dc89-111">A diferença está em como persistir esse modelo.</span><span class="sxs-lookup"><span data-stu-id="9dc89-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="9dc89-112">Se você implementar o modelo de domínio com base em classes de entidade POCO (objeto CRL básico), independentemente da persistência da infraestrutura, poderá parecer que é possível passar para uma infraestrutura de persistência diferente, até mesmo de relacional para NoSQL.</span><span class="sxs-lookup"><span data-stu-id="9dc89-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="9dc89-113">No entanto, essa não deve ser a sua meta.</span><span class="sxs-lookup"><span data-stu-id="9dc89-113">However, that should not be your goal.</span></span> <span data-ttu-id="9dc89-114">Sempre há restrições e compensações nas diferentes tecnologias de bancos de dados, portanto, não é possível usar o mesmo modelo para bancos de dados relacionais ou NoSQL.</span><span class="sxs-lookup"><span data-stu-id="9dc89-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="9dc89-115">Alterar os modelos de persistência não é tão fácil, pois as transações e as operações de persistência são muito diferentes.</span><span class="sxs-lookup"><span data-stu-id="9dc89-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="9dc89-116">Por exemplo, em um banco de dados orientado a documentos, é possível que uma raiz de agregação tenha diversas propriedades de coleção filhas.</span><span class="sxs-lookup"><span data-stu-id="9dc89-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="9dc89-117">Em um banco de dados relacional, consultar várias propriedades de coleção filhas é algo de difícil otimização, pois o EF retorna a você uma instrução UNION ALL SQL.</span><span class="sxs-lookup"><span data-stu-id="9dc89-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="9dc89-118">Ter o mesmo modelo de domínio para bancos de dados relacionais ou bancos de dados NoSQL não é simples e não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="9dc89-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="9dc89-119">Você realmente precisa criar seu modelo com uma compreensão de como os dados serão usados em cada banco de dados específico.</span><span class="sxs-lookup"><span data-stu-id="9dc89-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="9dc89-120">Um benefício de usar bancos de dados NoSQL é que as entidades são mais desnormalizadas, portanto, você não precisa definir um mapeamento de tabela.</span><span class="sxs-lookup"><span data-stu-id="9dc89-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="9dc89-121">O modelo de domínio pode ser mais flexível do que ao usar um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="9dc89-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="9dc89-122">Ao criar o modelo de domínio baseado em agregações, passar para bancos de dados NoSQL e orientados a documentos pode ser ainda mais fácil do que usar um banco de dados relacional, porque as agregações criadas são semelhantes aos documentos serializados em um banco de dados orientado a documentos.</span><span class="sxs-lookup"><span data-stu-id="9dc89-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="9dc89-123">Em seguida, você pode incluir nessas "bolsas" todas as informações que você pode precisar para essa agregação.</span><span class="sxs-lookup"><span data-stu-id="9dc89-123">Then you can include in those "bags" all the information you might need for that aggregate.</span></span>

<span data-ttu-id="9dc89-124">Por exemplo, o código JSON a seguir é um exemplo da implementação de uma agregação de pedido ao usar um banco de dados orientado a documentos.</span><span class="sxs-lookup"><span data-stu-id="9dc89-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="9dc89-125">Ele é semelhante à agregação de pedido que foi implementada no exemplo eShopOnContainers, mas sem usar o Core EF.</span><span class="sxs-lookup"><span data-stu-id="9dc89-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="9dc89-126">Introdução ao Azure Cosmos DB e à API nativa do Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="9dc89-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="9dc89-127">O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) é o serviço de banco de dados distribuído globalmente da Microsoft para aplicativos críticos.</span><span class="sxs-lookup"><span data-stu-id="9dc89-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="9dc89-128">O Azure Cosmos DB fornece [distribuição global de chave](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [dimensionamento elástico de taxa de transferência e armazenamento](https://docs.microsoft.com/azure/cosmos-db/partition-data) em todo o mundo, latências de milissegundos de dígito único no 99 º percentil, [cinco níveis de consistência bem definidos](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)e garantia de alta disponibilidade, tudo apoiado por [SLAs líderes do setor](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="9dc89-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="9dc89-129">O Azure Cosmos DB [indexa dados automaticamente](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) sem a necessidade de lidar com o gerenciamento do esquema e do índice.</span><span class="sxs-lookup"><span data-stu-id="9dc89-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="9dc89-130">Ele tem vários modelos e dá suporte a modelos de dados de colunas, grafos, valores-chave e documentos.</span><span class="sxs-lookup"><span data-stu-id="9dc89-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![Diagrama mostrando a distribuição global Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

<span data-ttu-id="9dc89-132">**Figura 7-19**.</span><span class="sxs-lookup"><span data-stu-id="9dc89-132">**Figure 7-19**.</span></span> <span data-ttu-id="9dc89-133">Distribuição global do Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="9dc89-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="9dc89-134">Ao usar um modelo C\# para implementar a agregação a ser usada pela API do Azure Cosmos DB, a agregação pode ser semelhante à das classes POCO do C\# usadas com o EF Core.</span><span class="sxs-lookup"><span data-stu-id="9dc89-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="9dc89-135">A diferença está na maneira de usá-las nas camadas de aplicativo e de infraestrutura, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="9dc89-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot's methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="9dc89-136">Você pode ver que a maneira de trabalhar com o modelo de domínio pode ser semelhante à maneira de usá-lo na camada do modelo de domínio quando a infraestrutura é o EF.</span><span class="sxs-lookup"><span data-stu-id="9dc89-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="9dc89-137">Você ainda pode usar os mesmos métodos de raiz de agregação para garantir a consistência, as invariáveis e as validações na agregação.</span><span class="sxs-lookup"><span data-stu-id="9dc89-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="9dc89-138">No entanto, ao persistir o modelo para o banco de dados NoSQL, o código e a API serão radicalmente alterados em comparação com o código do EF Core ou com qualquer outro código relacionado a bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="9dc89-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="9dc89-139">Implementar o código do .NET direcionado ao MongoDB e ao Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="9dc89-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="9dc89-140">Usar o Azure Cosmos DB de contêineres do .NET</span><span class="sxs-lookup"><span data-stu-id="9dc89-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="9dc89-141">Você pode acessar os bancos de dados Azure Cosmos DB do código do .NET em execução em contêineres, como de qualquer outro aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="9dc89-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="9dc89-142">Por exemplo, os microsserviços Locations.API e Marketing.API no eShopOnContainers são implementados para que possam consumir bancos de dados Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="9dc89-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="9dc89-143">No entanto, há uma limitação no Azure Cosmos DB do ponto de vista do ambiente de desenvolvimento do Docker.</span><span class="sxs-lookup"><span data-stu-id="9dc89-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="9dc89-144">Embora haja um [emulador de Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/local-emulator) local que pode ser executado em um computador de desenvolvimento, ele dá suporte apenas ao Windows.</span><span class="sxs-lookup"><span data-stu-id="9dc89-144">Even though there’s an on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) that can run in a local development machine, it only supports Windows.</span></span> <span data-ttu-id="9dc89-145">Não há suporte para Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="9dc89-145">Linux and macOS aren't supported.</span></span>

<span data-ttu-id="9dc89-146">Também há a possibilidade de executar esse emulador no Docker, mas apenas em contêineres do Windows, não com contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="9dc89-146">There's also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="9dc89-147">Essa é uma handicap inicial para o ambiente de desenvolvimento se seu aplicativo for implantado como contêineres do Linux, já que, no momento, você não pode implantar contêineres do Linux e do Windows em Docker for Windows ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9dc89-147">That's an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you can't deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="9dc89-148">Todos os contêineres que estão sendo implantados precisam ser do Linux ou do Windows.</span><span class="sxs-lookup"><span data-stu-id="9dc89-148">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="9dc89-149">O modo de implantação mais simples e ideal para uma solução de Desenvolvimento/Teste é poder implantar os sistemas de banco de dados como contêineres juntamente com contêineres personalizados para que os ambientes de Desenvolvimento/Teste estejam sempre consistentes.</span><span class="sxs-lookup"><span data-stu-id="9dc89-149">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="9dc89-150">Usar a API do MongoDB para contêineres locais do Linux/Windows de Desenvolvimento/Teste além do Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="9dc89-150">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="9dc89-151">Os bancos de dados Cosmos DB são compatíveis com a API do MongoDB para .NET, e com o protocolo de transmissão nativo do MongoDB.</span><span class="sxs-lookup"><span data-stu-id="9dc89-151">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="9dc89-152">Isso significa que, usando os drivers existentes, o aplicativo escrito para o MongoDB agora pode se comunicar com o Cosmos DB e usar os bancos de dados do Cosmos DB em vez dos bancos de dados do MongoDB, conforme é mostrado na Figura 7-20.</span><span class="sxs-lookup"><span data-stu-id="9dc89-152">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Diagrama mostrando que Cosmos DB dá suporte ao protocolo de transmissão .NET e MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

<span data-ttu-id="9dc89-154">**Figura 7-20**.</span><span class="sxs-lookup"><span data-stu-id="9dc89-154">**Figure 7-20**.</span></span> <span data-ttu-id="9dc89-155">Usando a API e o protocolo do MongoDB para acessar o Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="9dc89-155">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="9dc89-156">Essa é uma abordagem muito conveniente para prova de conceitos em ambientes do Docker com contêineres do Linux, porque a [imagem do Docker do MongoDB](https://hub.docker.com/r/_/mongo/) é uma imagem para várias arquiteturas, compatível com contêineres do Linux do Docker e do Windows do Docker.</span><span class="sxs-lookup"><span data-stu-id="9dc89-156">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="9dc89-157">Conforme é mostrado na imagem a seguir, usando a API do MongoDB, o eShopOnContainers permite contêineres do Windows e do Linux do MongoDB para o ambiente de desenvolvimento local, mas também é possível passar para uma solução de nuvem de PaaS escalonável, como o Azure Cosmos DB, simplesmente [alterando a cadeia de conexão do MongoDB para apontar para o Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="9dc89-157">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![Diagrama mostrando que o microserviço de localização no eShopOnContainers pode usar o Cosmos DB ou o Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

<span data-ttu-id="9dc89-159">**Figura 7-21**.</span><span class="sxs-lookup"><span data-stu-id="9dc89-159">**Figure 7-21**.</span></span> <span data-ttu-id="9dc89-160">eShopOnContainers usando contêineres do MongoDB para o ambiente de desenvolvimento ou para o Azure Cosmos DB para produção</span><span class="sxs-lookup"><span data-stu-id="9dc89-160">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="9dc89-161">O Azure Cosmos DB de produção seria executado na nuvem do Azure como um serviço de PaaS e escalonável.</span><span class="sxs-lookup"><span data-stu-id="9dc89-161">The production Azure Cosmos DB would be running in Azure's cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="9dc89-162">Os contêineres do .NET Core personalizados podem ser executados em um host do Docker de desenvolvimento local (que esteja usando o Docker para Windows em um computador Windows 10) ou ser implantados em um ambiente de produção, como o Kubernetes no AKS do Azure ou no Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="9dc89-162">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="9dc89-163">Nesse segundo ambiente, você implantaria apenas os contêineres personalizados do .NET Core, mas não o contêiner do MongoDB, já que usaria Azure Cosmos DB na nuvem para lidar com os dados em produção.</span><span class="sxs-lookup"><span data-stu-id="9dc89-163">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you'd be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="9dc89-164">Um benefício claro de usar a API do MongoDB é que a solução pode ser executada em ambos os mecanismos de banco de dados, MongoDB ou Azure Cosmos DB, facilitando as migrações para diferentes ambientes.</span><span class="sxs-lookup"><span data-stu-id="9dc89-164">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="9dc89-165">No entanto, às vezes, vale a pena usar uma API nativa (ou seja, a API nativa do Cosmos DB) para aproveitar ao máximo os recursos de um mecanismo de banco de dados específico.</span><span class="sxs-lookup"><span data-stu-id="9dc89-165">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="9dc89-166">Para obter mais comparações entre o simples uso do MongoDB ou do Cosmos DB na nuvem, consulte [Benefícios de usar o Azure Cosmos DB, nesta página](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="9dc89-166">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="9dc89-167">Analise sua abordagem para aplicativos de produção: API do MongoDB versus API de Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="9dc89-167">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="9dc89-168">No eShopOnContainers, estamos usando a API do MongoDB porque nossa prioridade era fundamental para ter um ambiente de desenvolvimento/teste consistente usando um banco de dados NoSQL que também poderia funcionar com Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="9dc89-168">In eShopOnContainers, we're using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="9dc89-169">No entanto, se você estiver planejando usar a API do MongoDB para acessar Azure Cosmos DB no Azure para aplicativos de produção, analise as diferenças em capacidades e desempenho ao usar a API do MongoDB para acessar bancos de dados do Azure Cosmos DB em comparação com o uso da API de Azure Cosmos DB nativa.</span><span class="sxs-lookup"><span data-stu-id="9dc89-169">However, if you are planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="9dc89-170">Se for semelhante, você poderá usar a API do MongoDB e obter o benefício de permitir dois mecanismos de banco de dados NoSQL simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="9dc89-170">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="9dc89-171">Você também pode usar clusters do MongoDB como o banco de dados de produção na nuvem do Azure, também, com o [serviço MongoDB do Azure](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="9dc89-171">You could also use MongoDB clusters as the production database in Azure's cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="9dc89-172">Mas esse não é um serviço de PaaS fornecido pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9dc89-172">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="9dc89-173">Nesse caso, o Azure está apenas hospedando essa solução proveniente do MongoDB.</span><span class="sxs-lookup"><span data-stu-id="9dc89-173">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="9dc89-174">Basicamente, essa é apenas uma declaração informando que você não deve sempre usar a API do MongoDB em Azure Cosmos DB, como fizemos no eShopOnContainers porque ela era uma opção conveniente para contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="9dc89-174">Basically, this is just a disclaimer stating that you shouldn't always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="9dc89-175">A decisão deve ser baseada as necessidades específicas e nos testes que você precisa fazer para o aplicativo de produção.</span><span class="sxs-lookup"><span data-stu-id="9dc89-175">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="9dc89-176">O código: usar a API MongoDB em aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="9dc89-176">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="9dc89-177">A API do MongoDB para .NET baseia-se em pacotes NuGet que você precisa adicionar nos projetos, como no projeto Locations.API mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="9dc89-177">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![Captura de tela das dependências nos pacotes NuGet do MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

<span data-ttu-id="9dc89-179">**Figura 7-22**.</span><span class="sxs-lookup"><span data-stu-id="9dc89-179">**Figure 7-22**.</span></span> <span data-ttu-id="9dc89-180">Referências de pacotes NuGet da API do MongoDB em um projeto do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9dc89-180">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="9dc89-181">Vamos examinar o código nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="9dc89-181">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="9dc89-182">Um modelo usado pela API do MongoDB</span><span class="sxs-lookup"><span data-stu-id="9dc89-182">A Model used by MongoDB API</span></span>

<span data-ttu-id="9dc89-183">Primeiro, você precisa definir um modelo que conterá os dados provenientes do banco de dado no espaço de memória do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9dc89-183">First, you need to define a model that will hold the data coming from the database in your application's memory space.</span></span> <span data-ttu-id="9dc89-184">Aqui está um exemplo do modelo usado para locais em eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9dc89-184">Here's an example of the model used for Locations at eShopOnContainers.</span></span>

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList)
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

<span data-ttu-id="9dc89-185">Você pode ver que há alguns atributos e tipos provenientes dos pacotes NuGet do MongoDB.</span><span class="sxs-lookup"><span data-stu-id="9dc89-185">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="9dc89-186">Os bancos de dados NoSQL normalmente são muito bem adequados para trabalhar com os dados hierárquicos não relacionais.</span><span class="sxs-lookup"><span data-stu-id="9dc89-186">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="9dc89-187">Neste exemplo, estamos usando tipos do MongoDB criados especialmente para localizações geográficas, como `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="9dc89-187">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="9dc89-188">Recuperar o banco de dados e a coleção</span><span class="sxs-lookup"><span data-stu-id="9dc89-188">Retrieve the database and the collection</span></span>

<span data-ttu-id="9dc89-189">No eShopOnContainers, criamos um contexto de banco de dados personalizado no qual podemos implementar o código para recuperar o banco de dados e as MongoCollections, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9dc89-189">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }
}
```

#### <a name="retrieve-the-data"></a><span data-ttu-id="9dc89-190">Recuperar os dados</span><span class="sxs-lookup"><span data-stu-id="9dc89-190">Retrieve the data</span></span>

<span data-ttu-id="9dc89-191">No código C#, como nos controladores de API Web ou na implementação personalizada de repositórios, você pode escrever um código semelhante ao seguinte ao consultar por meio da API do MongoDB.</span><span class="sxs-lookup"><span data-stu-id="9dc89-191">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="9dc89-192">Observe que o objeto `_context` é uma instância da classe `LocationsContext` anterior.</span><span class="sxs-lookup"><span data-stu-id="9dc89-192">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="9dc89-193">Use uma variável de ambiente no arquivo docker-compose.override.yml para a cadeia de conexão do MongoDB</span><span class="sxs-lookup"><span data-stu-id="9dc89-193">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="9dc89-194">Ao criar um objeto do MongoClient, ele precisa de um parâmetro fundamental, que é exatamente o parâmetro `ConnectionString`, apontando para o banco de dados certo.</span><span class="sxs-lookup"><span data-stu-id="9dc89-194">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="9dc89-195">No caso do eShopOnContainers, a cadeia de conexão pode apontar para um contêiner do Docker do MongoDB local ou para um banco de dados de Azure Cosmos DB de "produção".</span><span class="sxs-lookup"><span data-stu-id="9dc89-195">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a "production" Azure Cosmos DB database.</span></span>  <span data-ttu-id="9dc89-196">Essa cadeia de conexão vem de variáveis de ambiente definidas em arquivos `docker-compose.override.yml` usados ao implantar com o docker-compose ou o Visual Studio, como no código yml a seguir.</span><span class="sxs-lookup"><span data-stu-id="9dc89-196">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations-api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}

```

<span data-ttu-id="9dc89-197">A variável de ambiente `ConnectionString` é resolvida desta forma: se a variável global `ESHOP_AZURE_COSMOSDB` estiver definida no arquivo `.env` com a cadeia de conexão do Azure Cosmos DB, ela o usará para acessar o banco de dados Azure Cosmos DB na nuvem.</span><span class="sxs-lookup"><span data-stu-id="9dc89-197">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="9dc89-198">Se não estiver definido, ele utilizará o `mongodb://nosqldata` valor e usará o contêiner de desenvolvimento do MongoDB.</span><span class="sxs-lookup"><span data-stu-id="9dc89-198">If it’s not defined, it will take the `mongodb://nosqldata` value and use the development MongoDB container.</span></span>

<span data-ttu-id="9dc89-199">O código a seguir mostra o arquivo `.env` com a variável de ambiente global da cadeia de conexão do Azure Cosmos DB, conforme implementado no eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="9dc89-199">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

<span data-ttu-id="9dc89-200">Remova a marca de comentário da linha de ESHOP_AZURE_COSMOSDB e atualize-a com a cadeia de conexão Azure Cosmos DB obtida do portal do Azure, conforme explicado em [conectar um aplicativo MongoDB a Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="9dc89-200">Uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="9dc89-201">Se a `ESHOP_AZURE_COSMOSDB` variável global estiver vazia, o que significa que ela está comentada no `.env` arquivo, o contêiner usará uma cadeia de conexão padrão do MongoDB.</span><span class="sxs-lookup"><span data-stu-id="9dc89-201">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning it's commented out in the `.env` file, then the container uses a default MongoDB connection string.</span></span> <span data-ttu-id="9dc89-202">Essa cadeia de conexão aponta para o contêiner local do MongoDB implantado em eShopOnContainers que é nomeado `nosqldata` e definido no arquivo Docker-Compose, conforme mostrado no seguinte código. yml:</span><span class="sxs-lookup"><span data-stu-id="9dc89-202">This connection string points to the local MongoDB container deployed in eShopOnContainers that is named `nosqldata` and was defined at the docker-compose file, as shown in the following .yml code:</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="9dc89-203">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="9dc89-203">Additional resources</span></span>

- <span data-ttu-id="9dc89-204">**Modelando dados de documentos para bancos de dados NoSQL** </span><span class="sxs-lookup"><span data-stu-id="9dc89-204">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="9dc89-205">**Vaughn Vernon. O armazenamento agregado ideal de design controlado por domínio?**</span><span class="sxs-lookup"><span data-stu-id="9dc89-205">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="9dc89-206">**Introdução à Azure Cosmos DB: API para MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="9dc89-206">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="9dc89-207">**Azure Cosmos DB: compilar um aplicativo Web da API do MongoDB com o .NET e o portal do Azure**  </span><span class="sxs-lookup"><span data-stu-id="9dc89-207">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="9dc89-208">**Usar o emulador de Azure Cosmos DB para desenvolvimento e teste locais**  </span><span class="sxs-lookup"><span data-stu-id="9dc89-208">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="9dc89-209">**Conectar um aplicativo MongoDB ao Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="9dc89-209">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="9dc89-210">**A imagem do Docker do emulador Cosmos DB (contêiner do Windows)**  </span><span class="sxs-lookup"><span data-stu-id="9dc89-210">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="9dc89-211">**A imagem do Docker do MongoDB (contêiner do Linux e do Windows)**  </span><span class="sxs-lookup"><span data-stu-id="9dc89-211">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="9dc89-212">**Usar MongoChef (Studio 3T) com uma conta Azure Cosmos DB: API para MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="9dc89-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="9dc89-213">[Anterior](infrastructure-persistence-layer-implementation-entity-framework-core.md) 
> [Avançar](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="9dc89-213">[Previous](infrastructure-persistence-layer-implementation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
