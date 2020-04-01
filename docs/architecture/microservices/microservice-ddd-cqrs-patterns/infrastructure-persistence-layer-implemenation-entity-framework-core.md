---
title: Implementando a camada de persistência da infraestrutura com o Entity Framework Core
description: .NET Microservices Architecture for Containerized .NET Applications | Explorar os detalhes de implementação para a camada de persistência da infra-estrutura, usando o Entity Framework Core.
ms.date: 01/30/2020
ms.openlocfilehash: 2d28d9246be3e102625ed5bb67ee1ccede03c942
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523318"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="788d1-103">Implementar a camada de persistência de infraestrutura com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="788d1-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="788d1-104">Ao usar bancos de dados relacionais, como o SQL Server, o Oracle ou o PostgreSQL, uma abordagem recomendada é implementar a camada de persistência com base no EF (Entity Framework).</span><span class="sxs-lookup"><span data-stu-id="788d1-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="788d1-105">O EF é compatível com LINQ e fornece objetos fortemente tipados para o modelo, bem como uma persistência simplificada no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="788d1-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="788d1-106">O Entity Framework tem uma longa história de participação no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="788d1-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="788d1-107">Ao usar o .NET Core, você também deve usar o Entity Framework Core, que é executado no Windows ou no Linux da mesma maneira que o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="788d1-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="788d1-108">O EF Core é uma reformulação completa do Entity Framework, implementado com muito menos espaço e importantes melhorias no desempenho.</span><span class="sxs-lookup"><span data-stu-id="788d1-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="788d1-109">Introdução ao Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="788d1-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="788d1-110">O Entity Framework (EF) Core é uma versão de multiplaforma leve, extensível e de plataforma cruzada da popular tecnologia de acesso a dados do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="788d1-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="788d1-111">Ele foi introduzido com o .NET Core em meados de 2016.</span><span class="sxs-lookup"><span data-stu-id="788d1-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="788d1-112">Como uma introdução ao EF Core já está disponível na documentação da Microsoft, aqui nós vamos fornecer apenas os links para as informações.</span><span class="sxs-lookup"><span data-stu-id="788d1-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="788d1-113">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="788d1-113">Additional resources</span></span>

