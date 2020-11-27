---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 76cc619aed4ba2b944a8d11dc454a40368a4068c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269074"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="c144c-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="c144c-102">OperationBehaviorAttribute</span></span>

<span data-ttu-id="c144c-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="c144c-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c144c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c144c-104">Syntax</span></span>  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c144c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c144c-105">Methods</span></span>  

 <span data-ttu-id="c144c-106">A classe OperationBehaviorAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="c144c-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c144c-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c144c-107">Properties</span></span>  

 <span data-ttu-id="c144c-108">A classe OperationBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c144c-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="c144c-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="c144c-109">AutoDisposeParameters</span></span>  

 <span data-ttu-id="c144c-110">Tipo de dados: booliano</span><span class="sxs-lookup"><span data-stu-id="c144c-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="c144c-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c144c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c144c-112">O estado do recurso de disposição automática para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c144c-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="c144c-113">Representação</span><span class="sxs-lookup"><span data-stu-id="c144c-113">Impersonation</span></span>  

 <span data-ttu-id="c144c-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c144c-114">Data type: string</span></span>  
  
 <span data-ttu-id="c144c-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c144c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c144c-116">Indica o nível de representação do chamador ao qual a operação dá suporte.</span><span class="sxs-lookup"><span data-stu-id="c144c-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="c144c-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="c144c-117">ReleaseInstanceMode</span></span>  

 <span data-ttu-id="c144c-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c144c-118">Data type: string</span></span>  
  
 <span data-ttu-id="c144c-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c144c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c144c-120">Indica quando no decorrer de uma invocação de operação para reciclar o objeto.</span><span class="sxs-lookup"><span data-stu-id="c144c-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="c144c-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="c144c-121">TransactionAutoComplete</span></span>  

 <span data-ttu-id="c144c-122">Tipo de dados: booliano</span><span class="sxs-lookup"><span data-stu-id="c144c-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="c144c-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c144c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c144c-124">Indica se a transação atual deve ser confirmada automaticamente se não ocorrer nenhuma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="c144c-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="c144c-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="c144c-125">TransactionScopeRequired</span></span>  

 <span data-ttu-id="c144c-126">Tipo de dados: booliano</span><span class="sxs-lookup"><span data-stu-id="c144c-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="c144c-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="c144c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c144c-128">Indica se a operação requer uma transação.</span><span class="sxs-lookup"><span data-stu-id="c144c-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c144c-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c144c-129">Requirements</span></span>  
  
|<span data-ttu-id="c144c-130">MOF</span><span class="sxs-lookup"><span data-stu-id="c144c-130">MOF</span></span>|<span data-ttu-id="c144c-131">Declarado em ServiceModel. mof.</span><span class="sxs-lookup"><span data-stu-id="c144c-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c144c-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="c144c-132">Namespace</span></span>|<span data-ttu-id="c144c-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c144c-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c144c-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="c144c-134">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
