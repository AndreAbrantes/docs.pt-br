---
title: 'Exemplos de sintaxe da consulta com base em método: Operadores de conversão (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: b3c746f715f40f4c134185fa0cf8e6e115e0067b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164643"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="daf3c-102">Exemplos de sintaxe da consulta com base em método: Operadores de conversão (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="daf3c-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="daf3c-103">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, e métodos de <xref:System.Linq.Enumerable.ToList%2A> para executar imediatamente uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="daf3c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="daf3c-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="daf3c-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="daf3c-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="daf3c-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="daf3c-106">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="daf3c-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="daf3c-107">Para obter mais informações, consulte [como: criar um projeto de LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="daf3c-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="daf3c-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="daf3c-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="daf3c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="daf3c-109">Example</span></span>  

 <span data-ttu-id="daf3c-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.ToArray%2A> para avaliar imediatamente uma sequência em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="daf3c-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="daf3c-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="daf3c-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="daf3c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="daf3c-112">Example</span></span>  

 <span data-ttu-id="daf3c-113">Este exemplo usa o método de <xref:System.Linq.Enumerable.ToDictionary%2A> para avaliar imediatamente uma sequência e uma expressão chave relacionadas em um dicionário.</span><span class="sxs-lookup"><span data-stu-id="daf3c-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="daf3c-114">ToList</span><span class="sxs-lookup"><span data-stu-id="daf3c-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="daf3c-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="daf3c-115">Example</span></span>  

 <span data-ttu-id="daf3c-116">Este exemplo usa o método de <xref:System.Linq.Enumerable.ToList%2A> para avaliar imediatamente uma sequência em <xref:System.Collections.Generic.List%601>, onde `T` é do tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="daf3c-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="daf3c-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="daf3c-117">See also</span></span>

- [<span data-ttu-id="daf3c-118">Carregando dados em um DataSet</span><span class="sxs-lookup"><span data-stu-id="daf3c-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="daf3c-119">LINQ para exemplos de DataSet</span><span class="sxs-lookup"><span data-stu-id="daf3c-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="daf3c-120">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="daf3c-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="daf3c-121">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daf3c-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
