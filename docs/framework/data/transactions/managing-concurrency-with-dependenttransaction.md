---
title: Gerenciar simultaneidade com DependentTransaction
description: Gerenciar a simultaneidade de transação, incluindo tarefas assíncronas, usando a classe DependentTransaction no .NET.
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 1e99006c127d83892155bd81e683f5995ac517ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186738"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="cf816-103">Gerenciar simultaneidade com DependentTransaction</span><span class="sxs-lookup"><span data-stu-id="cf816-103">Managing Concurrency with DependentTransaction</span></span>

<span data-ttu-id="cf816-104">O <xref:System.Transactions.Transaction> objeto é criado usando o <xref:System.Transactions.Transaction.DependentClone%2A> método.</span><span class="sxs-lookup"><span data-stu-id="cf816-104">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="cf816-105">Sua única finalidade é garantir que a transação não confirmada enquanto alguns outros trechos de código (por exemplo, um thread de trabalho) ainda estão executando o trabalho na transação.</span><span class="sxs-lookup"><span data-stu-id="cf816-105">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="cf816-106">Quando o trabalho realizado dentro da transação clonada é concluído e pronto para ser confirmada, ele pode notificar o criador da transação usando o <xref:System.Transactions.DependentTransaction.Complete%2A> método.</span><span class="sxs-lookup"><span data-stu-id="cf816-106">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="cf816-107">Portanto, você pode preservar a consistência e correção dos dados.</span><span class="sxs-lookup"><span data-stu-id="cf816-107">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="cf816-108">O <xref:System.Transactions.DependentTransaction> classe também pode ser usada para gerenciar a simultaneidade entre tarefas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="cf816-108">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="cf816-109">Nesse cenário, o pai pode continuar a executar qualquer código enquanto o clone dependente funciona em suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="cf816-109">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="cf816-110">Em outras palavras, a execução do pai não é bloqueada até que o dependente é concluída.</span><span class="sxs-lookup"><span data-stu-id="cf816-110">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="cf816-111">Criando um Clone dependente</span><span class="sxs-lookup"><span data-stu-id="cf816-111">Creating a Dependent Clone</span></span>  

 <span data-ttu-id="cf816-112">Para criar uma transação dependente, chame o <xref:System.Transactions.Transaction.DependentClone%2A> método e passar o <xref:System.Transactions.DependentCloneOption> enumeração como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf816-112">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="cf816-113">Esse parâmetro define o comportamento da transação se `Commit` é chamado na transação pai antes que o clone dependente indica que ele está pronto para a transação seja confirmada (chamando o <xref:System.Transactions.DependentTransaction.Complete%2A> método).</span><span class="sxs-lookup"><span data-stu-id="cf816-113">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="cf816-114">Os seguintes valores são válidos para esse parâmetro:</span><span class="sxs-lookup"><span data-stu-id="cf816-114">The following values are valid for this parameter:</span></span>  
  
- <span data-ttu-id="cf816-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> Cria uma transação dependente que bloqueia o processo de confirmação da transação pai até que a transação pai expire ou até que <xref:System.Transactions.DependentTransaction.Complete%2A> seja chamada em todos os dependentes indicando sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="cf816-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="cf816-116">Isso é útil quando o cliente não deseja que a transação do pai seja confirmada até que as transações dependentes sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="cf816-116">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="cf816-117">Se o pai concluir seu trabalho antes que a transação dependente e chamadas <xref:System.Transactions.CommittableTransaction.Commit%2A> na transação, o processo de confirmação será bloqueado em um estado onde trabalho adicional pode ser feito na transação e novas inscrições podem ser criadas, até que todos os da chamada dependentes <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf816-117">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="cf816-118">Assim que todos eles concluiu seu trabalho e chame <xref:System.Transactions.DependentTransaction.Complete%2A>, inicia o processo de confirmação da transação.</span><span class="sxs-lookup"><span data-stu-id="cf816-118">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
- <span data-ttu-id="cf816-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, por outro lado, o cria uma transação dependente que aborta automaticamente se <xref:System.Transactions.CommittableTransaction.Commit%2A> for chamado na transação pai antes de <xref:System.Transactions.DependentTransaction.Complete%2A> ser chamado.</span><span class="sxs-lookup"><span data-stu-id="cf816-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="cf816-120">Nesse caso, todo o trabalho feito na transação dependente está intacto no tempo de vida de uma transação e não tem a oportunidade de confirmar apenas uma parte dele.</span><span class="sxs-lookup"><span data-stu-id="cf816-120">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="cf816-121">O <xref:System.Transactions.DependentTransaction.Complete%2A> método deve ser chamado apenas uma vez quando seu aplicativo termina seu trabalho na transação dependente; Caso contrário, um <xref:System.InvalidOperationException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="cf816-121">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="cf816-122">Depois que essa chamada é invocada, você não deve tentar qualquer trabalho adicional na transação ou uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="cf816-122">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="cf816-123">O exemplo de código a seguir mostra como criar uma transação dependente para gerenciar duas tarefas simultâneas por uma transação dependente de clonagem e passá-la para um thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cf816-123">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);
    }  
  
    public void ThreadMethod(object transaction)
    {
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();
             dependentTransaction.Dispose();
        }  
    }  
  
