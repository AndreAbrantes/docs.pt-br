---
title: Retornar o primeiro elemento em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 4506ef1a79c8f7e77160df4d55d0f93ee79f5a41
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200336"
---
# <a name="return-the-first-element-in-a-sequence"></a>Retornar o primeiro elemento em uma sequência

Use o operador de <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro elemento em uma sequência. Consultas que usam <xref:System.Linq.Enumerable.First%2A> é executado imediatamente.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não suporta o operador de <xref:System.Linq.Enumerable.Last%2A> .  
  
## <a name="example"></a>Exemplo  

 O código a seguir localiza o primeiro `Shipper` em uma tabela:  
  
 Se você executa essa consulta na base de dados de exemplo Northwind, os resultados são  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Exemplo  

 O código a seguir localiza único `Customer` que tem `CustomerID` BONAP.  
  
 Se você executa essa consulta na base de dados de exemplo Northwind, os resultados são `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Veja também

- [Exemplos de consulta](query-examples.md)
- [Baixar bancos de dados de amostra](downloading-sample-databases.md)
