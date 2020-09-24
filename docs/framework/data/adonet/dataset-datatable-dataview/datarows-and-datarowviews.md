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
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="2087c-102">DataRows e DataRowViews</span><span class="sxs-lookup"><span data-stu-id="2087c-102">DataRows and DataRowViews</span></span>

<span data-ttu-id="2087c-103">Um <xref:System.Data.DataView> expõe uma coleção enumerável de <xref:System.Data.DataRowView> objetos.</span><span class="sxs-lookup"><span data-stu-id="2087c-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="2087c-104">Os objetos **DataRowView** expõem valores como matrizes de objetos que são indexados pelo nome ou pela referência ordinal da coluna na tabela subjacente.</span><span class="sxs-lookup"><span data-stu-id="2087c-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="2087c-105">Você pode acessar o <xref:System.Data.DataRow> que é exposto pelo **DataRowView** usando a <xref:System.Data.DataRowView.Row%2A> propriedade de **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="2087c-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="2087c-106">Quando você exibe valores usando um **DataRowView**, a <xref:System.Data.DataView.RowStateFilter%2A> propriedade de **DataView** determina qual versão de linha da **DataRow** subjacente é exposta.</span><span class="sxs-lookup"><span data-stu-id="2087c-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="2087c-107">Para obter informações sobre como acessar versões de linha diferentes usando uma **DataRow**, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="2087c-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="2087c-108">O exemplo de código a seguir exibe todos os valores atuais e originais em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="2087c-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2087c-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="2087c-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="2087c-110">DataViews</span><span class="sxs-lookup"><span data-stu-id="2087c-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="2087c-111">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2087c-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
