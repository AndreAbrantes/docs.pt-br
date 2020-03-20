---
title: Problemas conhecidos e considerações no LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150136"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Problemas conhecidos e considerações no LINQ to Entities
Esta seção fornece informações sobre problemas conhecidos com consultas LINQ para Entidades.  
  
- [Consultas LINQ que não podem ser armazenadas em cache](#LINQQueriesThatAreNotCached)  
  
- [Informações de ordenação perdidas](#OrderingInfoLost)  
  
- [Inteiros sem sinal não suportados](#UnsignedIntsUnsupported)  
  
- [Erros de conversão de tipo](#TypeConversionErrors)  
  
- [Referenciando variáveis não escalares não suportadas](#RefNonScalarClosures)  
  
- [Pode haver falha em consultas aninhadas com o SQL Server 2000](#NestedQueriesSQL2000)  
  
- [Projetando para um tipo anônimo](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a>Consultas LINQ que não podem ser armazenadas em cache  
 A partir do .NET Framework 4.5, as consultas LINQ to Entities são automaticamente armazenadas em cache. No entanto, as consultas LINQ to Entities que aplicam o operador `Enumerable.Contains` a coleções na memória não são armazenadas em cache automaticamente. Além disso, não é permitido parametrizar coleções na memória em consultas LINQ compiladas.  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a>Informações de ordenação perdidas  
 Projetar colunas em um tipo anônimo fará com que as informações de pedidos sejam perdidas em algumas consultas que são executadas contra um banco de dados SQL Server 2005 definido para um nível de compatibilidade de "80".  Isso ocorre quando um nome de coluna na lista order-by corresponde a um nome de coluna no seletor, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a>Inteiros sem sinal não suportados  
 A especificação de um tipo inteiro não assinado em uma consulta LINQ para Entidades não é suportada porque o Quadro de Entidades não suporta inteiros não assinados. Se você especificar um inteiro <xref:System.ArgumentException> não assinado, uma exceção será lançada durante a tradução de expressão de consulta, conforme mostrado no exemplo a seguir. Este exemplo consulta um pedido com a ID 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a>Erros de conversão de tipos  
 No Visual Basic, quando uma propriedade é mapeada para uma coluna de tipo bit do SQL Server com um valor igual a 1 usando a função `CByte`, um <xref:System.Data.SqlClient.SqlException> é gerado com uma mensagem de “Erro de estouro aritmético". O exemplo a seguir consulta a coluna `Product.MakeFlag` no banco de dados de exemplo AdventureWorks e uma exceção é gerada quando os resultados da consulta são iterados sobre.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a>Referenciando variáveis não escalares não suportadas  
 A referência a variáveis não escalares, como uma entidade, em uma consulta não é suportada. Quando uma consulta desse tipo é executada, é gerada uma exceção <xref:System.NotSupportedException> com a mensagem "Não foi possível criar um valor constante de tipo `EntityType`. Apenas tipos primitivos ('como Int32, String e GUID') são suportados nesse contexto."  
  
> [!NOTE]
> A referência a uma coleção de variáveis escalares é suportada.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Pode haver falha em consultas aninhadas com o SQL Server 2000  
 Com o SQL Server 2000, pode haver falha em consultas do LINQ to Entities se elas gerarem consultas Transact-SQL aninhadas com três ou mais níveis de profundidade.  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a>Projetando para um tipo anônimo  
 Se você definir o caminho da consulta inicial para incluir objetos relacionados usando o método <xref:System.Data.Objects.ObjectQuery%601.Include%2A> no <xref:System.Data.Objects.ObjectQuery%601> e, em seguida, usar o LINQ para projetar os objetos retornados para um tipo anônimo, os objetos especificados no método de inclusão não serão incluídos nos resultados da consulta.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Para obter objetos relacionados, não projete tipos retornados para um tipo anônimo.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Confira também

- [LINQ para Entidades](linq-to-entities.md)
