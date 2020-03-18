---
title: Carregar dados de arquivos e outras fontes
description: Aprenda a carregar dados para processamento e treinamento em ML.NET usando a API. Os dados são armazenados em arquivos, bancos de dados, JSON, XML ou coleções na memória.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74344748"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="a5711-104">Carregar dados de arquivos e outras fontes</span><span class="sxs-lookup"><span data-stu-id="a5711-104">Load data from files and other sources</span></span>

<span data-ttu-id="a5711-105">Aprenda a carregar dados para processamento e treinamento em ML.NET usando a API.</span><span class="sxs-lookup"><span data-stu-id="a5711-105">Learn how to load data for processing and training into ML.NET using the API.</span></span> <span data-ttu-id="a5711-106">Originalmente, os dados são armazenados em arquivos ou outras fontes de dados, como bancos de dados, JSON, XML ou coleções na memória.</span><span class="sxs-lookup"><span data-stu-id="a5711-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

<span data-ttu-id="a5711-107">Se você estiver usando o Model Builder, consulte [Carregar dados de treinamento no Model Builder](load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="a5711-107">If you're using Model Builder, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="a5711-108">Criar o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="a5711-108">Create the data model</span></span>

<span data-ttu-id="a5711-109">O ML.NET permite que você defina modelos de dados por meio de classes.</span><span class="sxs-lookup"><span data-stu-id="a5711-109">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="a5711-110">Por exemplo, considerando os seguintes dados de entrada:</span><span class="sxs-lookup"><span data-stu-id="a5711-110">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="a5711-111">Crie um modelo de dados que represente o snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="a5711-111">Create a data model that represents the snippet below:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="a5711-112">Anotando o modelo de dados com atributos de coluna</span><span class="sxs-lookup"><span data-stu-id="a5711-112">Annotating the data model with column attributes</span></span>

<span data-ttu-id="a5711-113">Atributos dão ao ML.NET mais informações sobre o modelo de dados e a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="a5711-113">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="a5711-114">O [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) atributo especifica os índices da coluna de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="a5711-114">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5711-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)só é necessário ao carregar dados de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a5711-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="a5711-116">Carregar colunas como:</span><span class="sxs-lookup"><span data-stu-id="a5711-116">Load columns as:</span></span>

- <span data-ttu-id="a5711-117">Colunas individuais como `Size` e `CurrentPrices` na classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="a5711-117">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="a5711-118">Como várias colunas por vez na forma de um vetor `HistoricalPrices` na classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="a5711-118">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="a5711-119">Se você tiver uma propriedade [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) vetorial, aplique o atributo à propriedade em seu modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="a5711-119">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="a5711-120">É importante observar que todos os elementos no vetor precisam ser do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="a5711-120">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="a5711-121">Manter as colunas separadas permite a facilidade e a flexibilidade da engenharia de recursos, mas, para um número muito grande de colunas, a operação nas colunas individuais causa um impacto na velocidade de treinamento.</span><span class="sxs-lookup"><span data-stu-id="a5711-121">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="a5711-122">O ML.NET opera por meio de nomes de coluna.</span><span class="sxs-lookup"><span data-stu-id="a5711-122">ML.NET Operates through column names.</span></span> <span data-ttu-id="a5711-123">Se você quiser mudar o nome de uma coluna para [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) algo diferente do nome da propriedade, use o atributo.</span><span class="sxs-lookup"><span data-stu-id="a5711-123">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="a5711-124">Ao criar objetos na memória, você ainda cria objetos usando o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a5711-124">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="a5711-125">No entanto, para o processamento de dados e construção de modelos de [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) machine learning, ML.NET substitui e faz referência ao imóvel com o valor fornecido no atributo.</span><span class="sxs-lookup"><span data-stu-id="a5711-125">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="a5711-126">Carregar dados de um único arquivo</span><span class="sxs-lookup"><span data-stu-id="a5711-126">Load data from a single file</span></span>

<span data-ttu-id="a5711-127">Para carregar dados de [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) um arquivo, use o método juntamente com o modelo de dados para que os dados sejam carregados.</span><span class="sxs-lookup"><span data-stu-id="a5711-127">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="a5711-128">Uma vez que o parâmetro `separatorChar` é delimitado por tabulação por padrão, altere-o para seu arquivo de dados conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a5711-128">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="a5711-129">Se o arquivo tiver um cabeçalho, defina o parâmetro `hasHeader` como `true` para ignorar a primeira linha no arquivo e começar a carregar dados da segunda linha.</span><span class="sxs-lookup"><span data-stu-id="a5711-129">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="a5711-130">Carregar dados de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="a5711-130">Load data from multiple files</span></span>

<span data-ttu-id="a5711-131">Caso seus dados sejam armazenados em vários arquivos, desde que o esquema de dados seja o mesmo, o ML.NET permitirá que você carregue dados de vários arquivos que estejam no mesmo diretório ou em vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="a5711-131">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="a5711-132">Carregar de arquivos em um único diretório</span><span class="sxs-lookup"><span data-stu-id="a5711-132">Load from files in a single directory</span></span>

<span data-ttu-id="a5711-133">Quando todos os seus arquivos de dados estiverem no [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) mesmo diretório, use curingas no método.</span><span class="sxs-lookup"><span data-stu-id="a5711-133">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="a5711-134">Carregar de arquivos em vários diretórios</span><span class="sxs-lookup"><span data-stu-id="a5711-134">Load from files in multiple directories</span></span>