- <span data-ttu-id="788d1-114">**Núcleo de Estruturas de Entidades** </span><span class="sxs-lookup"><span data-stu-id="788d1-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="788d1-115">**Começando com ASP.NET Núcleo Core e Entity Framework Core usando o Visual Studio** </span><span class="sxs-lookup"><span data-stu-id="788d1-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="788d1-116">**Classe DbContext** </span><span class="sxs-lookup"><span data-stu-id="788d1-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="788d1-117">**Compare EF Core & EF6.x** </span><span class="sxs-lookup"><span data-stu-id="788d1-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="788d1-118">Infraestrutura no Entity Framework Core da perspectiva do DDD</span><span class="sxs-lookup"><span data-stu-id="788d1-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="788d1-119">Do ponto de vista do DDD, um recurso importante do EF é a capacidade de usar as entidades de domínio POCO (objeto CRL básico), também conhecidas na terminologia do EF como *entidades code-first* POCO.</span><span class="sxs-lookup"><span data-stu-id="788d1-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="788d1-120">Se você usar as entidades de domínio POCO, as classes de modelo de domínio ignorarão a persistência, seguindo os princípios de [Ignorância de Persistência](https://deviq.com/persistence-ignorance/) e de [Ignorância de Infraestrutura](https://ayende.com/blog/3137/infrastructure-ignorance).</span><span class="sxs-lookup"><span data-stu-id="788d1-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="788d1-121">De acordo com os padrões do DDD você deve encapsular o comportamento e as regras do domínio dentro da própria classe de entidade, assim ela poderá controlar as invariáveis, as validações e as regras ao acessar qualquer coleção.</span><span class="sxs-lookup"><span data-stu-id="788d1-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="788d1-122">Portanto, não é uma prática recomendada no DDD permitir o acesso público a coleções de entidades filhas ou a objetos de valor.</span><span class="sxs-lookup"><span data-stu-id="788d1-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="788d1-123">Em vez disso, é possível expor métodos que controlam como e quando as coleções de propriedade e os campos podem ser atualizados e qual comportamento e medidas deverão ser tomadas quando isso acontecer.</span><span class="sxs-lookup"><span data-stu-id="788d1-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="788d1-124">Desde o EF Core 1.1, para atender a esses requisitos de DDD, é possível ter campos simples nas entidades em vez de propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="788d1-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="788d1-125">Se você não quiser que um campo de entidade fique acessível externamente, bastará criar o atributo ou o campo em vez de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="788d1-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="788d1-126">Também é possível usar setters de propriedade privada.</span><span class="sxs-lookup"><span data-stu-id="788d1-126">You can also use private property setters.</span></span>

<span data-ttu-id="788d1-127">Da mesma forma, agora é possível ter acesso somente leitura a coleções usando uma propriedade pública digitada como `IReadOnlyCollection<T>`, com o apoio de um membro de campo privado para a coleção (como uma `List<T>`) na entidade, que se baseia no EF para persistência.</span><span class="sxs-lookup"><span data-stu-id="788d1-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="788d1-128">As versões anteriores do Entity Framework exigiam que as propriedades da coleção fossem compatíveis com `ICollection<T>`, o que significava que qualquer desenvolvedor que usasse uma classe da entidade pai poderia adicionar ou remover itens por meio de suas coleções de propriedade.</span><span class="sxs-lookup"><span data-stu-id="788d1-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="788d1-129">Essa possibilidade seria em relação aos padrões recomendados no DDD.</span><span class="sxs-lookup"><span data-stu-id="788d1-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="788d1-130">É possível usar uma coleção privada ao expor um objeto `IReadOnlyCollection<T>` somente leitura, como é mostrado no exemplo de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="788d1-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="788d1-131">Observe que a propriedade `OrderItems` somente pode ser acessada como somente leitura usando `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="788d1-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="788d1-132">Esse tipo é somente leitura, portanto, ele está protegido contra as atualizações externas regulares.</span><span class="sxs-lookup"><span data-stu-id="788d1-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="788d1-133">O EF Core fornece uma maneira de mapear o modelo de domínio para o banco de dados físico sem "contaminar" o modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="788d1-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="788d1-134">Trata-se de puro código POCO do .NET, pois a ação de mapeamento é implementada na camada de persistência.</span><span class="sxs-lookup"><span data-stu-id="788d1-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="788d1-135">Nessa ação de mapeamento, você precisa configurar o mapeamento dos campos para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="788d1-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="788d1-136">No exemplo a seguir do método `OnModelCreating` de `OrderingContext` e da classe `OrderEntityTypeConfiguration`, a chamada para `SetPropertyAccessMode` informa ao EF Core para acessar a propriedade `OrderItems` por meio de seu campo.</span><span class="sxs-lookup"><span data-stu-id="788d1-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="788d1-137">Ao usar campos em vez de propriedades, a entidade `OrderItem` será persistida como se tivesse uma propriedade `List<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="788d1-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="788d1-138">No entanto, ela expõe um único acessador, o método `AddOrderItem`, para adicionar novos itens ao pedido.</span><span class="sxs-lookup"><span data-stu-id="788d1-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="788d1-139">Como resultado, o comportamento e os dados ficarão vinculados e serão consistentes em todos os códigos de aplicativo que usarem o modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="788d1-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="788d1-140">Implementar repositórios personalizados com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="788d1-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="788d1-141">No nível da implementação, um repositório é simplesmente uma classe com o código de persistência de dados, coordenada por uma unidade de trabalho (DBContext no EF Core) ao executar atualizações, como mostra a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="788d1-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="788d1-142">Observe que a interface IBuyerRepository vem da camada de modelo de domínio como um contrato.</span><span class="sxs-lookup"><span data-stu-id="788d1-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="788d1-143">No entanto, a implementação do repositório é feita na camada de persistência e de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="788d1-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="788d1-144">O DbContext do EF é fornecido pelo construtor por meio de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="788d1-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="788d1-145">Ele é compartilhado entre vários repositórios no mesmo escopo de solicitação HTTP, graças ao seu tempo de vida padrão (`ServiceLifetime.Scoped`) no contêiner de IoC (inversão de controle) (que também pode ser definido explicitamente com `services.AddDbContext<>`).</span><span class="sxs-lookup"><span data-stu-id="788d1-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="788d1-146">Métodos a serem implementados em um repositório (atualizações ou transações em comparação com consultas)</span><span class="sxs-lookup"><span data-stu-id="788d1-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="788d1-147">Em cada classe de repositório, você deve colocar os métodos de persistência que atualizam o estado das entidades contidas na agregação relacionada.</span><span class="sxs-lookup"><span data-stu-id="788d1-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="788d1-148">Lembre-se de que há uma relação um-para-um entre uma agregação e seu repositório relacionado.</span><span class="sxs-lookup"><span data-stu-id="788d1-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="788d1-149">Leve em consideração que um objeto de entidade de raiz de agregação pode ter entidades filhas inseridas no grafo do EF.</span><span class="sxs-lookup"><span data-stu-id="788d1-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="788d1-150">Por exemplo, um comprador pode ter vários métodos de pagamento como entidades filhas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="788d1-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="788d1-151">Como a abordagem para o microsserviço de pedidos no eShopOnContainers também se baseia em CQS/CQRS, a maioria das consultas não são implementadas em repositórios personalizados.</span><span class="sxs-lookup"><span data-stu-id="788d1-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="788d1-152">Os desenvolvedores têm a liberdade de criar as consultas e junções que precisam para a camada de apresentação sem as restrições impostas pelas agregações, pelos repositórios personalizados por agregação e pelo DDD em geral.</span><span class="sxs-lookup"><span data-stu-id="788d1-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="788d1-153">A maioria dos repositórios personalizados sugeridos por este guia tem vários métodos de atualização ou transacionais, mas apenas os métodos de consulta necessários para fazer com que os dados sejam atualizados.</span><span class="sxs-lookup"><span data-stu-id="788d1-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="788d1-154">Por exemplo, o repositório BuyerRepository implementa um método FindAsync, porque o aplicativo precisa saber se um comprador específico existe antes de criar um novo comprador relacionado ao pedido.</span><span class="sxs-lookup"><span data-stu-id="788d1-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="788d1-155">No entanto, os métodos de consulta reais para obter os dados a serem enviados à camada de apresentação ou aos aplicativos clientes são implementados, conforme mencionado, nas consultas de CQRS baseadas em consultas flexíveis usando Dapper.</span><span class="sxs-lookup"><span data-stu-id="788d1-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="788d1-156">Usando um repositório personalizado em vez de usar o DbContext EF diretamente</span><span class="sxs-lookup"><span data-stu-id="788d1-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="788d1-157">A classe DbContext do Entity Framework baseia-se nos padrões de unidade de trabalho e de repositório e pode ser usada diretamente no código, como em um controlador MVC do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="788d1-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="788d1-158">Essa é a maneira de criar o código mais simples possível, como o microsserviço de catálogo de CRUD (criar, ler, atualizar e excluir) no eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="788d1-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="788d1-159">Nos casos em que você deseja o código mais simples possível, é possível usar diretamente a classe DbContext, como muitos desenvolvedores fazem.</span><span class="sxs-lookup"><span data-stu-id="788d1-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="788d1-160">No entanto, a implementação de repositórios personalizados oferece vários benefícios ao implementar microsserviços ou aplicativos mais complexos.</span><span class="sxs-lookup"><span data-stu-id="788d1-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="788d1-161">Os padrões de unidade de trabalho e de repositório são indicados para encapsular a camada de persistência da infraestrutura para que ela fique desacoplada das camadas de aplicativo e de modelo de domínio.</span><span class="sxs-lookup"><span data-stu-id="788d1-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="788d1-162">A implementação desses padrões pode facilitar o uso de repositórios fictícios para simulação de acesso ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="788d1-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="788d1-163">Na Figura 7-18, veja as diferenças entre não usar repositórios (usando diretamente o DbContext do EF) e usar repositórios, o que facilita a simulação desses repositórios.</span><span class="sxs-lookup"><span data-stu-id="788d1-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![Diagrama mostrando os componentes e o fluxo de dados nos dois repositórios.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="788d1-165">**Figura 7-18**.</span><span class="sxs-lookup"><span data-stu-id="788d1-165">**Figure 7-18**.</span></span> <span data-ttu-id="788d1-166">Usando repositórios personalizados em vez de um DbContext simples</span><span class="sxs-lookup"><span data-stu-id="788d1-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="788d1-167">A Figura 7-18 mostra que o uso de um repositório personalizado adiciona uma camada de abstração que pode ser usada para facilitar o teste zombando do repositório.</span><span class="sxs-lookup"><span data-stu-id="788d1-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="788d1-168">Existem várias alternativas para simulação.</span><span class="sxs-lookup"><span data-stu-id="788d1-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="788d1-169">Você pode simular apenas repositórios ou simular toda a unidade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="788d1-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="788d1-170">Geralmente, simular apenas os repositórios já é suficiente e a complexidade de abstrair e simular toda a unidade de trabalho, normalmente, não é necessária.</span><span class="sxs-lookup"><span data-stu-id="788d1-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="788d1-171">Mais adiante, quando nos concentramos na camada de aplicativo, você verá como funciona a injeção de dependência no ASP.NET Core e como ela é implementada ao usar repositórios.</span><span class="sxs-lookup"><span data-stu-id="788d1-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="788d1-172">Em resumo, os repositórios personalizados permitem que você teste o código mais facilmente com testes de unidade que não são afetados pelo estado da camada de dados.</span><span class="sxs-lookup"><span data-stu-id="788d1-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="788d1-173">Se você executar testes que também acessem o banco de dados real por meio do Entity Framework, eles não serão testes de unidade, mas sim testes de integração, que são muito mais lentos.</span><span class="sxs-lookup"><span data-stu-id="788d1-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="788d1-174">Se estivesse usando o DbContext diretamente, você precisaria simulá-lo ou executar testes de unidade usando um SQL Server na memória, com os dados previsíveis para testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="788d1-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="788d1-175">Mas simular o DbContext ou controlar dados falsos requer mais trabalho do que a simulação no nível do repositório.</span><span class="sxs-lookup"><span data-stu-id="788d1-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="788d1-176">Obviamente, sempre é possível testar os controladores MVC.</span><span class="sxs-lookup"><span data-stu-id="788d1-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="788d1-177">Tempo de vida da instância de DbContext e de IUnitOfWork do EF no contêiner de IoC</span><span class="sxs-lookup"><span data-stu-id="788d1-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="788d1-178">O objeto `DbContext` (exposto como um objeto `IUnitOfWork`) deve ser compartilhado entre vários repositórios dentro do mesmo escopo de solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="788d1-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="788d1-179">Por exemplo, isso é verdadeiro quando a operação que está sendo executada precisa lidar com várias agregações ou simplesmente porque você está usando várias instâncias do repositório.</span><span class="sxs-lookup"><span data-stu-id="788d1-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="788d1-180">Também é importante mencionar que a interface `IUnitOfWork` faz parte da camada de domínio, ela não é um tipo do EF Core.</span><span class="sxs-lookup"><span data-stu-id="788d1-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="788d1-181">Para isso, o tempo de vida de serviço da instância do objeto `DbContext` precisa ser definido como ServiceLifetime.Scoped.</span><span class="sxs-lookup"><span data-stu-id="788d1-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="788d1-182">Este é o tempo de vida padrão ao registrar um `DbContext` com `services.AddDbContext` no contêiner de IoC (inversão de controle) do método ConfigureServices do arquivo `Startup.cs`, no projeto de API Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="788d1-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="788d1-183">O código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="788d1-183">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="788d1-184">O modo de criação de instância do DbContext não deve ser configurado como ServiceLifetime.Transient ou ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="788d1-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="788d1-185">O tempo de vida da instância de repositório no contêiner de IoC</span><span class="sxs-lookup"><span data-stu-id="788d1-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="788d1-186">Da mesma forma, o tempo de vida do repositório normalmente deve ser definido como no escopo (InstancePerLifetimeScope no Autofac).</span><span class="sxs-lookup"><span data-stu-id="788d1-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="788d1-187">Ele também pode ser transitório (InstancePerDependency no Autofac), mas o serviço será mais eficiente em relação à memória ao usar o tempo de vida no escopo.</span><span class="sxs-lookup"><span data-stu-id="788d1-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="788d1-188">Observe que usar o tempo de vida singleton para o repositório poderá causar problemas graves de simultaneidade quando o DbContext estiver definido como tempo de vida no escopo (InstancePerLifetimeScope) (os tempos de vida padrão de um DBContext).</span><span class="sxs-lookup"><span data-stu-id="788d1-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="788d1-189">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="788d1-189">Additional resources</span></span>

- <span data-ttu-id="788d1-190">**Implementação do Repositório e da Unidade de Padrões de Trabalho em um aplicativo MVC ASP.NET** </span><span class="sxs-lookup"><span data-stu-id="788d1-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="788d1-191">**Jonathan Allen. Estratégias de implementação para o padrão de repositório com quadro de entidades, dapper e cadeia** </span><span class="sxs-lookup"><span data-stu-id="788d1-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="788d1-192">**Cesar de la Torre. Comparando ASP.NET vida útil do serviço de contêineres Core IoC com os escopos de instância de contêiner Autofac IoC** </span><span class="sxs-lookup"><span data-stu-id="788d1-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="788d1-193">Mapeamento de tabela</span><span class="sxs-lookup"><span data-stu-id="788d1-193">Table mapping</span></span>

<span data-ttu-id="788d1-194">O mapeamento de tabela identifica os dados de tabela a serem consultados e salvos no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="788d1-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="788d1-195">Você já viu como as entidades de domínio (por exemplo, um domínio de produto ou de pedido) podem ser usadas para gerar um esquema de banco de dados relacionado.</span><span class="sxs-lookup"><span data-stu-id="788d1-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="788d1-196">O EF foi projetado rigidamente de acordo com o conceito de *convenções*.</span><span class="sxs-lookup"><span data-stu-id="788d1-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="788d1-197">As convenções abrangem perguntas como "Qual será o nome de uma tabela?"</span><span class="sxs-lookup"><span data-stu-id="788d1-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="788d1-198">ou "Qual propriedade é a chave primária?"</span><span class="sxs-lookup"><span data-stu-id="788d1-198">or “What property is the primary key?”</span></span> <span data-ttu-id="788d1-199">As convenções normalmente se baseiam nos nomes convencionais. Por exemplo, é comum que a chave primária seja uma propriedade que termine com Id.</span><span class="sxs-lookup"><span data-stu-id="788d1-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="788d1-200">Por convenção, cada entidade será configurada para ser mapeada para uma tabela com o mesmo nome que a propriedade `DbSet<TEntity>` que expõe a entidade no contexto derivado.</span><span class="sxs-lookup"><span data-stu-id="788d1-200">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="788d1-201">Se nenhum valor de `DbSet<TEntity>` for fornecido para a entidade especificada, o nome da classe será usado.</span><span class="sxs-lookup"><span data-stu-id="788d1-201">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="788d1-202">Anotações de dados em comparação com a API fluente</span><span class="sxs-lookup"><span data-stu-id="788d1-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="788d1-203">Existem muitas convenções do EF Core adicionais e a maioria delas pode ser alterada usando anotações de dados ou a API fluente, implementada no método OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="788d1-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="788d1-204">As anotações de dados devem ser usadas nas próprias classes de modelo de entidade, o que é uma maneira mais invasiva do ponto de vista de DDD.</span><span class="sxs-lookup"><span data-stu-id="788d1-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="788d1-205">Isso ocorre porque você está contaminando o modelo com anotações de dados relacionadas ao banco de dados de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="788d1-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="788d1-206">Por outro lado, a API fluente é uma maneira conveniente de alterar a maioria das convenções e dos mapeamentos dentro da camada de infraestrutura de persistência de dados, para que o modelo de entidade fique limpo e desacoplado da infraestrutura de persistência.</span><span class="sxs-lookup"><span data-stu-id="788d1-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="788d1-207">API fluente e o método OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="788d1-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="788d1-208">Conforme mencionado, para alterar as convenções e os mapeamentos, você pode usar o método OnModelCreating na classe DbContext.</span><span class="sxs-lookup"><span data-stu-id="788d1-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="788d1-209">O microsserviço de pedidos no eShopOnContainers implementa o mapeamento e configuração explícitos, quando necessário, conforme é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="788d1-209">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

        orderConfiguration.HasKey(o => o.Id);

        orderConfiguration.Ignore(b => b.DomainEvents);

        orderConfiguration.Property(o => o.Id)
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

<span data-ttu-id="788d1-210">Você pode definir todos os mapeamentos `OnModelCreating` de API fluentes dentro do mesmo método, mas é aconselhável particionar esse código e ter várias classes de configuração, uma por entidade, como mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="788d1-210">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="788d1-211">Especialmente para modelos grandes, é aconselhável ter classes de configuração separadas para configurar diferentes tipos de entidades.</span><span class="sxs-lookup"><span data-stu-id="788d1-211">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="788d1-212">O código no exemplo mostra algumas declarações e mapeamentos explícitos.</span><span class="sxs-lookup"><span data-stu-id="788d1-212">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="788d1-213">No entanto, as convenções do EF Core fazem muitos desses mapeamentos automaticamente, portanto, o código real necessário para o seu caso poderá ser menor.</span><span class="sxs-lookup"><span data-stu-id="788d1-213">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="788d1-214">O algoritmo Hi/Lo no EF Core</span><span class="sxs-lookup"><span data-stu-id="788d1-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="788d1-215">Um aspecto interessante de código no exemplo anterior é que ele usa o [algoritmo Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) como a estratégia de geração de chave.</span><span class="sxs-lookup"><span data-stu-id="788d1-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="788d1-216">O algoritmo Hi/Lo é útil quando você precisa de chaves exclusivas antes de confirmar as alterações.</span><span class="sxs-lookup"><span data-stu-id="788d1-216">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="788d1-217">Em resumo, o algoritmo Hi-Lo atribui identificadores exclusivos às linhas da tabela, embora ele não dependa de armazenar a linha no banco de dados imediatamente.</span><span class="sxs-lookup"><span data-stu-id="788d1-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="788d1-218">Isso permite começar a usar os identificadores imediatamente, como acontece com as IDs de banco de dados sequenciais regulares.</span><span class="sxs-lookup"><span data-stu-id="788d1-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="788d1-219">O algoritmo Hi/Lo descreve um mecanismo para obter um lote de IDs exclusivas de uma sequência de banco de dados relacionado.</span><span class="sxs-lookup"><span data-stu-id="788d1-219">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="788d1-220">Essas IDs são seguras usar porque o banco de dados garante a exclusividade, portanto, não haverá nenhuma colisão entre usuários.</span><span class="sxs-lookup"><span data-stu-id="788d1-220">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="788d1-221">Esse algoritmo é interessante por estes motivos:</span><span class="sxs-lookup"><span data-stu-id="788d1-221">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="788d1-222">Ele não interrompe o padrão de unidade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="788d1-222">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="788d1-223">Ele obtém as IDs da sequência em lotes, para minimizar as viagens de ida e para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="788d1-223">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="788d1-224">Ele gera um identificador legível por pessoas, ao contrário das técnicas que usam GUIDs.</span><span class="sxs-lookup"><span data-stu-id="788d1-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="788d1-225">O EF Core suporta `UseHiLo` [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) com o método, como mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="788d1-225">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="788d1-226">Mapear campos em vez de propriedades</span><span class="sxs-lookup"><span data-stu-id="788d1-226">Map fields instead of properties</span></span>

<span data-ttu-id="788d1-227">Com esse recurso, disponível desde o EF Core 1.1, você pode mapear colunas para campos diretamente.</span><span class="sxs-lookup"><span data-stu-id="788d1-227">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="788d1-228">É possível não usar as propriedades na classe de entidade e apenas mapear as colunas de uma tabela para os campos.</span><span class="sxs-lookup"><span data-stu-id="788d1-228">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="788d1-229">Um caso de uso comum para isso seria os campos privados de algum estado interno que não precisam ser acessados de fora da entidade.</span><span class="sxs-lookup"><span data-stu-id="788d1-229">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="788d1-230">Você pode fazer isso com campos únicos ou também com coleções, como um campo `List<>`.</span><span class="sxs-lookup"><span data-stu-id="788d1-230">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="788d1-231">Esse ponto já foi mencionado quando discutimos a modelagem das classes de modelo de domínio, mas aqui você pode ver como esse mapeamento é realizado com a configuração `PropertyAccessMode.Field` realçada no código anterior.</span><span class="sxs-lookup"><span data-stu-id="788d1-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="788d1-232">Usar propriedades de sombra no EF Core, ocultas no nível da infraestrutura</span><span class="sxs-lookup"><span data-stu-id="788d1-232">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="788d1-233">As propriedades de sombra no EF Core são propriedades que não existem no modelo de classe de entidade.</span><span class="sxs-lookup"><span data-stu-id="788d1-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="788d1-234">Os valores e os estados dessas propriedades são mantidos unicamente na classe [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) no nível da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="788d1-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="788d1-235">Implementar o padrão de especificação de consulta</span><span class="sxs-lookup"><span data-stu-id="788d1-235">Implement the Query Specification pattern</span></span>

<span data-ttu-id="788d1-236">Conforme já foi apresentado na seção sobre design, o padrão de especificação de consulta é um padrão de design orientado por domínio projetado para ser o local em que você pode colocar a definição de uma consulta com uma lógica opcional de classificação e paginação.</span><span class="sxs-lookup"><span data-stu-id="788d1-236">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="788d1-237">O padrão de especificação de consulta define uma consulta em um objeto.</span><span class="sxs-lookup"><span data-stu-id="788d1-237">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="788d1-238">Por exemplo, para encapsular uma consulta paginada que procura por alguns produtos, você poderia criar uma especificação PagedProduct que usasse os parâmetros de entrada necessários (pageNumber, pageSize, filtro, etc.).</span><span class="sxs-lookup"><span data-stu-id="788d1-238">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="788d1-239">Então, qualquer método de repositório [geralmente uma sobrecarga List()] aceitaria uma IQuerySpecification e executaria a consulta esperada com base nessa especificação.</span><span class="sxs-lookup"><span data-stu-id="788d1-239">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="788d1-240">Um exemplo de uma interface de especificação genérica é o código a seguir de [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="788d1-240">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="788d1-241">Assim, a implementação de uma classe base de especificação genérica seria a seguinte.</span><span class="sxs-lookup"><span data-stu-id="788d1-241">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="788d1-242">A seguinte especificação carrega uma única entidade de cesta de compras de acordo com a ID da cesta de compras ou com a ID do comprador ao qual a cesta de compras pertence.</span><span class="sxs-lookup"><span data-stu-id="788d1-242">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="788d1-243">Isso fará o [carregamento adiantado](https://docs.microsoft.com/ef/core/querying/related-data) da coleção de itens do carrinho de compras.</span><span class="sxs-lookup"><span data-stu-id="788d1-243">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }

    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="788d1-244">E, finalmente, veja abaixo como um repositório do EF genérico pode usar uma especificação desse tipo para filtrar e fazer o carregamento adiantado dos dados relacionados a um determinado tipo de entidade T.</span><span class="sxs-lookup"><span data-stu-id="788d1-244">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

<span data-ttu-id="788d1-245">Além de encapsular a lógica de filtragem, a especificação pode especificar a forma dos dados a serem retornados, incluindo quais propriedades devem ser populadas.</span><span class="sxs-lookup"><span data-stu-id="788d1-245">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="788d1-246">Embora não recomendemos `IQueryable` voltar de um repositório, é perfeitamente bom usá-los dentro do repositório para construir um conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="788d1-246">Although we don’t recommend to return `IQueryable` from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="788d1-247">Você pode ver essa abordagem usada no `IQueryable` método Lista acima, que usa expressões intermediárias para construir a lista de inclui das ofertas antes de executar a consulta com os critérios da especificação na última linha.</span><span class="sxs-lookup"><span data-stu-id="788d1-247">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="788d1-248">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="788d1-248">Additional resources</span></span>

- <span data-ttu-id="788d1-249">**Mapeamento de tabelas** </span><span class="sxs-lookup"><span data-stu-id="788d1-249">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="788d1-250">**Use hilo para gerar chaves com o Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="788d1-250">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="788d1-251">**Campos de Apoio** </span><span class="sxs-lookup"><span data-stu-id="788d1-251">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="788d1-252">**Steve Smith. Coleções encapsuladas no Núcleo-Quadro de Entidades** </span><span class="sxs-lookup"><span data-stu-id="788d1-252">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="788d1-253">**Propriedades da sombra** </span><span class="sxs-lookup"><span data-stu-id="788d1-253">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="788d1-254">**O padrão de especificação** </span><span class="sxs-lookup"><span data-stu-id="788d1-254">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="788d1-255">[Próximo](infrastructure-persistence-layer-design.md)
> [anterior](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="788d1-255">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
