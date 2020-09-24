---
title: Formular junções e consultas entre produtos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 1527ad26524dbef3ac73b92e136cd22e33046483
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155881"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="96899-102">Formular junções e consultas entre produtos</span><span class="sxs-lookup"><span data-stu-id="96899-102">Formulate Joins and Cross-Product Queries</span></span>

<span data-ttu-id="96899-103">Os exemplos a seguir mostram como combinar resultados de várias tabelas.</span><span class="sxs-lookup"><span data-stu-id="96899-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96899-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-104">Example</span></span>  

 <span data-ttu-id="96899-105">O exemplo a seguir usa a navegação de chave estrangeira na `From` cláusula em Visual Basic ( `from` cláusula em C#) para selecionar todos os pedidos de clientes em Londres.</span><span class="sxs-lookup"><span data-stu-id="96899-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="96899-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-106">Example</span></span>  

 <span data-ttu-id="96899-107">O exemplo a seguir usa a navegação de chave estrangeira na `Where` cláusula em Visual Basic ( `where` cláusula em C#) para filtrar por indisponibilidade de estoque `Products` cujo `Supplier` está na Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="96899-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="96899-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-108">Example</span></span>  

 <span data-ttu-id="96899-109">O exemplo a seguir usa a navegação de chave estrangeira na `From` cláusula em Visual Basic ( `from` cláusula em C#) para filtrar os funcionários em Seattle e listar seus territórios.</span><span class="sxs-lookup"><span data-stu-id="96899-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="96899-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-110">Example</span></span>  

 <span data-ttu-id="96899-111">O exemplo a seguir usa a navegação de chave estrangeira na `Select` cláusula em Visual Basic ( `select` cláusula em C#) para filtrar os pares de funcionários em que um funcionário se reporta ao outro e onde ambos os funcionários são do mesmo `City` .</span><span class="sxs-lookup"><span data-stu-id="96899-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="96899-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-112">Example</span></span>  

 <span data-ttu-id="96899-113">O exemplo a seguir Visual Basic procura todos os clientes e pedidos, garante que os pedidos sejam correspondidos aos clientes e garante que, para cada cliente nessa lista, um nome de contato seja fornecido.</span><span class="sxs-lookup"><span data-stu-id="96899-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="96899-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-114">Example</span></span>  

 <span data-ttu-id="96899-115">O exemplo a seguir une explicitamente duas tabelas e os resultados dos projetos das duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="96899-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="96899-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-116">Example</span></span>  

 <span data-ttu-id="96899-117">O exemplo a seguir une explicitamente três tabelas e os resultados dos projetos de cada uma delas.</span><span class="sxs-lookup"><span data-stu-id="96899-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="96899-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-118">Example</span></span>  

 <span data-ttu-id="96899-119">O exemplo a seguir mostra como obter um `LEFT OUTER JOIN` usando `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="96899-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="96899-120">O método `DefaultIfEmpty()` retorna nulo quando não há nenhum `Order` para o `Employee`.</span><span class="sxs-lookup"><span data-stu-id="96899-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="96899-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-121">Example</span></span>  

 <span data-ttu-id="96899-122">O exemplo a seguir projeta uma expressão `let` resultante de uma junção.</span><span class="sxs-lookup"><span data-stu-id="96899-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="96899-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-123">Example</span></span>  

 <span data-ttu-id="96899-124">O exemplo a seguir mostra um `join` com uma chave composta.</span><span class="sxs-lookup"><span data-stu-id="96899-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="96899-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96899-125">Example</span></span>  

 <span data-ttu-id="96899-126">O exemplo a seguir mostra como construir um `join` onde um lado é anulável e o outro não.</span><span class="sxs-lookup"><span data-stu-id="96899-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="96899-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="96899-127">See also</span></span>

- [<span data-ttu-id="96899-128">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="96899-128">Query Examples</span></span>](query-examples.md)
