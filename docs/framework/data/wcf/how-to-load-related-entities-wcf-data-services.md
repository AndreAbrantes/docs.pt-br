---
title: Como carregar entidades relacionadas (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 1ef7fa93b5afdf664f22bd69d3fe3a3b17e98f18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180706"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Como carregar entidades relacionadas (WCF Data Services)

Quando você precisar carregar entidades associadas no WCF Data Services, poderá usar o <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> método na <xref:System.Data.Services.Client.DataServiceContext> classe. Você também pode usar o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método no <xref:System.Data.Services.Client.DataServiceQuery%601> para exigir que as entidades relacionadas sejam carregadas cuidadosamente na mesma resposta de consulta.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir mostra como carregar explicitamente o `Customer` que está relacionado a cada `Orders` instância retornada.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir mostra como usar o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método para retornar `Order Details` que pertence ao `Orders` retornado pela consulta.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Veja também

- [Consultar o serviço de dados](querying-the-data-service-wcf-data-services.md)
