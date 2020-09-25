---
title: Copiando conteúdo do DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: 1cadcacab6084bbf3caaf61d98b78fe3067d92f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202364"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="f85d5-102">Copiando conteúdo do DataSet</span><span class="sxs-lookup"><span data-stu-id="f85d5-102">Copying DataSet Contents</span></span>

<span data-ttu-id="f85d5-103">Você pode criar uma cópia de um <xref:System.Data.DataSet> para que você possa trabalhar com dados sem afetar os dados originais ou trabalhar com um subconjunto dos dados de um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f85d5-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="f85d5-104">Ao copiar um **conjunto**de um, você pode:</span><span class="sxs-lookup"><span data-stu-id="f85d5-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="f85d5-105">Crie uma cópia exata do **conjunto**de dados, incluindo o esquema, as informações de estado de linha e as versões de linha.</span><span class="sxs-lookup"><span data-stu-id="f85d5-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="f85d5-106">Crie um **conjunto** de registros que contenha o esquema de um **conjunto**de um existente, mas somente as linhas que foram modificadas.</span><span class="sxs-lookup"><span data-stu-id="f85d5-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="f85d5-107">Você pode retornar todas as linhas que foram modificadas ou especificar um **DataRowState**específico.</span><span class="sxs-lookup"><span data-stu-id="f85d5-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="f85d5-108">Para obter mais informações sobre Estados de linha, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="f85d5-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="f85d5-109">Copie o esquema ou a estrutura relacional somente do **conjunto** de dados, sem copiar nenhuma linha.</span><span class="sxs-lookup"><span data-stu-id="f85d5-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="f85d5-110">As linhas podem ser importadas em um <xref:System.Data.DataTable> existente usando o <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="f85d5-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="f85d5-111">Para criar uma cópia exata do **conjunto** de dados que inclui tanto o esquema quanto o dado, use o <xref:System.Data.DataSet.Copy%2A> método do **conjunto**.</span><span class="sxs-lookup"><span data-stu-id="f85d5-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="f85d5-112">O exemplo de código a seguir mostra como criar uma cópia exata do **conjunto**de uma.</span><span class="sxs-lookup"><span data-stu-id="f85d5-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="f85d5-113">Para criar uma cópia de um **conjunto** de dados que inclui o esquema e apenas o dado que representa as linhas **adicionadas**, **modificadas**ou **excluídas** , use o <xref:System.Data.DataSet.GetChanges%2A> método do **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f85d5-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="f85d5-114">Você também pode usar **GetChanges** para retornar apenas linhas com um estado de linha especificado, passando um valor de **DataRowState** ao chamar **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="f85d5-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="f85d5-115">O exemplo de código a seguir mostra como passar um **DataRowState** ao chamar **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="f85d5-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="f85d5-116">Para criar uma cópia de um **conjunto** de um DataSet que inclui apenas o esquema, use o <xref:System.Data.DataSet.Clone%2A> método do **conjunto**de um.</span><span class="sxs-lookup"><span data-stu-id="f85d5-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="f85d5-117">Você também pode adicionar linhas existentes ao **conjunto** de registros clonado usando o método **ImportRow** da **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="f85d5-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="f85d5-118">**ImportRow** adiciona informações de dados, estado de linha e versão de linha à tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="f85d5-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="f85d5-119">Os valores de coluna são adicionados somente onde o nome da coluna corresponde e o tipo de dados é compatível.</span><span class="sxs-lookup"><span data-stu-id="f85d5-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="f85d5-120">O exemplo de código a seguir cria um clone de um conjunto de um **DataSet** e, em seguida, adiciona as linhas do **conjunto** de registros original à tabela **Customers** no clone de **DataSet** para clientes em que a coluna **CountryRegion** tem o valor "Alemanha".</span><span class="sxs-lookup"><span data-stu-id="f85d5-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="f85d5-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="f85d5-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="f85d5-122">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="f85d5-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="f85d5-123">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f85d5-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
