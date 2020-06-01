---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: c488e49283f3e30ea729adf111fd9ca297039838
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241559"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="36e25-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="36e25-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="36e25-103">O termo "LINQ to Objects" refere-se ao uso de consultas LINQ com qualquer coleção <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> diretamente, sem o uso de uma API ou provedor LINQ intermediário como o [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) ou [LINQ to XML](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36e25-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="36e25-104">Você pode usar o LINQ para consultar qualquer coleção enumerável ​​como <xref:System.Collections.Generic.List%601>, <xref:System.Array> ou <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="36e25-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="36e25-105">A coleção pode ser definida pelo usuário ou pode ser retornada por uma API do .NET.</span><span class="sxs-lookup"><span data-stu-id="36e25-105">The collection may be user-defined or may be returned by a .NET API.</span></span>  
  
 <span data-ttu-id="36e25-106">Basicamente, o LINQ to Objects representa uma nova abordagem às coleções.</span><span class="sxs-lookup"><span data-stu-id="36e25-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="36e25-107">Na forma antiga, você precisava escrever loops `foreach` complexos que especificavam como recuperar dados de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="36e25-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="36e25-108">Na abordagem da LINQ, você escreve o código declarativo que descreve o que você deseja recuperar.</span><span class="sxs-lookup"><span data-stu-id="36e25-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="36e25-109">Além disso, as consultas LINQ oferecem três principais vantagens sobre os loops `foreach` tradicionais:</span><span class="sxs-lookup"><span data-stu-id="36e25-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="36e25-110">Elas são mais concisas e legíveis, especialmente quando você filtra várias condições.</span><span class="sxs-lookup"><span data-stu-id="36e25-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="36e25-111">Elas fornecem poderosos recursos de filtragem, ordenação e agrupamento com um mínimo de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="36e25-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="36e25-112">Elas podem ser movidas para outras fontes de dados com pouca ou nenhuma modificação.</span><span class="sxs-lookup"><span data-stu-id="36e25-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="36e25-113">Em geral, quanto mais complexa a operação que você deseja executar sobre os dados, maior benefício você perceberá usando consultas LINQs em vez de técnicas tradicionais de iteração.</span><span class="sxs-lookup"><span data-stu-id="36e25-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="36e25-114">O objetivo desta seção é demonstrar a abordagem LINQ com alguns exemplos selecionados.</span><span class="sxs-lookup"><span data-stu-id="36e25-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="36e25-115">Não pretendemos que ela seja detalhada.</span><span class="sxs-lookup"><span data-stu-id="36e25-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36e25-116">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="36e25-116">In This Section</span></span>  
 [<span data-ttu-id="36e25-117">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="36e25-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="36e25-118">Explica como a LINQ pode ser usada para consultar e transformar cadeias de caracteres e coleções de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="36e25-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="36e25-119">Também inclui links para tópicos que demonstram esses princípios.</span><span class="sxs-lookup"><span data-stu-id="36e25-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="36e25-120">LINQ e reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="36e25-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="36e25-121">Contém um link para um exemplo que demonstra como a LINQ usa a reflexão.</span><span class="sxs-lookup"><span data-stu-id="36e25-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="36e25-122">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="36e25-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="36e25-123">Explica como a LINQ pode ser usada para interagir com sistemas de arquivos.</span><span class="sxs-lookup"><span data-stu-id="36e25-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="36e25-124">Também inclui links para tópicos que demonstram esses conceitos.</span><span class="sxs-lookup"><span data-stu-id="36e25-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="36e25-125">Como consultar uma ArrayList com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="36e25-125">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="36e25-126">Demonstra como consultar um ArrayList no C#.</span><span class="sxs-lookup"><span data-stu-id="36e25-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="36e25-127">Como adicionar métodos personalizados para consultas LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="36e25-127">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="36e25-128">Explica como estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando os métodos de extensão à interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="36e25-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="36e25-129">LINQ (Consulta Integrada à Linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="36e25-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="36e25-130">Fornece links para tópicos que explicam a LINQ e fornecem exemplos de código que realizam consultas.</span><span class="sxs-lookup"><span data-stu-id="36e25-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
