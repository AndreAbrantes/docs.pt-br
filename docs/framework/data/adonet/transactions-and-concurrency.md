---
title: Transações e simultaneidade
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: 049e402345e1abbb46739e48c89101207a43bb27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191665"
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="597a9-102">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="597a9-102">Transactions and Concurrency</span></span>

<span data-ttu-id="597a9-103">Uma transação consiste em um único comando ou em um grupo de comandos executados como um pacote.</span><span class="sxs-lookup"><span data-stu-id="597a9-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="597a9-104">As transações permitem que você combine várias operações em uma única unidade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="597a9-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="597a9-105">Se uma falha ocorrer em determinado ponto na transação, todas as atualizações poderão ser revertidas para o estado em vigor antes da transação.</span><span class="sxs-lookup"><span data-stu-id="597a9-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="597a9-106">Uma transação deve estar de acordo com as propriedade ACID — atomicidade, consistência, isolamento e durabilidade — para garantir a consistência dos dados.</span><span class="sxs-lookup"><span data-stu-id="597a9-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="597a9-107">A maioria dos sistemas de banco de dados relacional, como o Microsoft SQL Server, oferece suporte a transações fornecendo recursos de bloqueio, registro e gerenciamento de transação sempre que um aplicativo cliente executa uma operação de atualização, inserção ou exclusão.</span><span class="sxs-lookup"><span data-stu-id="597a9-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="597a9-108">As transações que envolvem vários recursos podem reduzir a simultaneidade se os bloqueios forem mantidos muito longos.</span><span class="sxs-lookup"><span data-stu-id="597a9-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="597a9-109">Portanto, mantenha as transações curtas, o quanto possível.</span><span class="sxs-lookup"><span data-stu-id="597a9-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="597a9-110">Se uma transação envolver várias tabelas no mesmo banco de dados ou servidor, as transações explícitas em procedimentos armazenados geralmente apresentarão um melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="597a9-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="597a9-111">Você pode criar transações em procedimentos armazenados do SQL Server usando as instruções Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION` e `ROLLBACK TRANSACTION`.</span><span class="sxs-lookup"><span data-stu-id="597a9-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="597a9-112">Para obter mais informações, consulte os Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="597a9-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="597a9-113">As transações que envolvem diferentes gerenciadores de recursos, como uma transação entre SQL Server e Oracle, exigem uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="597a9-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="597a9-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="597a9-114">In This Section</span></span>  

 [<span data-ttu-id="597a9-115">Transações locais</span><span class="sxs-lookup"><span data-stu-id="597a9-115">Local Transactions</span></span>](local-transactions.md)  
 <span data-ttu-id="597a9-116">Demonstra como executar transações em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="597a9-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="597a9-117">Transações distribuídas</span><span class="sxs-lookup"><span data-stu-id="597a9-117">Distributed Transactions</span></span>](distributed-transactions.md)  
 <span data-ttu-id="597a9-118">Descreve como executar transações distribuídas no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="597a9-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="597a9-119">Integração de System.Transactions com o SQL Server</span><span class="sxs-lookup"><span data-stu-id="597a9-119">System.Transactions Integration with SQL Server</span></span>](system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="597a9-120">Descreve <xref:System.Transactions> a integração com o SQL Server para trabalhar com transações distribuídas.</span><span class="sxs-lookup"><span data-stu-id="597a9-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="597a9-121">Simultaneidade otimista</span><span class="sxs-lookup"><span data-stu-id="597a9-121">Optimistic Concurrency</span></span>](optimistic-concurrency.md)  
 <span data-ttu-id="597a9-122">Descreve a simultaneidade otimista e pessimista, e como você pode testar as violações de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="597a9-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597a9-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="597a9-123">See also</span></span>

- [<span data-ttu-id="597a9-124">Conceitos básicos de transação</span><span class="sxs-lookup"><span data-stu-id="597a9-124">Transaction Fundamentals</span></span>](../transactions/transaction-fundamentals.md)
- [<span data-ttu-id="597a9-125">Conectando a uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="597a9-125">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="597a9-126">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="597a9-126">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="597a9-127">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="597a9-127">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="597a9-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="597a9-128">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="597a9-129">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="597a9-129">ADO.NET Overview</span></span>](ado-net-overview.md)
