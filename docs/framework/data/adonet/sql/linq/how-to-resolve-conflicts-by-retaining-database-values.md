---
title: 'Como: resolver conflitos mantendo valores de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: b6f9b0308bcbf53a89ae0690ed44db0a364aef0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191691"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="e5b9b-102">Como: resolver conflitos mantendo valores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="e5b9b-102">How to: Resolve Conflicts by Retaining Database Values</span></span>

<span data-ttu-id="e5b9b-103">Para reconciliar diferenças entre valores esperados e reais de base de dados antes que você submeter tente novamente suas alterações, você pode usar <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> para manter os valores localizados na base de dados.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="e5b9b-104">Os valores atuais no modelo de objeto são substituídos em seguida.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="e5b9b-105">Para obter mais informações, consulte [simultaneidade otimista: visão geral](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e5b9b-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5b9b-106">Em todos os casos, o registro no cliente é atualizado primeiro recuperando os dados atualizados de base de dados.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="e5b9b-107">Esta ação certifique-se de que a seguir tentativa de atualização não falhará nas mesmas verificação de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5b9b-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5b9b-108">Example</span></span>  

 <span data-ttu-id="e5b9b-109">Nesse cenário, uma exceção é lançada de <xref:System.Data.Linq.ChangeConflictException> quando tenta User1 para enviar alterações, porque Usuário2 tiver alterado entretanto as colunas do assistente e departamento.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="e5b9b-110">A tabela a seguir mostra a situação.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="e5b9b-111">Gerente</span><span class="sxs-lookup"><span data-stu-id="e5b9b-111">Manager</span></span>|<span data-ttu-id="e5b9b-112">Assistente</span><span class="sxs-lookup"><span data-stu-id="e5b9b-112">Assistant</span></span>|<span data-ttu-id="e5b9b-113">department</span><span class="sxs-lookup"><span data-stu-id="e5b9b-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="e5b9b-114">Estado original de base de dados quando consultado por User1 e por Usuário2.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="e5b9b-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="e5b9b-115">Alfreds</span></span>|<span data-ttu-id="e5b9b-116">Maria</span><span class="sxs-lookup"><span data-stu-id="e5b9b-116">Maria</span></span>|<span data-ttu-id="e5b9b-117">Sales</span><span class="sxs-lookup"><span data-stu-id="e5b9b-117">Sales</span></span>|  
|<span data-ttu-id="e5b9b-118">User1 prepara-se para enviar essas alterações.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="e5b9b-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="e5b9b-119">Alfred</span></span>||<span data-ttu-id="e5b9b-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="e5b9b-120">Marketing</span></span>|  
|<span data-ttu-id="e5b9b-121">Usuário2 já tiver enviado essas alterações.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="e5b9b-122">Mary</span><span class="sxs-lookup"><span data-stu-id="e5b9b-122">Mary</span></span>|<span data-ttu-id="e5b9b-123">Serviço</span><span class="sxs-lookup"><span data-stu-id="e5b9b-123">Service</span></span>|  
  
 <span data-ttu-id="e5b9b-124">User1 decidir resolver esse conflito com os valores mais recentes de base de dados substitui os valores atuais no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="e5b9b-125">Quando User1 resolver o conflito usando <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, o resultado na base de dados é o seguinte na tabela:</span><span class="sxs-lookup"><span data-stu-id="e5b9b-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="e5b9b-126">Gerente</span><span class="sxs-lookup"><span data-stu-id="e5b9b-126">Manager</span></span>|<span data-ttu-id="e5b9b-127">Assistente</span><span class="sxs-lookup"><span data-stu-id="e5b9b-127">Assistant</span></span>|<span data-ttu-id="e5b9b-128">department</span><span class="sxs-lookup"><span data-stu-id="e5b9b-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="e5b9b-129">Novo estado após a resolução do conflito.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-129">New state after conflict resolution.</span></span>|<span data-ttu-id="e5b9b-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="e5b9b-130">Alfreds</span></span><br /><br /> <span data-ttu-id="e5b9b-131">(original)</span><span class="sxs-lookup"><span data-stu-id="e5b9b-131">(original)</span></span>|<span data-ttu-id="e5b9b-132">Mary</span><span class="sxs-lookup"><span data-stu-id="e5b9b-132">Mary</span></span><br /><br /> <span data-ttu-id="e5b9b-133">(de Usuário2)</span><span class="sxs-lookup"><span data-stu-id="e5b9b-133">(from User2)</span></span>|<span data-ttu-id="e5b9b-134">Serviço</span><span class="sxs-lookup"><span data-stu-id="e5b9b-134">Service</span></span><br /><br /> <span data-ttu-id="e5b9b-135">(de Usuário2)</span><span class="sxs-lookup"><span data-stu-id="e5b9b-135">(from User2)</span></span>|  
  
 <span data-ttu-id="e5b9b-136">O código exemplo a seguir mostra como substituir valores atuais no modelo de objeto com os valores de base de dados.</span><span class="sxs-lookup"><span data-stu-id="e5b9b-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="e5b9b-137">(Nenhuma inspeção ou manipulação personalizada de conflitos de membro individual ocorrem.)</span><span class="sxs-lookup"><span data-stu-id="e5b9b-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e5b9b-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="e5b9b-138">See also</span></span>

- [<span data-ttu-id="e5b9b-139">Como: gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="e5b9b-139">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
