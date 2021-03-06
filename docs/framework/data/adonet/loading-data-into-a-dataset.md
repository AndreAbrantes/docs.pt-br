---
title: Carregando dados em um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: c870cabc875aa0152910ce916819fb1ff1c018f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166702"
---
# <a name="loading-data-into-a-dataset"></a>Carregando dados em um DataSet

Um <xref:System.Data.DataSet> objeto deve ser preenchido primeiro antes que você possa consultá-lo com LINQ to DataSet. Há várias maneiras diferentes de popular o <xref:System.Data.DataSet>. Por exemplo, você pode usar o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] para consultar o banco de dados e carregar os resultados no <xref:System.Data.DataSet> . Para obter mais informações, consulte [LINQ to SQL](./sql/linq/index.md).  
  
 Outra maneira comum de carregar dados em um <xref:System.Data.DataSet> é usar a classe <xref:System.Data.Common.DataAdapter> para recuperar dados do banco de dados. Isso é ilustrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  

 Esse exemplo usa <xref:System.Data.Common.DataAdapter> para consultar o banco de dados AdventureWorks para obter informações sobre as vendas do ano 2002 e carrega os resultados em um <xref:System.Data.DataSet>. Depois que o <xref:System.Data.DataSet> tiver sido preenchido, você poderá escrever consultas nele usando LINQ to DataSet. O `FillDataSet` método neste exemplo é usado nas consultas de exemplo em [LINQ to DataSet exemplos](linq-to-dataset-examples.md). Para obter mais informações, consulte [consultando conjuntos](querying-datasets-linq-to-dataset.md)de dados.  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Confira também

- [LINQ para visão geral do DataSet](linq-to-dataset-overview.md)
- [Consultar DataSets](querying-datasets-linq-to-dataset.md)
- [LINQ para exemplos de DataSet](linq-to-dataset-examples.md)
