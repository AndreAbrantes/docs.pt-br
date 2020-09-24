---
title: Exclusão de DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 2092d7319a398bbdeaef764d677818f78ddf9de9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153346"
---
# <a name="datarow-deletion"></a><span data-ttu-id="b8361-102">Exclusão de DataRow</span><span class="sxs-lookup"><span data-stu-id="b8361-102">DataRow Deletion</span></span>

<span data-ttu-id="b8361-103">Há dois métodos que você pode usar para excluir um <xref:System.Data.DataRow> objeto de um <xref:System.Data.DataTable> objeto: o método **Remove** do <xref:System.Data.DataRowCollection> objeto e o <xref:System.Data.DataRow.Delete%2A> método do objeto **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="b8361-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="b8361-104">Enquanto o <xref:System.Data.DataRowCollection.Remove%2A> método exclui uma **DataRow** de **DataRowCollection**, o <xref:System.Data.DataRow.Delete%2A> método marca apenas a linha para exclusão.</span><span class="sxs-lookup"><span data-stu-id="b8361-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="b8361-105">A remoção real ocorre quando o aplicativo chama o método **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="b8361-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="b8361-106">Usando <xref:System.Data.DataRow.Delete%2A>, você pode verificar programaticamente quais linhas estão marcadas para exclusão antes de realmente removê-las.</span><span class="sxs-lookup"><span data-stu-id="b8361-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="b8361-107">Quando uma linha está marcada para exclusão, sua propriedade <xref:System.Data.DataRow.RowState%2A> é definida como <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8361-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="b8361-108">Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> deve ser chamado em um loop foreach ao fazer a iteração por meio de um objeto de <xref:System.Data.DataRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="b8361-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="b8361-109">Nem <xref:System.Data.DataRow.Delete%2A> ou <xref:System.Data.DataRowCollection.Remove%2A> modificam o estado da coleção.</span><span class="sxs-lookup"><span data-stu-id="b8361-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="b8361-110">Ao usar uma <xref:System.Data.DataSet> **DataTable** ou em conjunto com um **DataAdapter** e uma fonte de dados relacional, use o método **delete** da **DataRow** para remover a linha.</span><span class="sxs-lookup"><span data-stu-id="b8361-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="b8361-111">O método **delete** marca a linha como **excluída** no **DataSet** ou **DataTable** , mas não a remove.</span><span class="sxs-lookup"><span data-stu-id="b8361-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="b8361-112">Em vez disso, quando o **DataAdapter** encontra uma linha marcada como **excluída**, ele executa seu método **DeleteCommand** para excluir a linha na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="b8361-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="b8361-113">Em seguida, a linha pode ser removida permanentemente usando o método **AcceptChanges** .</span><span class="sxs-lookup"><span data-stu-id="b8361-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="b8361-114">Se você usar **remover** para excluir a linha, a linha será completamente removida da tabela, mas o **DataAdapter** não excluirá a linha na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="b8361-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="b8361-115">O método **Remove** da **DataRowCollection** usa uma **DataRow** como um argumento e a remove da coleção, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8361-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="b8361-116">Por outro lado, o exemplo a seguir demonstra como chamar o método **delete** em uma **DataRow** para alterar seu **RowState** para **excluído**.</span><span class="sxs-lookup"><span data-stu-id="b8361-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="b8361-117">Se uma linha for marcada para exclusão e você chamar o método **AcceptChanges** do objeto **DataTable** , a linha será removida da **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="b8361-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="b8361-118">Por outro lado, se você chamar **RejectChanges**, o **RowState** da linha será revertido para o que estava antes de ser marcado como **excluído**.</span><span class="sxs-lookup"><span data-stu-id="b8361-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8361-119">Se o **RowState** de uma **DataRow** for **adicionado**, o que significa que acabou de ser adicionado à tabela e, em seguida, marcado como **excluído**, ele será removido da tabela.</span><span class="sxs-lookup"><span data-stu-id="b8361-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8361-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8361-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="b8361-121">Manipulando dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="b8361-121">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="b8361-122">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b8361-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
