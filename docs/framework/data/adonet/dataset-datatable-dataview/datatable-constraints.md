---
title: Restrições de DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151280"
---
# <a name="datatable-constraints"></a><span data-ttu-id="4a82a-102">Restrições de DataTable</span><span class="sxs-lookup"><span data-stu-id="4a82a-102">DataTable Constraints</span></span>
<span data-ttu-id="4a82a-103">Você pode usar restrições para impor restrições nos dados em um <xref:System.Data.DataTable>, para manter a integridade dos dados.</span><span class="sxs-lookup"><span data-stu-id="4a82a-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="4a82a-104">Uma restrição é uma regra automática, aplicada a uma coluna ou colunas relacionadas, que determina o curso de ação quando o valor de uma linha é modificado de alguma maneira.</span><span class="sxs-lookup"><span data-stu-id="4a82a-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="4a82a-105">As restrições são `System.Data.DataSet.EnforceConstraints` impostas <xref:System.Data.DataSet> quando a propriedade do é **verdadeiro.**</span><span class="sxs-lookup"><span data-stu-id="4a82a-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="4a82a-106">Para um exemplo de código que mostra como definir a propriedade `EnforceConstraints`, consulte o tópico de referência <xref:System.Data.DataSet.EnforceConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a82a-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="4a82a-107">Há dois tipos de restrições no ADO.NET: o <xref:System.Data.ForeignKeyConstraint> e o <xref:System.Data.UniqueConstraint>.</span><span class="sxs-lookup"><span data-stu-id="4a82a-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="4a82a-108">Por padrão, ambas as restrições são criadas automaticamente quando você cria <xref:System.Data.DataRelation> uma relação entre duas ou mais tabelas adicionando a ao **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="4a82a-109">No entanto, você pode desativar esse comportamento especificando **createRestrições** = **falsas** ao criar a relação.</span><span class="sxs-lookup"><span data-stu-id="4a82a-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="4a82a-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="4a82a-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="4a82a-111">Uma **Restrição de Tecla Estrangeira** impõe regras sobre como as atualizações e exclusões em tabelas relacionadas são propagadas.</span><span class="sxs-lookup"><span data-stu-id="4a82a-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="4a82a-112">Por exemplo, se um valor em uma linha de uma tabela for atualizado ou excluído, e esse mesmo valor também for usado em uma ou mais tabelas relacionadas, uma **ForeignKeyRestrição** determina o que acontece nas tabelas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="4a82a-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="4a82a-113">As <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> propriedades da **ForeignKeyConstraint** definem a ação a ser tomada quando o usuário tenta excluir ou atualizar uma linha em uma tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="4a82a-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="4a82a-114">A tabela a seguir descreve as diferentes configurações disponíveis para as propriedades **DeleteRule** e **UpdateRule** da **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="4a82a-115">Configuração de regra</span><span class="sxs-lookup"><span data-stu-id="4a82a-115">Rule setting</span></span>|<span data-ttu-id="4a82a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a82a-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="4a82a-117">**Cascata**</span><span class="sxs-lookup"><span data-stu-id="4a82a-117">**Cascade**</span></span>|<span data-ttu-id="4a82a-118">Excluir ou atualizar linhas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="4a82a-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="4a82a-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="4a82a-119">**SetNull**</span></span>|<span data-ttu-id="4a82a-120">Defina valores em linhas relacionadas a **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="4a82a-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="4a82a-121">**SetDefault**</span></span>|<span data-ttu-id="4a82a-122">Definir valores em linhas relacionadas para o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="4a82a-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="4a82a-123">**Nenhum**</span><span class="sxs-lookup"><span data-stu-id="4a82a-123">**None**</span></span>|<span data-ttu-id="4a82a-124">Nenhuma ação em linhas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="4a82a-124">Take no action on related rows.</span></span> <span data-ttu-id="4a82a-125">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="4a82a-125">This is the default.</span></span>|  
  
 <span data-ttu-id="4a82a-126">Uma **Restrição de Tecla Estrangeira** pode restringir, bem como propagar, alterações em colunas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="4a82a-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="4a82a-127">Dependendo das propriedades definidas para a **Configuração de Chave Estrangeira** de uma coluna, se a propriedade **EnforceConstraints** do **DataSet for** **verdadeira,** a realização de certas operações na linha pai resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4a82a-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="4a82a-128">Por exemplo, se a propriedade **DeleteRule** da **ForeignKeyConstraint** for **None**, uma linha pai não poderá ser excluída se tiver alguma linha de filho.</span><span class="sxs-lookup"><span data-stu-id="4a82a-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="4a82a-129">Você pode criar uma restrição de chave estrangeira entre colunas únicas ou entre uma matriz de colunas usando o construtor **ForeignKeyConstraint.**</span><span class="sxs-lookup"><span data-stu-id="4a82a-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="4a82a-130">Passe o objeto **ForeignKeyConstraint** resultante para o método **Add** da propriedade **Restrições** da tabela, que é uma Coleção de **Restrições**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="4a82a-131">Você também pode passar argumentos de construtor para várias sobrecargas do método **Add** de uma **ConstraintCollection** para criar uma **Restrição de Teceladeria estrangeira**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="4a82a-132">Ao criar uma **Configuração de Chave Estrangeira,** você pode passar os valores **DeleteRule** e **UpdateRule** para o construtor como argumentos, ou você pode defini-los como propriedades como no exemplo a seguir (quando o valor **DeleteRule** é definido como **Nenhum**).</span><span class="sxs-lookup"><span data-stu-id="4a82a-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="4a82a-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="4a82a-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="4a82a-134">Alterações nas linhas podem ser aceitas usando o método **AcceptChanges** ou canceladas usando o método **RejectChanges** do **DataSet,** **DataTable**ou **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="4a82a-135">Quando um **Conjunto de Dados** contém **Restrições de Tecelanderna,** invocar os métodos **AcceptChanges** ou **RejectChanges** impõe a **Regra de Aceitação**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="4a82a-136">A propriedade **AcceptRejectRule** da **ForeignKeyConstraint** determina qual ação será tomada nas linhas de filho quando **As alterações aceitas** ou **rejeições** são chamadas na linha pai.</span><span class="sxs-lookup"><span data-stu-id="4a82a-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="4a82a-137">A tabela a seguir lista as configurações disponíveis para **a AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="4a82a-138">Configuração de regra</span><span class="sxs-lookup"><span data-stu-id="4a82a-138">Rule setting</span></span>|<span data-ttu-id="4a82a-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a82a-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="4a82a-140">**Cascata**</span><span class="sxs-lookup"><span data-stu-id="4a82a-140">**Cascade**</span></span>|<span data-ttu-id="4a82a-141">Aceitar ou rejeitar alterações em linhas filho.</span><span class="sxs-lookup"><span data-stu-id="4a82a-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="4a82a-142">**Nenhum**</span><span class="sxs-lookup"><span data-stu-id="4a82a-142">**None**</span></span>|<span data-ttu-id="4a82a-143">Nenhuma ação em linhas filho.</span><span class="sxs-lookup"><span data-stu-id="4a82a-143">Take no action on child rows.</span></span> <span data-ttu-id="4a82a-144">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="4a82a-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="4a82a-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a82a-145">Example</span></span>  
 <span data-ttu-id="4a82a-146">O exemplo a seguir cria um <xref:System.Data.ForeignKeyConstraint>, define várias das suas propriedades, incluindo <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> e adiciona-os ao <xref:System.Data.ConstraintCollection> de um objeto <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4a82a-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="4a82a-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="4a82a-147">UniqueConstraint</span></span>  
 <span data-ttu-id="4a82a-148">O objeto **UniqueConstraint,** que pode ser atribuído a uma única coluna ou a uma matriz de colunas em uma Tabela de **Dados,** garante que todos os dados na coluna ou colunas especificadas sejam únicos por linha.</span><span class="sxs-lookup"><span data-stu-id="4a82a-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="4a82a-149">Você pode criar uma restrição única para uma coluna ou matriz de colunas usando o construtor **UniqueConstraint.**</span><span class="sxs-lookup"><span data-stu-id="4a82a-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="4a82a-150">Passe o objeto **UniqueConstraint** resultante para o método **Add** da propriedade **Restrições** da tabela, que é uma Coleção de **Restrições**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="4a82a-151">Você também pode passar argumentos de construtor para várias sobrecargas do método **Add** de uma **ConstraintCollection** para criar uma **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="4a82a-152">Ao criar uma **Restrição Única** para uma coluna ou colunas, você pode especificar opcionalmente se a coluna ou as colunas são uma chave principal.</span><span class="sxs-lookup"><span data-stu-id="4a82a-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="4a82a-153">Você também pode criar uma restrição única para uma coluna definindo a propriedade **Unique** da coluna como **verdadeira**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="4a82a-154">Alternativamente, definir a propriedade **Unique** de uma única coluna para **falsa** remove qualquer restrição única que possa existir.</span><span class="sxs-lookup"><span data-stu-id="4a82a-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="4a82a-155">Definir uma coluna ou colunas como uma chave primária para uma tabela criará automaticamente uma restrição exclusiva para a coluna ou colunas especificadas.</span><span class="sxs-lookup"><span data-stu-id="4a82a-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="4a82a-156">Se você remover uma coluna da propriedade **PrimaryKey** de uma Tabela de **Dados,** a **'Restrições únicas'** será removida.</span><span class="sxs-lookup"><span data-stu-id="4a82a-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="4a82a-157">O exemplo a seguir cria uma **Restrição Única** para duas colunas de uma Tabela de **Dados**.</span><span class="sxs-lookup"><span data-stu-id="4a82a-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]
    {custTable.Columns["CustomerID"],
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a82a-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="4a82a-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="4a82a-159">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="4a82a-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="4a82a-160">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="4a82a-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="4a82a-161">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a82a-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
