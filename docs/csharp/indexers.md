---
title: Indexadores
description: Saiba mais sobre indexadores C# e como implementar propriedades indexadas, que são propriedades referenciadas usando um ou mais argumentos.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 1369740404c500d8b44b4706959bf4640c26aa2d
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656105"
---
# <a name="indexers"></a><span data-ttu-id="f5f34-103">Indexadores</span><span class="sxs-lookup"><span data-stu-id="f5f34-103">Indexers</span></span>

<span data-ttu-id="f5f34-104">Os *indexadores* são semelhantes às propriedades.</span><span class="sxs-lookup"><span data-stu-id="f5f34-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="f5f34-105">De muitas maneiras, os indexadores baseiam-se nos mesmos recursos de linguagem que as [propriedades](properties.md).</span><span class="sxs-lookup"><span data-stu-id="f5f34-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="f5f34-106">Os indexadores habilitam as propriedades *indexadas*: propriedades referenciadas com o uso de um ou mais argumentos.</span><span class="sxs-lookup"><span data-stu-id="f5f34-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="f5f34-107">Esses argumentos fornecem um índice em um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="f5f34-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="f5f34-108">Sintaxe do indexador</span><span class="sxs-lookup"><span data-stu-id="f5f34-108">Indexer Syntax</span></span>

<span data-ttu-id="f5f34-109">Você pode acessar um indexador por meio de um nome de variável e colchetes.</span><span class="sxs-lookup"><span data-stu-id="f5f34-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="f5f34-110">Coloque os argumentos do indexador dentro de colchetes:</span><span class="sxs-lookup"><span data-stu-id="f5f34-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="f5f34-111">Você declara os indexadores usando a palavra-chave `this` como o nome da propriedade e declarando os argumentos entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="f5f34-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="f5f34-112">Essa declaração corresponderia à utilização mostrada no parágrafo anterior:</span><span class="sxs-lookup"><span data-stu-id="f5f34-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="f5f34-113">Neste exemplo inicial, você pode ver a relação entre a sintaxe das propriedades e dos indexadores.</span><span class="sxs-lookup"><span data-stu-id="f5f34-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="f5f34-114">Essa analogia impulsiona a maioria das regras de sintaxe para indexadores.</span><span class="sxs-lookup"><span data-stu-id="f5f34-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="f5f34-115">Os indexadores podem ter qualquer modificador de acesso válido (público, protegido interno, protegido, interno, particular ou protegido de forma privada).</span><span class="sxs-lookup"><span data-stu-id="f5f34-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="f5f34-116">Eles podem ser sealed, virtual ou abstract.</span><span class="sxs-lookup"><span data-stu-id="f5f34-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="f5f34-117">Assim como acontece com as propriedades, você pode especificar modificadores de acesso diferentes para os acessadores get e set em um indexador.</span><span class="sxs-lookup"><span data-stu-id="f5f34-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="f5f34-118">Você também pode especificar indexadores somente leitura (omitindo o acessador set) ou indexadores somente gravação (omitindo o acessador get).</span><span class="sxs-lookup"><span data-stu-id="f5f34-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="f5f34-119">Você pode aplicar aos indexadores quase tudo o que aprendeu ao trabalhar com propriedades.</span><span class="sxs-lookup"><span data-stu-id="f5f34-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="f5f34-120">A única exceção a essa regra são as *propriedades autoimplementadas*.</span><span class="sxs-lookup"><span data-stu-id="f5f34-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="f5f34-121">O compilador não pode gerar sempre o armazenamento correto para um indexador.</span><span class="sxs-lookup"><span data-stu-id="f5f34-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="f5f34-122">A presença dos argumentos para referenciar um item em um conjunto de itens distingue os indexadores das propriedades.</span><span class="sxs-lookup"><span data-stu-id="f5f34-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="f5f34-123">Você pode definir vários indexadores em um tipo, contanto que as listas de argumentos para cada indexador seja exclusiva.</span><span class="sxs-lookup"><span data-stu-id="f5f34-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="f5f34-124">Vamos explorar diferentes cenários em que você pode usar um ou mais indexadores em uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="f5f34-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span>