//Client code
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 <span data-ttu-id="cf816-124">O código do cliente cria um escopo transacional que também define a transação de ambiente.</span><span class="sxs-lookup"><span data-stu-id="cf816-124">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="cf816-125">Você não deve passar a transação de ambiente para o thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cf816-125">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="cf816-126">Em vez disso, você deve clonar a transação (ambiente) atual chamando o <xref:System.Transactions.Transaction.DependentClone%2A> método na transação atual e passe o dependente para o thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cf816-126">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="cf816-127">O `ThreadMethod` método é executado no novo segmento.</span><span class="sxs-lookup"><span data-stu-id="cf816-127">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="cf816-128">O cliente inicia um novo thread, passando a transação dependente como o `ThreadMethod` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf816-128">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="cf816-129">Como a transação dependente é criada com <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, terá a garantia de que a transação não pode ser confirmada até que todos os do trabalho transacional feito no segundo thread é concluído e <xref:System.Transactions.DependentTransaction.Complete%2A> é chamado na transação dependente.</span><span class="sxs-lookup"><span data-stu-id="cf816-129">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="cf816-130">Isso significa que, se o escopo do cliente terminar (quando tentar descartar o objeto de transação no final da `using` instrução) antes que o novo thread chame <xref:System.Transactions.DependentTransaction.Complete%2A> na transação dependente, o código do cliente será bloqueado até que <xref:System.Transactions.DependentTransaction.Complete%2A> seja chamado no dependente.</span><span class="sxs-lookup"><span data-stu-id="cf816-130">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the `using` statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="cf816-131">Em seguida, a transação pode concluir a confirmação ou anulação.</span><span class="sxs-lookup"><span data-stu-id="cf816-131">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="cf816-132">Problemas de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="cf816-132">Concurrency Issues</span></span>  

 <span data-ttu-id="cf816-133">Existem alguns problemas de simultaneidade adicionais que precisam ser consideradas ao usar o <xref:System.Transactions.DependentTransaction> classe:</span><span class="sxs-lookup"><span data-stu-id="cf816-133">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
- <span data-ttu-id="cf816-134">Se o thread de trabalho reverte a transação, mas o pai tenta confirmar, um <xref:System.Transactions.TransactionAbortedException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="cf816-134">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
- <span data-ttu-id="cf816-135">Você deve criar um novo clone dependente para cada thread de trabalho na transação.</span><span class="sxs-lookup"><span data-stu-id="cf816-135">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="cf816-136">Não passam o mesmo clone dependente em vários threads, porque apenas um deles pode chamar <xref:System.Transactions.DependentTransaction.Complete%2A> nele.</span><span class="sxs-lookup"><span data-stu-id="cf816-136">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
- <span data-ttu-id="cf816-137">Se o thread de trabalho gera um novo thread de trabalho, certifique-se de criar um clone dependente do clone dependente e passá-lo para o novo thread.</span><span class="sxs-lookup"><span data-stu-id="cf816-137">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf816-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="cf816-138">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
