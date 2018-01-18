---
title: Linguagem Entity SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1618ff37ffd2b25140196a42d49d5a01f7e9da90
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-sql-language"></a><span data-ttu-id="ceae3-102">Linguagem Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ceae3-102">Entity SQL Language</span></span>
<span data-ttu-id="ceae3-103">O Entity SQL é uma linguagem de consulta independente de armazenamento semelhante ao SQL.</span><span class="sxs-lookup"><span data-stu-id="ceae3-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="ceae3-104">O Entity SQL permite que você consulte dados de entidade, como objetos ou em forma de tabela.</span><span class="sxs-lookup"><span data-stu-id="ceae3-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="ceae3-105">Você deve considerar o uso do Entity SQL nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="ceae3-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="ceae3-106">Quando uma consulta deve ser construída dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ceae3-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="ceae3-107">Nesse caso, você também deve considerar o uso dos métodos do construtor de consultas de <xref:System.Data.Objects.ObjectQuery%601>, em vez de construir uma cadeia de caracteres de consulta Entity SQL em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ceae3-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="ceae3-108">Quando você deseja definir uma consulta como parte da definição do modelo.</span><span class="sxs-lookup"><span data-stu-id="ceae3-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="ceae3-109">Somente o Entity SQL tem suporte em um modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="ceae3-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="ceae3-110">Para obter mais informações, consulte [QueryView elemento (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span><span class="sxs-lookup"><span data-stu-id="ceae3-110">For more information, see [QueryView Element (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span></span>  
  
-   <span data-ttu-id="ceae3-111">Ao usar EntityClient para retornar dados de entidade somente leitura como conjuntos de linhas usando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ceae3-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="ceae3-112">Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="ceae3-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="ceae3-113">Se você já for um especialista em linguagens de consulta baseadas em SQL, o Entity SQL poderá parecer a opção mais natural para você.</span><span class="sxs-lookup"><span data-stu-id="ceae3-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="ceae3-114">Usando Entity SQL com o provedor EntityClient</span><span class="sxs-lookup"><span data-stu-id="ceae3-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="ceae3-115">Se você desejar usar o Entity SQL com o provedor EntityClient, consulte os seguintes tópicos para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="ceae3-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="ceae3-116">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ceae3-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="ceae3-117">Como compilar uma cadeia de conexão EntityConnection</span><span class="sxs-lookup"><span data-stu-id="ceae3-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="ceae3-118">Como executar uma consulta que retorna resultados PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="ceae3-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="ceae3-119">Como executar uma consulta que retorna resultados StructuralType</span><span class="sxs-lookup"><span data-stu-id="ceae3-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="ceae3-120">Como executar uma consulta que retorna resultados RefType</span><span class="sxs-lookup"><span data-stu-id="ceae3-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="ceae3-121">Como executar uma consulta que retorna tipos complexos</span><span class="sxs-lookup"><span data-stu-id="ceae3-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="ceae3-122">Como executar uma consulta que retorna coleções aninhadas</span><span class="sxs-lookup"><span data-stu-id="ceae3-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="ceae3-123">Como executar uma consulta Entity SQL parametrizada usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="ceae3-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="ceae3-124">Como executar um procedimento armazenado parametrizado usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="ceae3-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="ceae3-125">Como executar uma consulta polimorfa</span><span class="sxs-lookup"><span data-stu-id="ceae3-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="ceae3-126">Como navegar em relações com o operador Navigate</span><span class="sxs-lookup"><span data-stu-id="ceae3-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="ceae3-127">Usando o Entity SQL com consultas de objetos</span><span class="sxs-lookup"><span data-stu-id="ceae3-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="ceae3-128">Se você desejar usar o Entity SQL com consultas de objetos, consulte os seguintes tópicos para obter mais informações:</span><span class="sxs-lookup"><span data-stu-id="ceae3-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="ceae3-129">Como: executar uma consulta que retorna os objetos de tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="ceae3-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](http://msdn.microsoft.com/en-us/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="ceae3-130">Como: executar uma consulta parametrizada</span><span class="sxs-lookup"><span data-stu-id="ceae3-130">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="ceae3-131">Como: navegar em relações usando propriedades de navegação</span><span class="sxs-lookup"><span data-stu-id="ceae3-131">How to: Navigate Relationships Using Navigation Properties</span></span>](http://msdn.microsoft.com/en-us/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="ceae3-132">Como: chamar uma função definida pelo usuário</span><span class="sxs-lookup"><span data-stu-id="ceae3-132">How to: Call a User-Defined Function</span></span>](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="ceae3-133">Como: filtrar dados</span><span class="sxs-lookup"><span data-stu-id="ceae3-133">How to: Filter Data</span></span>](http://msdn.microsoft.com/en-us/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="ceae3-134">Como: classificar dados</span><span class="sxs-lookup"><span data-stu-id="ceae3-134">How to: Sort Data</span></span>](http://msdn.microsoft.com/en-us/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="ceae3-135">Como: agrupar dados</span><span class="sxs-lookup"><span data-stu-id="ceae3-135">How to: Group Data</span></span>](http://msdn.microsoft.com/en-us/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="ceae3-136">Como: dados de agregação</span><span class="sxs-lookup"><span data-stu-id="ceae3-136">How to: Aggregate Data</span></span>](http://msdn.microsoft.com/en-us/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="ceae3-137">Como: executar uma consulta que retorna objetos de tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="ceae3-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/en-us/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="ceae3-138">Como: executar uma consulta que retorna uma coleção de tipos primitivos</span><span class="sxs-lookup"><span data-stu-id="ceae3-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](http://msdn.microsoft.com/en-us/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="ceae3-139">Como: consultar objetos relacionados em uma EntityCollection</span><span class="sxs-lookup"><span data-stu-id="ceae3-139">How to: Query Related Objects in an EntityCollection</span></span>](http://msdn.microsoft.com/en-us/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="ceae3-140">Como: ordenar a união de duas consultas</span><span class="sxs-lookup"><span data-stu-id="ceae3-140">How to: Order the Union of Two Queries</span></span>](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="ceae3-141">Como: resultados da página por meio de consulta</span><span class="sxs-lookup"><span data-stu-id="ceae3-141">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="ceae3-142">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ceae3-142">In This Section</span></span>  
 [<span data-ttu-id="ceae3-143">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ceae3-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="ceae3-144">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ceae3-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="ceae3-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ceae3-145">See Also</span></span>  
 [<span data-ttu-id="ceae3-146">Entity Framework do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ceae3-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="ceae3-147">Referência de Linguagem</span><span class="sxs-lookup"><span data-stu-id="ceae3-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