## <a name="scenarios"></a><span data-ttu-id="f5f34-125">Cenários</span><span class="sxs-lookup"><span data-stu-id="f5f34-125">Scenarios</span></span>

<span data-ttu-id="f5f34-126">Você deve definir *indexadores* em seu tipo quando a API do tipo modela alguma coleção na qual você define os argumentos para essa coleção.</span><span class="sxs-lookup"><span data-stu-id="f5f34-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="f5f34-127">Seu indexadores podem ou não mapear diretamente para os tipos de coleção que fazem parte da estrutura principal do .NET.</span><span class="sxs-lookup"><span data-stu-id="f5f34-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="f5f34-128">O tipo pode ter outras responsabilidades, além da modelagem de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f5f34-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="f5f34-129">Os indexadores permitem que você forneça a API que corresponda à abstração do tipo, sem expor os detalhes internos de como os valores dessa abstração são armazenados ou computados.</span><span class="sxs-lookup"><span data-stu-id="f5f34-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="f5f34-130">Vamos examinar alguns dos cenários comuns de uso de *indexadores*.</span><span class="sxs-lookup"><span data-stu-id="f5f34-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="f5f34-131">Você pode acessar a [pasta de exemplo para indexadores](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="f5f34-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/master/csharp/indexers).</span></span> <span data-ttu-id="f5f34-132">Para obter instruções de download, consulte [Exemplos e tutoriais](../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="f5f34-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="f5f34-133">Matrizes e vetores</span><span class="sxs-lookup"><span data-stu-id="f5f34-133">Arrays and Vectors</span></span>

<span data-ttu-id="f5f34-134">Um dos cenários mais comuns para a criação de indexadores é quando seu tipo modela uma matriz ou um vetor.</span><span class="sxs-lookup"><span data-stu-id="f5f34-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="f5f34-135">Você pode criar um indexador para modelar uma lista ordenada de dados.</span><span class="sxs-lookup"><span data-stu-id="f5f34-135">You can create an indexer to model an ordered list of data.</span></span>

<span data-ttu-id="f5f34-136">A vantagem de criar seu próprio indexador é que você pode definir o armazenamento dessa coleção para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="f5f34-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="f5f34-137">Imagine um cenário em que seu tipo modela dados históricos que são muito grandes para serem carregados na memória ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="f5f34-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="f5f34-138">Você precisa carregar e descarregar seções da coleção com base na utilização.</span><span class="sxs-lookup"><span data-stu-id="f5f34-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="f5f34-139">O exemplo a seguir modela esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="f5f34-139">The example following models this behavior.</span></span> <span data-ttu-id="f5f34-140">Ele relata quantos pontos de dados existem.</span><span class="sxs-lookup"><span data-stu-id="f5f34-140">It reports on how many data points exist.</span></span> <span data-ttu-id="f5f34-141">Ele cria páginas para manter as seções de dados sob demanda.</span><span class="sxs-lookup"><span data-stu-id="f5f34-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="f5f34-142">Ele remove páginas da memória a fim de liberar espaço para as páginas necessárias para as solicitações mais recentes.</span><span class="sxs-lookup"><span data-stu-id="f5f34-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

```csharp
public class DataSamples
{
    private class Page
    {
        private readonly List<Measurements> pageData = new List<Measurements>();
        private readonly int startingIndex;
        private readonly int length;
        private bool dirty;
        private DateTime lastAccess;

        public Page(int startingIndex, int length)
        {
            this.startingIndex = startingIndex;
            this.length = length;
            lastAccess = DateTime.Now;

            // This stays as random stuff:
            var generator = new Random();
            for(int i=0; i < length; i++)
            {
                var m = new Measurements
                {
                    HiTemp = generator.Next(50, 95),
                    LoTemp = generator.Next(12, 49),
                    AirPressure = 28.0 + generator.NextDouble() * 4
                };
                pageData.Add(m);
            }
        }
        public bool HasItem(int index) =>
            ((index >= startingIndex) &&
            (index < startingIndex + length));

        public Measurements this[int index]
        {
            get
            {
                lastAccess = DateTime.Now;
                return pageData[index - startingIndex];
            }
            set
            {
                pageData[index - startingIndex] = value;
                dirty = true;
                lastAccess = DateTime.Now;
            }
        }

        public bool Dirty => dirty;
        public DateTime LastAccess => lastAccess;
    }

    private readonly int totalSize;
    private readonly List<Page> pagesInMemory = new List<Page>();

    public DataSamples(int totalSize)
    {
        this.totalSize = totalSize;
    }

    public Measurements this[int index]
    {
        get
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");

            var page = updateCachedPagesForAccess(index);
            return page[index];
        }
        set
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");
            var page = updateCachedPagesForAccess(index);

            page[index] = value;
        }
    }

    private Page updateCachedPagesForAccess(int index)
    {
        foreach (var p in pagesInMemory)
        {
            if (p.HasItem(index))
            {
                return p;
            }
        }
        var startingIndex = (index / 1000) * 1000;
        var newPage = new Page(startingIndex, 1000);
        addPageToCache(newPage);
        return newPage;
    }

    private void addPageToCache(Page p)
    {
        if (pagesInMemory.Count > 4)
        {
            // remove oldest non-dirty page:
            var oldest = pagesInMemory
                .Where(page => !page.Dirty)
                .OrderBy(page => page.LastAccess)
                .FirstOrDefault();
            // Note that this may keep more than 5 pages in memory
            // if too much is dirty
            if (oldest != null)
                pagesInMemory.Remove(oldest);
        }
        pagesInMemory.Add(p);
    }
}
```

<span data-ttu-id="f5f34-143">Você pode seguir esta linguagem de design para modelar qualquer tipo de coleção na qual há bons motivos para não carregar todo o conjunto de dados em uma coleção na memória.</span><span class="sxs-lookup"><span data-stu-id="f5f34-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="f5f34-144">Observe que a classe `Page` é uma classe particular aninhada que não faz parte da interface pública.</span><span class="sxs-lookup"><span data-stu-id="f5f34-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="f5f34-145">Esses detalhes estão ocultos de qualquer usuário dessa classe.</span><span class="sxs-lookup"><span data-stu-id="f5f34-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="f5f34-146">Dicionários</span><span class="sxs-lookup"><span data-stu-id="f5f34-146">Dictionaries</span></span>

<span data-ttu-id="f5f34-147">Outro cenário comum é quando você precisa modelar um dicionário ou um mapa.</span><span class="sxs-lookup"><span data-stu-id="f5f34-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="f5f34-148">Esse cenário é quando o seu tipo armazena valores com base na chave, normalmente chaves de texto.</span><span class="sxs-lookup"><span data-stu-id="f5f34-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="f5f34-149">Este exemplo cria um dicionário que mapeia os argumentos de linha de comando para [expressões lambda](delegates-overview.md) que gerenciam essas opções.</span><span class="sxs-lookup"><span data-stu-id="f5f34-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="f5f34-150">O exemplo a seguir mostra duas classes: uma classe `ArgsActions` que mapeia uma opção de linha de comando para um delegado `Action` e uma `ArgsProcessor`, que usa a `ArgsActions` para executar cada `Action`, quando encontrar essa opção.</span><span class="sxs-lookup"><span data-stu-id="f5f34-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

```csharp
public class ArgsProcessor
{
    private readonly ArgsActions actions;

    public ArgsProcessor(ArgsActions actions)
    {
        this.actions = actions;
    }

    public void Process(string[] args)
    {
        foreach(var arg in args)
        {
            actions[arg]?.Invoke();
        }
    }

}
public class ArgsActions
{
    readonly private Dictionary<string, Action> argsActions = new Dictionary<string, Action>();

    public Action this[string s]
    {
        get
        {
            Action action;
            Action defaultAction = () => {} ;
            return argsActions.TryGetValue(s, out action) ? action : defaultAction;
        }
    }

    public void SetOption(string s, Action a)
    {
        argsActions[s] = a;
    }
}
```

<span data-ttu-id="f5f34-151">Neste exemplo, a coleção `ArgsAction` mapeia próximo à coleção subjacente.</span><span class="sxs-lookup"><span data-stu-id="f5f34-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="f5f34-152">O `get` determina se uma opção específica foi configurada.</span><span class="sxs-lookup"><span data-stu-id="f5f34-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="f5f34-153">Se sim, ele retorna a `Action` associada a essa opção.</span><span class="sxs-lookup"><span data-stu-id="f5f34-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="f5f34-154">Se não, ele retorna uma `Action` que não faz nada.</span><span class="sxs-lookup"><span data-stu-id="f5f34-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="f5f34-155">O acessador público não inclui um acessador `set`.</span><span class="sxs-lookup"><span data-stu-id="f5f34-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="f5f34-156">Em vez disso, o design usa um método público para a configuração de opções.</span><span class="sxs-lookup"><span data-stu-id="f5f34-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="f5f34-157">Mapas multidimensionais</span><span class="sxs-lookup"><span data-stu-id="f5f34-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="f5f34-158">Você pode criar indexadores que usam vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="f5f34-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="f5f34-159">Além disso, esses argumentos não estão restritos a serem do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="f5f34-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="f5f34-160">Vamos analisar dois exemplos.</span><span class="sxs-lookup"><span data-stu-id="f5f34-160">Let's look at two examples.</span></span>

<span data-ttu-id="f5f34-161">O primeiro exemplo mostra uma classe que gera valores para um conjunto de Mandelbrot.</span><span class="sxs-lookup"><span data-stu-id="f5f34-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="f5f34-162">Para obter mais informações sobre a matemática por trás desse conjunto, leia [este artigo](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="f5f34-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span>
<span data-ttu-id="f5f34-163">O indexador usa dois duplos para definir um ponto no plano X, Y.</span><span class="sxs-lookup"><span data-stu-id="f5f34-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="f5f34-164">O acessador get calcula o número de iterações até que um ponto seja considerado como fora do conjunto.</span><span class="sxs-lookup"><span data-stu-id="f5f34-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="f5f34-165">Se o número máximo de iterações for atingido, o ponto está no conjunto e o valor da classe maxIterations será retornado.</span><span class="sxs-lookup"><span data-stu-id="f5f34-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="f5f34-166">(As imagens geradas por computador, popularizadas para o conjunto de Mandelbrot, definem cores para o número de iterações necessárias para determinar que um ponto está fora do conjunto.</span><span class="sxs-lookup"><span data-stu-id="f5f34-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

```csharp
public class Mandelbrot
{
    readonly private int maxIterations;

    public Mandelbrot(int maxIterations)
    {
        this.maxIterations = maxIterations;
    }

    public int this [double x, double y]
    {
        get
        {
            var iterations = 0;
            var x0 = x;
            var y0 = y;

            while ((x*x + y * y < 4) &&
                (iterations < maxIterations))
            {
                var newX = x * x - y * y + x0;
                y = 2 * x * y + y0;
                x = newX;
                iterations++;
            }
            return iterations;
        }
    }
}
```

<span data-ttu-id="f5f34-167">O conjunto de Mandelbrot define valores em cada coordenada (x,y) para valores de número real.</span><span class="sxs-lookup"><span data-stu-id="f5f34-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="f5f34-168">Isso define um dicionário que poderia conter um número infinito de valores.</span><span class="sxs-lookup"><span data-stu-id="f5f34-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="f5f34-169">Portanto, não há armazenamento por trás desse conjunto.</span><span class="sxs-lookup"><span data-stu-id="f5f34-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="f5f34-170">Em vez disso, essa classe calcula o valor de cada ponto quando o código chama o acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="f5f34-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="f5f34-171">Não há nenhum armazenamento subjacente usado.</span><span class="sxs-lookup"><span data-stu-id="f5f34-171">There's no underlying storage used.</span></span>

<span data-ttu-id="f5f34-172">Vamos examinar um último uso de indexadores, em que o indexador recebe vários argumentos de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="f5f34-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="f5f34-173">Considere um programa que gerencia os dados históricos de temperatura.</span><span class="sxs-lookup"><span data-stu-id="f5f34-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="f5f34-174">Esse indexador utiliza uma cidade e uma data para definir ou obter as temperaturas máximas e mínimas desse local:</span><span class="sxs-lookup"><span data-stu-id="f5f34-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

```csharp
using DateMeasurements =
    System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements =
    System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;

public class HistoricalWeatherData
{
    readonly CityDataMeasurements storage = new CityDataMeasurements();

    public Measurements this[string city, DateTime date]
    {
        get
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
                throw new ArgumentOutOfRangeException(nameof(city), "City not found");

            // strip out any time portion:
            var index = date.Date;
            var measure = default(Measurements);
            if (cityData.TryGetValue(index, out measure))
                return measure;
            throw new ArgumentOutOfRangeException(nameof(date), "Date not found");
        }
        set
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
            {
                cityData = new DateMeasurements();
                storage.Add(city, cityData);
            }

            // Strip out any time portion:
            var index = date.Date;
            cityData[index] = value;
        }
    }
}
```

<span data-ttu-id="f5f34-175">Este exemplo cria um indexador que mapeia dados meteorológicos de dois argumentos diferentes: uma cidade (representada por uma `string`) e uma data (representada por uma `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="f5f34-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="f5f34-176">O armazenamento interno usa duas classes `Dictionary` para representar o dicionário bidimensional.</span><span class="sxs-lookup"><span data-stu-id="f5f34-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="f5f34-177">A API pública não representa mais o armazenamento subjacente.</span><span class="sxs-lookup"><span data-stu-id="f5f34-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="f5f34-178">Em vez disso, os recursos de linguagem dos indexadores permite que você crie uma interface pública que representa a sua abstração, mesmo que o armazenamento subjacente deva usar diferentes tipos principais de coleção.</span><span class="sxs-lookup"><span data-stu-id="f5f34-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="f5f34-179">Há duas partes desse código que podem não ser familiares para alguns desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="f5f34-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="f5f34-180">Essas duas `using` diretivas:</span><span class="sxs-lookup"><span data-stu-id="f5f34-180">These two `using` directives:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="f5f34-181">criam um *alias* para um tipo genérico construído.</span><span class="sxs-lookup"><span data-stu-id="f5f34-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="f5f34-182">Essas instruções habilitam o código a usar, mais adiante, os nomes `DateMeasurements` e `CityDateMeasurements` mais descritivos, em vez da construção genérica de `Dictionary<DateTime, Measurements>` e `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="f5f34-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span>
<span data-ttu-id="f5f34-183">Esse constructo exige o uso de nomes de tipo totalmente qualificados no lado direito do sinal `=`.</span><span class="sxs-lookup"><span data-stu-id="f5f34-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="f5f34-184">A segunda técnica é para remover as partes de hora de qualquer objeto `DateTime` usado para indexar na coleção.</span><span class="sxs-lookup"><span data-stu-id="f5f34-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="f5f34-185">O .NET não inclui um tipo somente de data.</span><span class="sxs-lookup"><span data-stu-id="f5f34-185">.NET doesn't include a date-only type.</span></span>
<span data-ttu-id="f5f34-186">Os desenvolvedores usam o tipo `DateTime`, mas usam a propriedade `Date` para garantir que qualquer objeto `DateTime` daquele dia sejam iguais.</span><span class="sxs-lookup"><span data-stu-id="f5f34-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="f5f34-187">Resumindo</span><span class="sxs-lookup"><span data-stu-id="f5f34-187">Summing Up</span></span>

<span data-ttu-id="f5f34-188">Você deve criar indexadores sempre que tiver um elemento semelhante a uma propriedade em sua classe, em que essa propriedade representa não um único valor, mas uma coleção de valores em que cada item individual é identificado por um conjunto de argumentos.</span><span class="sxs-lookup"><span data-stu-id="f5f34-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="f5f34-189">Esses argumentos podem identificar exclusivamente qual item da coleção deve ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="f5f34-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="f5f34-190">Os indexadores estendem o conceito de [Propriedades](properties.md), em que um membro é tratado como um item de dados de fora da classe, mas como um método no interior.</span><span class="sxs-lookup"><span data-stu-id="f5f34-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the inside.</span></span> <span data-ttu-id="f5f34-191">Os indexadores permitem que os argumentos localizem um único item em uma propriedade que representa um conjunto de itens.</span><span class="sxs-lookup"><span data-stu-id="f5f34-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
