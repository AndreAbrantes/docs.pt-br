---
title: Transformações de dados com LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: d20f5d826620ad8654ddf1e9471ecc894b2c0391
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408517"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="9e94a-102">Transformações de dados com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="9e94a-102">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="9e94a-103">A consulta integrada à linguagem (LINQ) não se refere apenas à recuperação de dados.</span><span class="sxs-lookup"><span data-stu-id="9e94a-103">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="9e94a-104">Também é uma ferramenta poderosa para transformação de dados.</span><span class="sxs-lookup"><span data-stu-id="9e94a-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="9e94a-105">Usando uma consulta LINQ, você pode usar uma sequência de origem como entrada e modificá-la de várias maneiras para criar uma nova sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="9e94a-105">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="9e94a-106">Você pode modificar a própria sequência sem modificar os respectivos elementos, classificando-os e agrupando-os.</span><span class="sxs-lookup"><span data-stu-id="9e94a-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="9e94a-107">Mas talvez o recurso mais poderoso das consultas LINQ seja a capacidade de criar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="9e94a-107">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="9e94a-108">Isso é feito na cláusula [select](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9e94a-108">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="9e94a-109">Por exemplo, é possível executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="9e94a-109">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="9e94a-110">Mesclar várias sequências de entrada em uma única sequência de saída que tenha um novo tipo.</span><span class="sxs-lookup"><span data-stu-id="9e94a-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="9e94a-111">Criar sequências de saída cujos elementos consistem em apenas uma ou várias propriedades de cada elemento da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="9e94a-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="9e94a-112">Criar sequências de saída cujos elementos consistem nos resultados das operações realizadas nos dados de origem.</span><span class="sxs-lookup"><span data-stu-id="9e94a-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="9e94a-113">Criar sequências de saída em um formato diferente.</span><span class="sxs-lookup"><span data-stu-id="9e94a-113">Create output sequences in a different format.</span></span> <span data-ttu-id="9e94a-114">Por exemplo, você pode transformar dados de linhas do SQL ou de arquivos de texto em XML.</span><span class="sxs-lookup"><span data-stu-id="9e94a-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="9e94a-115">Esses são apenas alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="9e94a-115">These are just several examples.</span></span> <span data-ttu-id="9e94a-116">É claro que essas transformações podem ser combinadas de diversas maneiras na mesma consulta.</span><span class="sxs-lookup"><span data-stu-id="9e94a-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="9e94a-117">Além disso, a sequência de saída de uma consulta pode ser usada como a sequência de entrada de uma nova consulta.</span><span class="sxs-lookup"><span data-stu-id="9e94a-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="9e94a-118">Ingressando Várias Entradas em uma Única Sequência de Saída</span><span class="sxs-lookup"><span data-stu-id="9e94a-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="9e94a-119">Você pode usar uma consulta LINQ para criar uma sequência de saída que contenha elementos de mais de uma sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="9e94a-119">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="9e94a-120">O exemplo a seguir mostra como combinar duas estruturas de dados na memória, mas os mesmos princípios podem ser aplicados para combinar dados de origens de XML, SQL ou DataSet.</span><span class="sxs-lookup"><span data-stu-id="9e94a-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="9e94a-121">Considere os dois tipos de classe a seguir:</span><span class="sxs-lookup"><span data-stu-id="9e94a-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="9e94a-122">O exemplo a seguir mostra a consulta:</span><span class="sxs-lookup"><span data-stu-id="9e94a-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="9e94a-123">Para obter mais informações, consulte [cláusula join](../../../language-reference/keywords/join-clause.md) e [cláusula select](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9e94a-123">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="9e94a-124">Selecionando um Subconjunto de Cada Elemento de Origem</span><span class="sxs-lookup"><span data-stu-id="9e94a-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="9e94a-125">Há duas maneiras principais de selecionar um subconjunto de cada elemento na sequência de origem:</span><span class="sxs-lookup"><span data-stu-id="9e94a-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="9e94a-126">Para selecionar apenas um membro do elemento de origem, use a operação de ponto.</span><span class="sxs-lookup"><span data-stu-id="9e94a-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="9e94a-127">No exemplo a seguir, suponha que um objeto `Customer` contém várias propriedades públicas, incluindo uma cadeia de caracteres denominada `City`.</span><span class="sxs-lookup"><span data-stu-id="9e94a-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="9e94a-128">Quando executada, essa consulta produzirá uma sequência de saída de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9e94a-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="9e94a-129">Para criar elementos que contenham mais de uma propriedade do elemento de origem, você pode usar um inicializador de objeto com um objeto nomeado ou um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="9e94a-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="9e94a-130">O exemplo a seguir mostra o uso de um tipo anônimo para encapsular duas propriedades de cada elemento `Customer`:</span><span class="sxs-lookup"><span data-stu-id="9e94a-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="9e94a-131">Para obter mais informações, consulte [Inicializadores de coleção e de objeto](../../classes-and-structs/object-and-collection-initializers.md) e [Tipos anônimos](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9e94a-131">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="9e94a-132">Transformando Objetos na Memória em XML</span><span class="sxs-lookup"><span data-stu-id="9e94a-132">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="9e94a-133">As consultas do LINQ facilitam a transformação de dados entre estruturas de dados na memória, bancos de dados SQL, ADO.NET e fluxos XML ou documentos.</span><span class="sxs-lookup"><span data-stu-id="9e94a-133">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="9e94a-134">O exemplo a seguir transforma objetos de uma estrutura de dados na memória em elementos XML.</span><span class="sxs-lookup"><span data-stu-id="9e94a-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="9e94a-135">O código produz a seguinte saída XML:</span><span class="sxs-lookup"><span data-stu-id="9e94a-135">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="9e94a-136">Para obter mais informações, consulte [Criando árvores XML em C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="9e94a-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="9e94a-137">Realizando Operações em Elementos de Origem</span><span class="sxs-lookup"><span data-stu-id="9e94a-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="9e94a-138">Uma sequência de saída pode não conter os elementos ou propriedades de elementos da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="9e94a-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="9e94a-139">Em vez disso, a saída pode ser uma sequência de valores que é calculada usando os elementos de origem como argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="9e94a-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span>

 <span data-ttu-id="9e94a-140">A consulta a seguir usará uma sequência de números que representam raios de círculos, calculará a área para cada raio e retornará uma sequência de saída contendo cadeias de caracteres formatadas com a área calculada.</span><span class="sxs-lookup"><span data-stu-id="9e94a-140">The following query will take a sequence of numbers that represent radii of circles, calculate the area for each radius, and return an output sequence containing strings formatted with the calculated area.</span></span>

 <span data-ttu-id="9e94a-141">Cada cadeia de caracteres da sequência de saída será formatada usando [interpolação de cadeia de caracteres](../../../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="9e94a-141">Each string for the output sequence will be formatted using [string interpolation](../../../language-reference/tokens/interpolated.md).</span></span> <span data-ttu-id="9e94a-142">Uma cadeia de caracteres interpolada terá uma `$` na frente das aspas de abertura da cadeia de caracteres, e as operações poderão ser executadas dentro das chaves colocadas dentro da cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="9e94a-142">An interpolated string will have a `$` in front of the string's opening quotation mark, and operations can be performed within curly braces placed inside the interpolated string.</span></span> <span data-ttu-id="9e94a-143">Depois que essas operações forem executadas, os resultados serão concatenados.</span><span class="sxs-lookup"><span data-stu-id="9e94a-143">Once those operations are performed, the results will be concatenated.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9e94a-144">Não há suporte para chamar métodos em expressões de consulta se a consulta será movida para outro domínio.</span><span class="sxs-lookup"><span data-stu-id="9e94a-144">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="9e94a-145">Por exemplo, você não pode chamar um método comum de C# no [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] porque o SQL Server não tem contexto para ele.</span><span class="sxs-lookup"><span data-stu-id="9e94a-145">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="9e94a-146">No entanto, você pode mapear procedimentos armazenados para os métodos e chamá-los.</span><span class="sxs-lookup"><span data-stu-id="9e94a-146">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="9e94a-147">Para obter mais informações, consulte [Procedimentos armazenados](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9e94a-147">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="9e94a-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e94a-148">See also</span></span>

- [<span data-ttu-id="9e94a-149">LINQ (Consulta Integrada à Linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="9e94a-149">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="9e94a-150">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9e94a-150">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="9e94a-151">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9e94a-151">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="9e94a-152">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9e94a-152">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="9e94a-153">Expressões de Consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="9e94a-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="9e94a-154">cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="9e94a-154">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
