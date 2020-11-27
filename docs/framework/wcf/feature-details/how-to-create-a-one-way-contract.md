---
title: 'Como: criar um contrato unidirecional'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 7f0285ba4824ac842b3644d0834782139fd90657
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268684"
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="40cbd-102">Como: criar um contrato unidirecional</span><span class="sxs-lookup"><span data-stu-id="40cbd-102">How to: Create a One-Way Contract</span></span>

<span data-ttu-id="40cbd-103">Este tópico mostra as etapas básicas para criar métodos que usam um contrato unidirecional.</span><span class="sxs-lookup"><span data-stu-id="40cbd-103">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="40cbd-104">Esses métodos invocam operações em um serviço de Windows Communication Foundation (WCF) de um cliente, mas não esperam uma resposta.</span><span class="sxs-lookup"><span data-stu-id="40cbd-104">Such methods invoke operations on a Windows Communication Foundation (WCF) service from a client but do not expect a reply.</span></span> <span data-ttu-id="40cbd-105">Esse tipo de contrato pode ser usado, por exemplo, para publicar notificações para muitos assinantes.</span><span class="sxs-lookup"><span data-stu-id="40cbd-105">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="40cbd-106">Você também pode usar contratos unidirecionais ao criar um contrato duplex (bidirecional), que permite que clientes e servidores se comuniquem entre si de forma independente, de forma que seja possível iniciar chamadas para o outro.</span><span class="sxs-lookup"><span data-stu-id="40cbd-106">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="40cbd-107">Isso pode permitir, em particular, que o servidor faça chamadas unidirecionais para o cliente que o cliente pode tratar como eventos.</span><span class="sxs-lookup"><span data-stu-id="40cbd-107">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="40cbd-108">Para obter informações detalhadas sobre como especificar métodos unidirecionais, consulte a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade e a <xref:System.ServiceModel.OperationContractAttribute> classe.</span><span class="sxs-lookup"><span data-stu-id="40cbd-108">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 <span data-ttu-id="40cbd-109">Para obter mais informações sobre como criar um aplicativo cliente para um contrato duplex, consulte [como acessar serviços com One-Way e contratos de Request-Reply](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="40cbd-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="40cbd-110">Para obter um exemplo funcional, consulte o exemplo [unidirecional](../samples/one-way.md) .</span><span class="sxs-lookup"><span data-stu-id="40cbd-110">For a working sample, see the [One-Way](../samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="40cbd-111">Para criar um contrato unidirecional</span><span class="sxs-lookup"><span data-stu-id="40cbd-111">To create a one-way contract</span></span>  
  
1. <span data-ttu-id="40cbd-112">Crie o contrato de serviço aplicando a <xref:System.ServiceModel.ServiceContractAttribute> classe à interface que define os métodos que o serviço deve implementar.</span><span class="sxs-lookup"><span data-stu-id="40cbd-112">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2. <span data-ttu-id="40cbd-113">Indique quais métodos na interface um cliente pode invocar aplicando a <xref:System.ServiceModel.OperationContractAttribute> classe a eles.</span><span class="sxs-lookup"><span data-stu-id="40cbd-113">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3. <span data-ttu-id="40cbd-114">Designe operações que não devem ter nenhuma saída (nenhum valor de retorno e nenhum parâmetro out ou ref) como unidirecional definindo a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade como `true` .</span><span class="sxs-lookup"><span data-stu-id="40cbd-114">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="40cbd-115">Observe que as operações que carregam a <xref:System.ServiceModel.OperationContractAttribute> classe atendem a um contrato de solicitação-resposta por padrão, pois a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade é `false` por padrão.</span><span class="sxs-lookup"><span data-stu-id="40cbd-115">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="40cbd-116">Portanto, você deve especificar explicitamente o valor da propriedade de atributo como `true` se desejar um contrato unidirecional para o método.</span><span class="sxs-lookup"><span data-stu-id="40cbd-116">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40cbd-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40cbd-117">Example</span></span>  

 <span data-ttu-id="40cbd-118">O exemplo de código a seguir define um contrato para um serviço que inclui vários métodos unidirecionais.</span><span class="sxs-lookup"><span data-stu-id="40cbd-118">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="40cbd-119">Todos os métodos têm contratos unidirecionais, exceto `Equals` , que assume a solicitação-Reply e retorna um resultado.</span><span class="sxs-lookup"><span data-stu-id="40cbd-119">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="40cbd-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="40cbd-120">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="40cbd-121">Serviços de implantação e projeção</span><span class="sxs-lookup"><span data-stu-id="40cbd-121">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="40cbd-122">Como definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="40cbd-122">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="40cbd-123">Sessão</span><span class="sxs-lookup"><span data-stu-id="40cbd-123">Session</span></span>](../samples/session.md)
- [<span data-ttu-id="40cbd-124">Como: criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="40cbd-124">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