<span data-ttu-id="a5711-135">Para carregar dados de vários [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) diretórios, [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)use o método para criar um .</span><span class="sxs-lookup"><span data-stu-id="a5711-135">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="a5711-136">Em seguida, [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) use o método e especifique os caminhos de arquivo individuais (curingas não podem ser usados).</span><span class="sxs-lookup"><span data-stu-id="a5711-136">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="a5711-137">Carregar dados de um banco de dados relacional</span><span class="sxs-lookup"><span data-stu-id="a5711-137">Load data from a relational database</span></span>

<span data-ttu-id="a5711-138">ML.NET suporta o carregamento de dados de uma [`System.Data`](xref:System.Data) variedade de bancos de dados relacionais suportados por isso incluem SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 e muito mais.</span><span class="sxs-lookup"><span data-stu-id="a5711-138">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="a5711-139">Para `DatabaseLoader`usar, consulte o pacote [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5711-139">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="a5711-140">Dado um banco `House` de dados com uma tabela nomeada e o seguinte esquema:</span><span class="sxs-lookup"><span data-stu-id="a5711-140">Given a database with a table named `House` and the following schema:</span></span>

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="a5711-141">Os dados podem ser modelados por uma classe como `HouseData`.</span><span class="sxs-lookup"><span data-stu-id="a5711-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="a5711-142">Então, dentro de sua `DatabaseLoader`aplicação, crie um .</span><span class="sxs-lookup"><span data-stu-id="a5711-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="a5711-143">Defina sua seqüência de conexões, bem como o comando `DatabaseSource` SQL a ser executado no banco de dados e crie uma instância.</span><span class="sxs-lookup"><span data-stu-id="a5711-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="a5711-144">Esta amostra usa um banco de dados LocalDB SQL Server com um caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="a5711-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="a5711-145">No entanto, o DatabaseLoader suporta qualquer outra seqüência de conexão válida para bancos de dados no local e na nuvem.</span><span class="sxs-lookup"><span data-stu-id="a5711-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="a5711-146">Dados numéricos que não [`Real`](xref:System.Data.SqlDbType) sejam do tipo [`Real`](xref:System.Data.SqlDbType)devem ser convertidos em .</span><span class="sxs-lookup"><span data-stu-id="a5711-146">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="a5711-147">O [`Real`](xref:System.Data.SqlDbType) tipo é representado como um valor [`Single`](xref:System.Single)de ponto flutuante de precisão única ou , o tipo de entrada esperado por algoritmos ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a5711-147">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="a5711-148">Nesta amostra, `NumBed` a coluna é um inteiro no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a5711-148">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="a5711-149">Usando `CAST` a função incorporada, ela é [`Real`](xref:System.Data.SqlDbType)convertida em .</span><span class="sxs-lookup"><span data-stu-id="a5711-149">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="a5711-150">Como `Price` a propriedade já [`Real`](xref:System.Data.SqlDbType) é do tipo que está carregada como está.</span><span class="sxs-lookup"><span data-stu-id="a5711-150">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="a5711-151">Use `Load` o método para carregar [`IDataView`](xref:Microsoft.ML.IDataView)os dados em um .</span><span class="sxs-lookup"><span data-stu-id="a5711-151">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="a5711-152">Carregar dados de outras fontes</span><span class="sxs-lookup"><span data-stu-id="a5711-152">Load data from other sources</span></span>

<span data-ttu-id="a5711-153">Além de carregar os dados armazenados em arquivos, o ML.NET dá suporte ao carregamento de dados de várias fontes que incluem, mas não se limitam a:</span><span class="sxs-lookup"><span data-stu-id="a5711-153">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="a5711-154">Coleções na memória</span><span class="sxs-lookup"><span data-stu-id="a5711-154">In-memory collections</span></span>
- <span data-ttu-id="a5711-155">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="a5711-155">JSON/XML</span></span>

<span data-ttu-id="a5711-156">Observe que, ao trabalhar com fontes de streaming, o ML.NET espera que a entrada esteja na forma de uma coleção em memória.</span><span class="sxs-lookup"><span data-stu-id="a5711-156">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="a5711-157">Portanto, ao trabalhar com fontes, como JSON/XML, formate os dados em uma coleção em memória.</span><span class="sxs-lookup"><span data-stu-id="a5711-157">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="a5711-158">Dada a coleção em memória a seguir:</span><span class="sxs-lookup"><span data-stu-id="a5711-158">Given the following in-memory collection:</span></span>

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

<span data-ttu-id="a5711-159">Carregue a coleção na [`IDataView`](xref:Microsoft.ML.IDataView) memória [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) em um com o método:</span><span class="sxs-lookup"><span data-stu-id="a5711-159">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5711-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)assume que [`IEnumerable`](xref:System.Collections.IEnumerable) o que ele carrega é seguro para rosca.</span><span class="sxs-lookup"><span data-stu-id="a5711-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="a5711-161">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a5711-161">Next steps</span></span>

- <span data-ttu-id="a5711-162">Para limpar ou processar dados, consulte [Preparar dados para a construção de um modelo](prepare-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="a5711-162">To clean or otherwise process data, see [Prepare data for building a model](prepare-data-ml-net.md).</span></span>
- <span data-ttu-id="a5711-163">Quando estiver pronto para construir um modelo, consulte [Treinar e avaliar um modelo](train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="a5711-163">When you're ready to build a model, see [Train and evaluate a model](train-machine-learning-model-ml-net.md).</span></span>
