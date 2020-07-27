---
title: LINQ e cadeias de caracteres (C#)
description: O LINQ pode consultar e transformar cadeias de caracteres e coleções de cadeias de caracteres. Você pode combinar consultas LINQ com funções de cadeia de caracteres C# e expressões regulares.
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c515a0c56ad6473f93c6339540e4ed0245bb5bd2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165617"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="d57c9-104">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-104">LINQ and strings (C#)</span></span>

<span data-ttu-id="d57c9-105">A LINQ pode ser usada para consultar e transformar as cadeias de caracteres e coleções de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d57c9-105">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="d57c9-106">Ele pode ser especialmente útil com os dados semiestruturados em arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="d57c9-106">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="d57c9-107">Consultas LINQ podem ser combinadas com expressões regulares e funções de cadeia de caracteres tradicionais.</span><span class="sxs-lookup"><span data-stu-id="d57c9-107">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="d57c9-108">Por exemplo, você pode usar o método <xref:System.String.Split%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> para criar uma matriz de cadeias de caracteres que você pode consultar ou modificar usando o LINQ.</span><span class="sxs-lookup"><span data-stu-id="d57c9-108">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="d57c9-109">Você pode usar o método <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> na cláusula `where` de uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="d57c9-109">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="d57c9-110">E você pode usar o LINQ para consultar ou modificar os resultados de <xref:System.Text.RegularExpressions.MatchCollection> retornados por uma expressão regular.</span><span class="sxs-lookup"><span data-stu-id="d57c9-110">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="d57c9-111">Você também pode usar as técnicas descritas nessa seção para transformar dados de texto semiestruturados em XML.</span><span class="sxs-lookup"><span data-stu-id="d57c9-111">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="d57c9-112">Para obter mais informações, consulte [como gerar XML a partir de arquivos CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="d57c9-112">For more information, see [How to generate XML from CSV files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="d57c9-113">Os exemplos nesta seção se enquadram em duas categorias:</span><span class="sxs-lookup"><span data-stu-id="d57c9-113">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="d57c9-114">Consultando um bloco de texto</span><span class="sxs-lookup"><span data-stu-id="d57c9-114">Querying a block of text</span></span>

<span data-ttu-id="d57c9-115">Consultar, analisar e modificar os blocos de texto dividindo-os em uma matriz de cadeias de caracteres menores consultáveis usando o método <xref:System.String.Split%2A?displayProperty=nameWithType> ou o método <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d57c9-115">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d57c9-116">Você pode dividir o texto de origem em palavras, frases, parágrafos, páginas ou quaisquer outros critérios e, em seguida, executar divisões adicionais se elas forem necessárias em sua consulta.</span><span class="sxs-lookup"><span data-stu-id="d57c9-116">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="d57c9-117">Como contar ocorrências de uma palavra em uma cadeia de caracteres (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-117">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="d57c9-118">Mostra como usar a LINQ para consultas simples em texto.</span><span class="sxs-lookup"><span data-stu-id="d57c9-118">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="d57c9-119">Como consultar frases que contêm um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-119">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="d57c9-120">Mostra como dividir os arquivos de texto em limites arbitrários e como executar consultas em cada parte.</span><span class="sxs-lookup"><span data-stu-id="d57c9-120">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="d57c9-121">Como consultar caracteres em uma cadeia (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-121">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="d57c9-122">Demonstra que uma cadeia de caracteres é de um tipo passível de consulta.</span><span class="sxs-lookup"><span data-stu-id="d57c9-122">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="d57c9-123">Como combinar consultas LINQ com expressões regulares (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-123">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="d57c9-124">Mostra como usar expressões regulares em consultas LINQ para correspondência de padrões complexos em resultados de consulta filtrados.</span><span class="sxs-lookup"><span data-stu-id="d57c9-124">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="d57c9-125">Consultando dados semiestruturados em formato de texto</span><span class="sxs-lookup"><span data-stu-id="d57c9-125">Querying semi-structured data in text format</span></span>

<span data-ttu-id="d57c9-126">Muitos tipos diferentes de arquivos de texto consistem em uma série de linhas, geralmente com formatação semelhante, como arquivos delimitados por tabulação ou vírgula ou linhas de comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="d57c9-126">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="d57c9-127">Depois de ler um arquivo de texto na memória, você pode usar a LINQ para consultar e/ou modificar as linhas.</span><span class="sxs-lookup"><span data-stu-id="d57c9-127">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="d57c9-128">As consultas LINQ também simplificam a tarefa de combinar dados de várias fontes.</span><span class="sxs-lookup"><span data-stu-id="d57c9-128">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="d57c9-129">Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-129">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="d57c9-130">Mostra como localizar todas as cadeias de caracteres que estão presentes em uma lista, mas não na outra.</span><span class="sxs-lookup"><span data-stu-id="d57c9-130">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="d57c9-131">Como classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-131">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="d57c9-132">Mostra como classificar linhas de texto com base em qualquer palavra ou campo.</span><span class="sxs-lookup"><span data-stu-id="d57c9-132">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="d57c9-133">Como reordenar os campos de um arquivo delimitado (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-133">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="d57c9-134">Mostra como reordenar campos em uma linha em um arquivo .csv.</span><span class="sxs-lookup"><span data-stu-id="d57c9-134">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="d57c9-135">Como combinar e comparar coleções de cadeias de caracteres (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-135">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="d57c9-136">Mostra como combinar listas de cadeias de caracteres de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="d57c9-136">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="d57c9-137">Como preencher coleções de objetos de várias fontes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="d57c9-138">Mostra como criar coleções de objetos usando vários arquivos de texto como fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="d57c9-138">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="d57c9-139">Como unir conteúdo de arquivos diferentes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-139">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="d57c9-140">Mostra como combinar cadeias de caracteres em duas listas em uma única cadeia de caracteres usando uma chave correspondente.</span><span class="sxs-lookup"><span data-stu-id="d57c9-140">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="d57c9-141">Como dividir um arquivo em vários arquivos usando grupos (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-141">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="d57c9-142">Mostra como criar novos arquivos usando um único arquivo como uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d57c9-142">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="d57c9-143">Como computar valores de coluna em um arquivo de texto CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-143">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="d57c9-144">Mostra como executar cálculos matemáticos em dados de texto em arquivos .csv.</span><span class="sxs-lookup"><span data-stu-id="d57c9-144">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="d57c9-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="d57c9-145">See also</span></span>

- [<span data-ttu-id="d57c9-146">LINQ (Consulta Integrada à Linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="d57c9-146">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="d57c9-147">Como gerar XML de arquivos CSV</span><span class="sxs-lookup"><span data-stu-id="d57c9-147">How to generate XML from CSV files</span></span>](how-to-generate-xml-from-csv-files.md)
