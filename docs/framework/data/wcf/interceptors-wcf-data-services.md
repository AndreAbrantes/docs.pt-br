---
title: Interceptores (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 64c5c82f33daf677e58d49655897c392f1f7b7f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204391"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="ca7bc-102">Interceptores (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ca7bc-102">Interceptors (WCF Data Services)</span></span>

<span data-ttu-id="ca7bc-103">WCF Data Services permite que um aplicativo intercepte mensagens de solicitação para que você possa adicionar lógica personalizada a uma operação.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-103">WCF Data Services enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="ca7bc-104">Você pode usar essa lógica personalizada para validar dados em mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="ca7bc-105">Você também pode usá-la para restringir mais o escopo de uma solicitação de consulta, como inserir uma política de autorização personalizada com base na solicitação.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="ca7bc-106">A interceptação é executada por métodos especialmente atribuídos no serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="ca7bc-107">Esses métodos são chamados por WCF Data Services no ponto apropriado do processamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-107">These methods are called by WCF Data Services at the appropriate point in message processing.</span></span> <span data-ttu-id="ca7bc-108">Os interceptores são definidos com base no conjunto de entidades, e os métodos de interceptor não podem aceitar parâmetros da solicitação, como ocorre nas operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="ca7bc-109">Os métodos de interceptor de consulta, que são chamados durante o processamento de uma solicitação HTTP GET, devem retornar uma expressão lambda que determina se uma instância do conjunto de entidades do interceptor deve ser retornada pelos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="ca7bc-110">Esta expressão é usada pelo serviço de dados para refinar mais a operação solicitada.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="ca7bc-111">Veja a seguir um exemplo de definição de um interceptor de consulta.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="ca7bc-112">Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ca7bc-112">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="ca7bc-113">Os interceptores de alteração, que são chamados para processar operações sem consulta, devem retornar `void` (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ca7bc-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="ca7bc-114">Os métodos de interceptor de alteração devem aceitar estes dois parâmetros:</span><span class="sxs-lookup"><span data-stu-id="ca7bc-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="ca7bc-115">Um parâmetro de um tipo que seja compatível com o tipo de entidade do conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="ca7bc-116">Quando o serviço de dados chamar o interceptor de alteração, o valor desse parâmetro refletirá as informações de entidade enviadas pela solicitação.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="ca7bc-117">Um parâmetro do tipo <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="ca7bc-118">Quando o serviço de dados chamar o interceptor de alteração, o valor desse parâmetro refletirá a operação que a solicitação estiver tentando executar.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="ca7bc-119">Veja a seguir um exemplo de definição de um interceptor de alteração.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="ca7bc-120">Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ca7bc-120">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="ca7bc-121">Os atributos a seguir têm suporte para interceptação.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="ca7bc-122">**[QueryInterceptor (** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="ca7bc-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="ca7bc-123">Os métodos com o atributo <xref:System.Data.Services.QueryInterceptorAttribute> aplicado são chamados quando uma solicitação HTTP GET é recebida para o recurso de destino do conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="ca7bc-124">Esses métodos devem sempre retornar uma expressão lambda no formato `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="ca7bc-125">**[ChangeInterceptor (** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="ca7bc-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="ca7bc-126">Os métodos com o atributo <xref:System.Data.Services.ChangeInterceptorAttribute> aplicado são chamados quando uma solicitação HTTP, que não seja HTTP GET, é recebida para o recurso de destino do conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="ca7bc-127">Esses métodos devem sempre retornar `void` (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ca7bc-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="ca7bc-128">Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ca7bc-128">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7bc-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="ca7bc-129">See also</span></span>

- [<span data-ttu-id="ca7bc-130">Operações de serviço</span><span class="sxs-lookup"><span data-stu-id="ca7bc-130">Service Operations</span></span>](service-operations-wcf-data-services.md)
