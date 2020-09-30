---
title: Injeção de dependência no .NET
description: Saiba como o .NET implementa a injeção de dependência e como usá-la.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: overview
ms.openlocfilehash: b986f414dcc0e81578e6cf57304f6e5c31578e88
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247881"
---
# <a name="dependency-injection-in-net"></a><span data-ttu-id="dcfbc-103">Injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="dcfbc-103">Dependency injection in .NET</span></span>

<span data-ttu-id="dcfbc-104">O .NET dá suporte ao padrão de design de software de injeção de dependência (DI), que é uma técnica para obter [inversão de controle (IOC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) entre classes e suas dependências.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-104">.NET supports the dependency injection (DI) software design pattern, which is a technique for achieving [Inversion of Control (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) between classes and their dependencies.</span></span> <span data-ttu-id="dcfbc-105">A injeção de dependência no .NET é um [cidadão de primeira classe](https://en.wikipedia.org/wiki/First-class_citizen), juntamente com configuração, registro em log e o padrão de opções.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-105">Dependency injection in .NET is a [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen), along with configuration, logging, and the options pattern.</span></span>

<span data-ttu-id="dcfbc-106">Uma *dependência* é um objeto do qual outro objeto depende.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-106">A *dependency* is an object that another object depends on.</span></span> <span data-ttu-id="dcfbc-107">Examine a seguinte `MessageWriter` classe com um `Write` método de que outras classes dependem:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-107">Examine the following `MessageWriter` class with a `Write` method that other classes depend on:</span></span>

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

<span data-ttu-id="dcfbc-108">Uma classe pode criar uma instância da `MessageWriter` classe para fazer uso de seu `Write` método.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-108">A class can create an instance of the `MessageWriter` class to make use of its `Write` method.</span></span> <span data-ttu-id="dcfbc-109">No exemplo a seguir, a `MessageWriter` classe é uma dependência da `Worker` classe:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-109">In the following example, the `MessageWriter` class is a dependency of the `Worker` class:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="dcfbc-110">A classe cria e depende diretamente da `MessageWriter` classe.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-110">The class creates and directly depends on the `MessageWriter` class.</span></span> <span data-ttu-id="dcfbc-111">As dependências embutidas em código, como no exemplo anterior, são problemáticas e devem ser evitadas pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-111">Hard-coded dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:</span></span>

- <span data-ttu-id="dcfbc-112">Para substituir `MessageWriter` por uma implementação diferente, a `MessageService` classe deve ser modificada.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-112">To replace `MessageWriter` with a different implementation, the `MessageService` class must be modified.</span></span>
- <span data-ttu-id="dcfbc-113">Se `MessageWriter` tiver dependências, elas também deverão ser configuradas pela `MessageService` classe.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-113">If `MessageWriter` has dependencies, they must also be configured by the `MessageService` class.</span></span> <span data-ttu-id="dcfbc-114">Em um projeto grande com várias classes dependendo da `MessageWriter`, o código de configuração fica pulverizado por todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-114">In a large project with multiple classes depending on `MessageWriter`, the configuration code becomes scattered across the app.</span></span>
- <span data-ttu-id="dcfbc-115">É difícil testar a unidade dessa implementação.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-115">This implementation is difficult to unit test.</span></span> <span data-ttu-id="dcfbc-116">O aplicativo deve usar uma simulação ou stub da classe `MessageWriter`, o que não é possível com essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-116">The app should use a mock or stub `MessageWriter` class, which isn't possible with this approach.</span></span>

<span data-ttu-id="dcfbc-117">Injeção de dependência trata desses problemas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-117">Dependency injection addresses these problems through:</span></span>

- <span data-ttu-id="dcfbc-118">O uso de uma interface ou classe base para abstrair a implementação da dependência.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-118">The use of an interface or base class to abstract the dependency implementation.</span></span>
- <span data-ttu-id="dcfbc-119">Registrando a dependência em um contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-119">Registration of the dependency in a service container.</span></span> <span data-ttu-id="dcfbc-120">O .NET fornece um contêiner de serviço interno, <xref:System.IServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-120">.NET provides a built-in service container, <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="dcfbc-121">Normalmente, os serviços são registrados na inicialização do aplicativo e anexados a um <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-121">Services are typically registered at the app's start-up, and appended to an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="dcfbc-122">Depois que todos os serviços forem adicionados, você usará <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> para criar o contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-122">Once all services are added, you use <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> to create the service container.</span></span>
- <span data-ttu-id="dcfbc-123">*Injeção* do serviço no construtor da classe na qual ele é usado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-123">*Injection* of the service into the constructor of the class where it's used.</span></span> <span data-ttu-id="dcfbc-124">A estrutura assume a responsabilidade de criar uma instância da dependência e de descartá-la quando não for mais necessária.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-124">The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.</span></span>

<span data-ttu-id="dcfbc-125">Por exemplo, a `IMessageWriter` interface define o `Write` método:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-125">As an example, the `IMessageWriter` interface defines the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

<span data-ttu-id="dcfbc-126">Essa interface é implementada por um tipo concreto, `MessageWriter`:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-126">This interface is implemented by a concrete type, `MessageWriter`:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

<span data-ttu-id="dcfbc-127">O código de exemplo registra o `IMessageWriter` serviço com o tipo concreto `MessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-127">The sample code registers the `IMessageWriter` service with the concrete type `MessageWriter`.</span></span> <span data-ttu-id="dcfbc-128">O <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> método registra o serviço com um tempo de vida de escopo, o tempo de vida de uma única solicitação.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-128">The <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> method registers the service with a scoped lifetime, the lifetime of a single request.</span></span> <span data-ttu-id="dcfbc-129">Descreveremos posteriormente neste tópico os [tempos de vida do serviço](#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="dcfbc-129">[Service lifetimes](#service-lifetimes) are described later in this topic.</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

<span data-ttu-id="dcfbc-130">No aplicativo de exemplo, o `IMessageWriter` serviço é solicitado e usado para chamar o `Write` método:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-130">In the sample app, the `IMessageWriter` service is requested and used to call the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

<span data-ttu-id="dcfbc-131">Usando o padrão DI, o serviço de trabalho:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-131">By using the DI pattern, the worker service:</span></span>

- <span data-ttu-id="dcfbc-132">Não usa o tipo concreto `MessageWriter` , apenas a `IMessageWriter` interface que o implementa.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-132">Doesn't use the concrete type `MessageWriter`, only the `IMessageWriter` interface that implements it.</span></span> <span data-ttu-id="dcfbc-133">Isso facilita a alteração da implementação que o controlador usa sem modificar o controlador.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-133">That makes it easy to change the implementation that the controller uses without modifying the controller.</span></span>
- <span data-ttu-id="dcfbc-134">Não cria uma instância do `MessageWriter` , ela é criada pelo contêiner de di.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-134">Doesn't create an instance of `MessageWriter`, it's created by the DI container.</span></span>

<span data-ttu-id="dcfbc-135">A implementação da `IMessageWriter` interface pode ser aprimorada usando a API de registro em log interna:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-135">The implementation of the `IMessageWriter` interface can be improved by using the built-in logging API:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

<span data-ttu-id="dcfbc-136">O `ConfigureServices` método atualizado registra a nova `IMessageWriter` implementação:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-136">The updated `ConfigureServices` method registers the new `IMessageWriter` implementation:</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

<span data-ttu-id="dcfbc-137">`LoggingMessageWriter` depende de <xref:Microsoft.Extensions.Logging.ILogger%601> , que ele solicita no construtor.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-137">`LoggingMessageWriter` depends on <xref:Microsoft.Extensions.Logging.ILogger%601>, which it requests in the constructor.</span></span> <span data-ttu-id="dcfbc-138">`ILogger<TCategoryName>` é um [serviço fornecido pelo Framework](#framework-provided-services).</span><span class="sxs-lookup"><span data-stu-id="dcfbc-138">`ILogger<TCategoryName>` is a [framework-provided service](#framework-provided-services).</span></span>

<span data-ttu-id="dcfbc-139">Não é incomum usar a injeção de dependência de uma maneira encadeada.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-139">It's not unusual to use dependency injection in a chained fashion.</span></span> <span data-ttu-id="dcfbc-140">Por sua vez, cada dependência solicitada solicita suas próprias dependências.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-140">Each requested dependency in turn requests its own dependencies.</span></span> <span data-ttu-id="dcfbc-141">O contêiner resolve as dependências no grafo e retorna o serviço totalmente resolvido.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-141">The container resolves the dependencies in the graph and returns the fully resolved service.</span></span> <span data-ttu-id="dcfbc-142">O conjunto de dependências que precisa ser resolvido normalmente é chamado de *árvore de dependência*, *grafo de dependência* ou *grafo de objeto*.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-142">The collective set of dependencies that must be resolved is typically referred to as a *dependency tree*, *dependency graph*, or *object graph*.</span></span>

<span data-ttu-id="dcfbc-143">O contêiner resolve aproveitando `ILogger<TCategoryName>` os [tipos abertos (genéricos)](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminando a necessidade de registrar cada [tipo construído (genérico)](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="dcfbc-143">The container resolves `ILogger<TCategoryName>` by taking advantage of [(generic) open types](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminating the need to register every [(generic) constructed type](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span></span>

<span data-ttu-id="dcfbc-144">Na terminologia de injeção de dependência, um serviço:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-144">In dependency injection terminology, a service:</span></span>

- <span data-ttu-id="dcfbc-145">Normalmente é um objeto que fornece um serviço para outros objetos, como o `IMessageWriter` serviço.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-145">Is typically an object that provides a service to other objects, such as the `IMessageWriter` service.</span></span>
- <span data-ttu-id="dcfbc-146">O não está relacionado a um serviço Web, embora o serviço possa usar um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-146">Is not related to a web service, although the service may use a web service.</span></span>

<span data-ttu-id="dcfbc-147">A estrutura fornece um sistema de registro em log robusto.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-147">The framework provides a robust logging system.</span></span> <span data-ttu-id="dcfbc-148">As `IMessageWriter` implementações mostradas nos exemplos anteriores foram escritas para demonstrar a di básica, não para implementar o registro em log.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-148">The `IMessageWriter` implementations shown in the preceding examples were written to demonstrate basic DI, not to implement logging.</span></span> <span data-ttu-id="dcfbc-149">A maioria dos aplicativos não deve precisar gravar agentes.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-149">Most apps shouldn't need to write loggers.</span></span> <span data-ttu-id="dcfbc-150">O código a seguir demonstra como usar o log padrão, que requer que apenas o seja `Worker` registrado no `ConfigureServices` como um serviço hospedado <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> :</span><span class="sxs-lookup"><span data-stu-id="dcfbc-150">The following code demonstrates using the default logging, which only requires the `Worker` to be registered in `ConfigureServices` as a hosted service <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="dcfbc-151">Usando o código anterior, não há necessidade de atualizar `ConfigureServices` , porque o registro em log é fornecido pela estrutura.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-151">Using the preceding code, there is no need to update `ConfigureServices`, because logging is provided by the framework.</span></span>

## <a name="register-groups-of-services-with-extension-methods"></a><span data-ttu-id="dcfbc-152">Registrar grupos de serviços com métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="dcfbc-152">Register groups of services with extension methods</span></span>

<span data-ttu-id="dcfbc-153">O Microsoft Extensions usa uma Convenção para registrar um grupo de serviços relacionados.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-153">Microsoft Extensions uses a convention for registering a group of related services.</span></span> <span data-ttu-id="dcfbc-154">A Convenção é usar um método de `Add{GROUP_NAME}` extensão único para registrar todos os serviços exigidos por um recurso de estrutura.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-154">The convention is to use a single `Add{GROUP_NAME}` extension method to register all of the services required by a framework feature.</span></span> <span data-ttu-id="dcfbc-155">Por exemplo, o <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> método de extensão registra todos os serviços necessários para usar as opções.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-155">For example, the <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> extension method registers all of the services required for using options.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="dcfbc-156">Serviços fornecidos pela estrutura</span><span class="sxs-lookup"><span data-stu-id="dcfbc-156">Framework-provided services</span></span>

<span data-ttu-id="dcfbc-157">O `ConfigureServices` método registra os serviços que o aplicativo usa, incluindo recursos de plataforma.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-157">The `ConfigureServices` method registers services that the app uses, including platform features.</span></span> <span data-ttu-id="dcfbc-158">Inicialmente, o `IServiceCollection` fornecido para o `ConfigureServices` tem serviços definidos pela estrutura, dependendo de [como o host foi configurado](generic-host.md#host-configuration).</span><span class="sxs-lookup"><span data-stu-id="dcfbc-158">Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on [how the host was configured](generic-host.md#host-configuration).</span></span> <span data-ttu-id="dcfbc-159">Para aplicativos baseados nos modelos .NET, a estrutura registra centenas de serviços.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-159">For apps based on the .NET templates, the framework registers hundreds of services.</span></span>

<span data-ttu-id="dcfbc-160">A tabela a seguir lista uma pequena amostra desses serviços registrados no Framework:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-160">The following table lists a small sample of these framework-registered services:</span></span>

| <span data-ttu-id="dcfbc-161">Tipo de Serviço</span><span class="sxs-lookup"><span data-stu-id="dcfbc-161">Service Type</span></span>                                                                       | <span data-ttu-id="dcfbc-162">Tempo de vida</span><span class="sxs-lookup"><span data-stu-id="dcfbc-162">Lifetime</span></span>  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | <span data-ttu-id="dcfbc-163">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-163">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | <span data-ttu-id="dcfbc-164">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-164">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | <span data-ttu-id="dcfbc-165">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-165">Singleton</span></span> |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | <span data-ttu-id="dcfbc-166">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-166">Singleton</span></span> |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | <span data-ttu-id="dcfbc-167">Transitório</span><span class="sxs-lookup"><span data-stu-id="dcfbc-167">Transient</span></span> |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | <span data-ttu-id="dcfbc-168">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-168">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | <span data-ttu-id="dcfbc-169">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-169">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | <span data-ttu-id="dcfbc-170">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-170">Singleton</span></span> |

## <a name="service-lifetimes"></a><span data-ttu-id="dcfbc-171">Tempos de vida do serviço</span><span class="sxs-lookup"><span data-stu-id="dcfbc-171">Service lifetimes</span></span>

<span data-ttu-id="dcfbc-172">Os serviços podem ser registrados com um dos seguintes tempos de vida:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-172">Services can be registered with one of the following lifetimes:</span></span>

- <span data-ttu-id="dcfbc-173">Transitório</span><span class="sxs-lookup"><span data-stu-id="dcfbc-173">Transient</span></span>
- <span data-ttu-id="dcfbc-174">Com escopo</span><span class="sxs-lookup"><span data-stu-id="dcfbc-174">Scoped</span></span>
- <span data-ttu-id="dcfbc-175">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-175">Singleton</span></span>

<span data-ttu-id="dcfbc-176">As seções a seguir descrevem cada um dos tempos de vida anteriores.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-176">The following sections describe each of the preceding lifetimes.</span></span> <span data-ttu-id="dcfbc-177">Escolha um tempo de vida apropriado para cada serviço registrado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-177">Choose an appropriate lifetime for each registered service.</span></span>

### <a name="transient"></a><span data-ttu-id="dcfbc-178">Transitório</span><span class="sxs-lookup"><span data-stu-id="dcfbc-178">Transient</span></span>

<span data-ttu-id="dcfbc-179">Serviços temporários de tempo de vida são criados cada vez que são solicitados pelo contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-179">Transient lifetime services are created each time they're requested from the service container.</span></span> <span data-ttu-id="dcfbc-180">Esse tempo de vida funciona melhor para serviços leves e sem estado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-180">This lifetime works best for lightweight, stateless services.</span></span> <span data-ttu-id="dcfbc-181">Registre serviços transitórios com <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-181">Register transient services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span></span>

<span data-ttu-id="dcfbc-182">Em aplicativos que processam solicitações, os serviços transitórios são descartados no final da solicitação.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-182">In apps that process requests, transient services are disposed at the end of the request.</span></span>

### <a name="scoped"></a><span data-ttu-id="dcfbc-183">Com escopo</span><span class="sxs-lookup"><span data-stu-id="dcfbc-183">Scoped</span></span>

<span data-ttu-id="dcfbc-184">Para aplicativos Web, um tempo de vida com escopo indica que os serviços são criados uma vez por solicitação do cliente (conexão).</span><span class="sxs-lookup"><span data-stu-id="dcfbc-184">For web applications a scoped lifetime indicates that services are created once per client request (connection).</span></span> <span data-ttu-id="dcfbc-185">Registre os serviços com escopo com <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-185">Register scoped services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span></span>

<span data-ttu-id="dcfbc-186">Em aplicativos que processam solicitações, os serviços com escopo são descartados no final da solicitação.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-186">In apps that process requests, scoped services are disposed at the end of the request.</span></span>

<span data-ttu-id="dcfbc-187">Ao usar Entity Framework Core, o <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> método de extensão registra os `DbContext` tipos com um tempo de vida com escopo definido por padrão.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-187">When using Entity Framework Core, the <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> extension method registers `DbContext` types with a scoped lifetime by default.</span></span>

> [!NOTE]
> <span data-ttu-id="dcfbc-188">***Não*** resolva um serviço com escopo de um singleton.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-188">Do ***not*** resolve a scoped service from a singleton.</span></span> <span data-ttu-id="dcfbc-189">Pode fazer com que o serviço tenha um estado incorreto durante o processamento das solicitações seguintes.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-189">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="dcfbc-190">Não há problema em:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-190">It's fine to:</span></span>
>
> - <span data-ttu-id="dcfbc-191">Resolva um serviço singleton de um serviço com escopo ou transitório.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-191">Resolve a singleton service from a scoped or transient service.</span></span>
> - <span data-ttu-id="dcfbc-192">Resolva um serviço com escopo de outro serviço com escopo ou transitório.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-192">Resolve a scoped service from another scoped or transient service.</span></span>

<span data-ttu-id="dcfbc-193">Por padrão, no ambiente de desenvolvimento, a resolução de um serviço de outro serviço com um tempo de vida maior gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-193">By default, in the development environment, resolving a service from another service with a longer lifetime throws an exception.</span></span> <span data-ttu-id="dcfbc-194">Para obter mais informações, confira [Validação de escopo](#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="dcfbc-194">For more information, see [Scope validation](#scope-validation).</span></span>

### <a name="singleton"></a><span data-ttu-id="dcfbc-195">Singleton</span><span class="sxs-lookup"><span data-stu-id="dcfbc-195">Singleton</span></span>

<span data-ttu-id="dcfbc-196">Os serviços de vida útil singleton são criados:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-196">Singleton lifetime services are created either:</span></span>

- <span data-ttu-id="dcfbc-197">Na primeira vez que forem solicitadas.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-197">The first time they're requested.</span></span>
- <span data-ttu-id="dcfbc-198">Pelo desenvolvedor, ao fornecer uma instância de implementação diretamente para o contêiner.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-198">By the developer, when providing an implementation instance directly to the container.</span></span> <span data-ttu-id="dcfbc-199">Essa abordagem raramente é necessária.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-199">This approach is rarely needed.</span></span>

<span data-ttu-id="dcfbc-200">Cada solicitação subsequente da implementação do serviço do contêiner de injeção de dependência usa a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-200">Every subsequent request of the service implementation from the dependency injection container uses the same instance.</span></span> <span data-ttu-id="dcfbc-201">Se o aplicativo exigir um comportamento singleton, permita que o contêiner de serviço gerencie o tempo de vida do serviço.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-201">If the app requires singleton behavior, allow the service container to manage the service's lifetime.</span></span> <span data-ttu-id="dcfbc-202">Não implemente o padrão de design singleton e forneça código para descartar o singleton.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-202">Don't implement the singleton design pattern and provide code to dispose of the singleton.</span></span> <span data-ttu-id="dcfbc-203">Os serviços nunca devem ser descartados pelo código que resolveu o serviço do contêiner.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-203">Services should never be disposed by code that resolved the service from the container.</span></span> <span data-ttu-id="dcfbc-204">Se um tipo ou fábrica for registrado como um singleton, o contêiner descartará o singleton automaticamente.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-204">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="dcfbc-205">Registre os serviços singleton com <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-205">Register singleton services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span></span> <span data-ttu-id="dcfbc-206">Os serviços singleton devem ser thread-safe e geralmente são usados em serviços sem estado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-206">Singleton services must be thread safe and are often used in stateless services.</span></span>

<span data-ttu-id="dcfbc-207">Em aplicativos que processam solicitações, os serviços singleton são descartados quando o <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> é Descartado no desligamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-207">In apps that process requests, singleton services are disposed when the <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> is disposed on application shutdown.</span></span> <span data-ttu-id="dcfbc-208">Como a memória não é liberada até que o aplicativo seja desligado, considere o uso de memória com um serviço singleton.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-208">Because memory is not released until the app is shut down, consider memory use with a singleton service.</span></span>

> [!WARNING]
> <span data-ttu-id="dcfbc-209">***Não*** resolva um serviço com escopo de um singleton.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-209">Do ***not*** resolve a scoped service from a singleton.</span></span> <span data-ttu-id="dcfbc-210">Pode fazer com que o serviço tenha um estado incorreto durante o processamento das solicitações seguintes.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-210">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="dcfbc-211">É bom resolver um serviço singleton de um serviço com escopo ou transitório.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-211">It's fine to resolve a singleton service from a scoped or transient service.</span></span>

## <a name="service-registration-methods"></a><span data-ttu-id="dcfbc-212">Métodos de registro do serviço</span><span class="sxs-lookup"><span data-stu-id="dcfbc-212">Service registration methods</span></span>

<span data-ttu-id="dcfbc-213">A estrutura fornece métodos de extensão de registro de serviço que são úteis em cenários específicos:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-213">The framework provides service registration extension methods that are useful in specific scenarios:</span></span>

| <span data-ttu-id="dcfbc-214">Método</span><span class="sxs-lookup"><span data-stu-id="dcfbc-214">Method</span></span> | <span data-ttu-id="dcfbc-215">Automática</span><span class="sxs-lookup"><span data-stu-id="dcfbc-215">Automatic</span></span><br><span data-ttu-id="dcfbc-216">objeto</span><span class="sxs-lookup"><span data-stu-id="dcfbc-216">object</span></span><br><span data-ttu-id="dcfbc-217">descarte</span><span class="sxs-lookup"><span data-stu-id="dcfbc-217">disposal</span></span> | <span data-ttu-id="dcfbc-218">Vários</span><span class="sxs-lookup"><span data-stu-id="dcfbc-218">Multiple</span></span><br><span data-ttu-id="dcfbc-219">implementações</span><span class="sxs-lookup"><span data-stu-id="dcfbc-219">implementations</span></span> | <span data-ttu-id="dcfbc-220">Passar argumentos</span><span class="sxs-lookup"><span data-stu-id="dcfbc-220">Pass args</span></span> |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br><span data-ttu-id="dcfbc-221">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-221">Example:</span></span><br><br>`services.AddSingleton<IMyDep, MyDep>();` | <span data-ttu-id="dcfbc-222">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-222">Yes</span></span> | <span data-ttu-id="dcfbc-223">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-223">Yes</span></span> | <span data-ttu-id="dcfbc-224">Não</span><span class="sxs-lookup"><span data-stu-id="dcfbc-224">No</span></span> |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br><span data-ttu-id="dcfbc-225">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-225">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | <span data-ttu-id="dcfbc-226">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-226">Yes</span></span> | <span data-ttu-id="dcfbc-227">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-227">Yes</span></span> | <span data-ttu-id="dcfbc-228">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-228">Yes</span></span> |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br><span data-ttu-id="dcfbc-229">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-229">Example:</span></span><br><br>`services.AddSingleton<MyDep>();` | <span data-ttu-id="dcfbc-230">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-230">Yes</span></span> | <span data-ttu-id="dcfbc-231">Não</span><span class="sxs-lookup"><span data-stu-id="dcfbc-231">No</span></span> | <span data-ttu-id="dcfbc-232">Não</span><span class="sxs-lookup"><span data-stu-id="dcfbc-232">No</span></span> |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br><span data-ttu-id="dcfbc-233">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-233">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | <span data-ttu-id="dcfbc-234">Não</span><span class="sxs-lookup"><span data-stu-id="dcfbc-234">No</span></span> | <span data-ttu-id="dcfbc-235">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-235">Yes</span></span> | <span data-ttu-id="dcfbc-236">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-236">Yes</span></span> |
| `AddSingleton(new {IMPLEMENTATION})`<br><br><span data-ttu-id="dcfbc-237">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-237">Examples:</span></span><br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | <span data-ttu-id="dcfbc-238">Não</span><span class="sxs-lookup"><span data-stu-id="dcfbc-238">No</span></span> | <span data-ttu-id="dcfbc-239">Não</span><span class="sxs-lookup"><span data-stu-id="dcfbc-239">No</span></span> | <span data-ttu-id="dcfbc-240">Sim</span><span class="sxs-lookup"><span data-stu-id="dcfbc-240">Yes</span></span> |

<span data-ttu-id="dcfbc-241">Para obter mais informações sobre o descarte de tipos, consulte a seção [Descarte de serviços](dependency-injection-guidelines.md#disposal-of-services).</span><span class="sxs-lookup"><span data-stu-id="dcfbc-241">For more information on type disposal, see the [Disposal of services](dependency-injection-guidelines.md#disposal-of-services) section.</span></span>

<span data-ttu-id="dcfbc-242">A estrutura também fornece `TryAdd{LIFETIME}` métodos de extensão, que registram o serviço somente se ainda não houver uma implementação registrada.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-242">The framework also provides `TryAdd{LIFETIME}` extension methods, which register the service only if there isn't already an implementation registered.</span></span>

<span data-ttu-id="dcfbc-243">No exemplo a seguir, a chamada para `AddSingleton` registra `MessageWriter` como uma implementação para `IMessageWriter` .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-243">In the following example, the call to `AddSingleton` registers `MessageWriter` as an implementation for `IMessageWriter`.</span></span> <span data-ttu-id="dcfbc-244">A chamada para `TryAddSingleton` não tem efeito porque `IMessageWriter` já tem uma implementação registrada:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-244">The call to `TryAddSingleton` has no effect because `IMessageWriter` already has a registered implementation:</span></span>

```csharp
services.AddSingleton<IMessageWriter, MessageWriter>();
services.TryAddSingleton<IMessageWriter, DifferentMessageWriter>();
```

<span data-ttu-id="dcfbc-245">O `TryAddSingleton` não tem efeito, pois já foi adicionado e o "try" falhará.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-245">The `TryAddSingleton` has no effect, as it was already added and the "try" will fail.</span></span>

<span data-ttu-id="dcfbc-246">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-246">For more information, see:</span></span>

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

<span data-ttu-id="dcfbc-247">Os métodos [TryAddEnumerable (Service Descriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) registram o serviço somente se ainda não houver uma implementação *do mesmo tipo*.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-247">The [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) methods register the service only if there isn't already an implementation *of the same type*.</span></span> <span data-ttu-id="dcfbc-248">Vários serviços são resolvidos via `IEnumerable<{SERVICE}>`.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-248">Multiple services are resolved via `IEnumerable<{SERVICE}>`.</span></span> <span data-ttu-id="dcfbc-249">Ao registrar serviços, adicione uma instância se um dos mesmos tipos ainda não tiver sido adicionado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-249">When registering services, add an instance if one of the same types hasn't already been added.</span></span> <span data-ttu-id="dcfbc-250">Os autores de biblioteca usam `TryAddEnumerable` para evitar o registro de várias cópias de uma implementação no contêiner.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-250">Library authors use `TryAddEnumerable` to avoid registering multiple copies of an implementation in the container.</span></span>

<span data-ttu-id="dcfbc-251">No exemplo a seguir, a primeira chamada para `TryAddEnumerable` registra `MessageWriter` como uma implementação para `IMessageWriter1` .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-251">In the following example, the first call to `TryAddEnumerable` registers `MessageWriter` as an implementation for `IMessageWriter1`.</span></span> <span data-ttu-id="dcfbc-252">A segunda chamada é registrada `MessageWriter` para `IMessageWriter2` .</span><span class="sxs-lookup"><span data-stu-id="dcfbc-252">The second call registers `MessageWriter` for `IMessageWriter2`.</span></span> <span data-ttu-id="dcfbc-253">A terceira chamada não tem nenhum efeito porque `IMessageWriter1` já tem uma implementação registrada de `MessageWriter` :</span><span class="sxs-lookup"><span data-stu-id="dcfbc-253">The third call has no effect because `IMessageWriter1` already has a registered implementation of `MessageWriter`:</span></span>

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

<span data-ttu-id="dcfbc-254">O registro de serviço geralmente é independente de ordem, exceto ao registrar várias implementações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-254">Service registration is generally order independent except when registering multiple implementations of the same type.</span></span>

<span data-ttu-id="dcfbc-255">`IServiceCollection` é uma coleção de <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objetos.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-255">`IServiceCollection` is a collection of <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objects.</span></span> <span data-ttu-id="dcfbc-256">O exemplo a seguir mostra como registrar um serviço criando e adicionando um `ServiceDescriptor` :</span><span class="sxs-lookup"><span data-stu-id="dcfbc-256">The following example shows how to register a service by creating and adding a `ServiceDescriptor`:</span></span>

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

<span data-ttu-id="dcfbc-257">Os `Add{LIFETIME}` métodos internos usam a mesma abordagem.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-257">The built-in `Add{LIFETIME}` methods use the same approach.</span></span> <span data-ttu-id="dcfbc-258">Por exemplo, consulte o [código-fonte de Addscoped](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span><span class="sxs-lookup"><span data-stu-id="dcfbc-258">For example, see the [AddScoped source code](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span></span>

### <a name="constructor-injection-behavior"></a><span data-ttu-id="dcfbc-259">Comportamento da injeção de construtor</span><span class="sxs-lookup"><span data-stu-id="dcfbc-259">Constructor injection behavior</span></span>

<span data-ttu-id="dcfbc-260">Os serviços podem ser resolvidos usando:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-260">Services can be resolved by using:</span></span>

- <xref:System.IServiceProvider>
- <span data-ttu-id="dcfbc-261"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-261"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span></span>
  - <span data-ttu-id="dcfbc-262">Cria objetos que não estão registrados no contêiner.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-262">Creates objects that aren't registered in the container.</span></span>
  - <span data-ttu-id="dcfbc-263">Usado com alguns recursos de estrutura.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-263">Used with some framework features.</span></span>

<span data-ttu-id="dcfbc-264">Os construtores podem aceitar argumentos que não são fornecidos pela injeção de dependência, mas que precisam atribuir valores padrão.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-264">Constructors can accept arguments that aren't provided by dependency injection, but the arguments must assign default values.</span></span>

<span data-ttu-id="dcfbc-265">Quando os serviços são resolvidos por `IServiceProvider` ou `ActivatorUtilities`, a injeção do construtor exige um construtor *público*.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-265">When services are resolved by `IServiceProvider` or `ActivatorUtilities`, constructor injection requires a *public* constructor.</span></span>

<span data-ttu-id="dcfbc-266">Quando os serviços são resolvidos por `ActivatorUtilities`, a injeção de construtor exige a existência de apenas de um construtor aplicável.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-266">When services are resolved by `ActivatorUtilities`, constructor injection requires that only one applicable constructor exists.</span></span> <span data-ttu-id="dcfbc-267">Há suporte para sobrecargas de construtor, mas somente uma sobrecarga pode existir, cujos argumentos podem ser todos atendidos pela injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-267">Constructor overloads are supported, but only one overload can exist whose arguments can all be fulfilled by dependency injection.</span></span>

## <a name="scope-validation"></a><span data-ttu-id="dcfbc-268">Validação de escopo</span><span class="sxs-lookup"><span data-stu-id="dcfbc-268">Scope validation</span></span>

<span data-ttu-id="dcfbc-269">Quando o aplicativo é executado no `Development` ambiente e chama [CreateDefaultBuilder](generic-host.md#default-builder-settings) para criar o host, o provedor de serviço padrão executa verificações para verificar se:</span><span class="sxs-lookup"><span data-stu-id="dcfbc-269">When the app runs in the `Development` environment and calls [CreateDefaultBuilder](generic-host.md#default-builder-settings) to build the host, the default service provider performs checks to verify that:</span></span>

- <span data-ttu-id="dcfbc-270">Os serviços com escopo não são resolvidos do provedor de serviços raiz.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-270">Scoped services aren't resolved from the root service provider.</span></span>
- <span data-ttu-id="dcfbc-271">Os serviços com escopo não são injetados em singletons.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-271">Scoped services aren't injected into singletons.</span></span>

<span data-ttu-id="dcfbc-272">O provedor de serviços raiz é criado quando <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-272">The root service provider is created when <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> is called.</span></span> <span data-ttu-id="dcfbc-273">O tempo de vida do provedor de serviço raiz corresponde ao tempo de vida do aplicativo quando o provedor começa com o aplicativo e é Descartado quando o aplicativo é desligado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-273">The root service provider's lifetime corresponds to the app's lifetime when the provider starts with the app and is disposed when the app shuts down.</span></span>

<span data-ttu-id="dcfbc-274">Os serviços com escopo são descartados pelo contêiner que os criou.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-274">Scoped services are disposed by the container that created them.</span></span> <span data-ttu-id="dcfbc-275">Se um serviço com escopo for criado no contêiner raiz, o tempo de vida do serviço será efetivamente promovido para singleton porque é descartado apenas pelo contêiner raiz quando o aplicativo é desligado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-275">If a scoped service is created in the root container, the service's lifetime is effectively promoted to singleton because it's only disposed by the root container when the app shuts down.</span></span> <span data-ttu-id="dcfbc-276">A validação dos escopos de serviço detecta essas situações quando `BuildServiceProvider` é chamado.</span><span class="sxs-lookup"><span data-stu-id="dcfbc-276">Validating service scopes catches these situations when `BuildServiceProvider` is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcfbc-277">Confira também</span><span class="sxs-lookup"><span data-stu-id="dcfbc-277">See also</span></span>

- [<span data-ttu-id="dcfbc-278">Usar injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="dcfbc-278">Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
- [<span data-ttu-id="dcfbc-279">Diretrizes de injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="dcfbc-279">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
- [<span data-ttu-id="dcfbc-280">Padrões de conferência NDC para desenvolvimento de aplicativo de DI</span><span class="sxs-lookup"><span data-stu-id="dcfbc-280">NDC Conference Patterns for DI app development</span></span>](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [<span data-ttu-id="dcfbc-281">Princípio de dependências explícitas</span><span class="sxs-lookup"><span data-stu-id="dcfbc-281">Explicit dependencies principle</span></span>](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [<span data-ttu-id="dcfbc-282">Inversão de contêineres de controle e padrão de injeção de dependência (Martin Fowler)</span><span class="sxs-lookup"><span data-stu-id="dcfbc-282">Inversion of control containers and the dependency injection pattern (Martin Fowler)</span></span>](https://www.martinfowler.com/articles/injection.html)