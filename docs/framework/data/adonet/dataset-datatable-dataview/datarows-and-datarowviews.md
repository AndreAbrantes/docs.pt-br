---
title: DataRows e DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: bce90c1d310178e66da7c758c6df2cd357199c8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153281"
---
# <a name="datarows-and-datarowviews"></a>DataRows e DataRowViews

Um <xref:System.Data.DataView> expõe uma coleção enumerável de <xref:System.Data.DataRowView> objetos. Os objetos **DataRowView** expõem valores como matrizes de objetos que são indexados pelo nome ou pela referência ordinal da coluna na tabela subjacente. Você pode acessar o <xref:System.Data.DataRow> que é exposto pelo **DataRowView** usando a <xref:System.Data.DataRowView.Row%2A> propriedade de **DataRowView**.  
  
 Quando você exibe valores usando um **DataRowView**, a <xref:System.Data.DataView.RowStateFilter%2A> propriedade de **DataView** determina qual versão de linha da **DataRow** subjacente é exposta. Para obter informações sobre como acessar versões de linha diferentes usando uma **DataRow**, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).  
  
 O exemplo de código a seguir exibe todos os valores atuais e originais em uma tabela.  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataViews](dataviews.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
