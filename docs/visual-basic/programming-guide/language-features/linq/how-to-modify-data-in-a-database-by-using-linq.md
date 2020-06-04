---
title: Como modificar dados em um banco de dados usando LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: eb076d9156fa66858f2e560422eef0dc61ba22b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403479"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="64d64-102">Como modificar dados em um banco de dados usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64d64-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="64d64-103">As consultas de LINQ (consulta integrada à linguagem) facilitam o acesso a informações do banco de dados e a modificação de valores no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="64d64-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="64d64-104">O exemplo a seguir mostra como criar um novo aplicativo que recupera e atualiza informações em um banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="64d64-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="64d64-105">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="64d64-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="64d64-106">Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="64d64-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="64d64-107">Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="64d64-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="64d64-108">Para criar uma conexão com um banco de dados</span><span class="sxs-lookup"><span data-stu-id="64d64-108">To create a connection to a database</span></span>

1. <span data-ttu-id="64d64-109">No Visual Studio, abra **Gerenciador de servidores** / **Gerenciador de banco de dados** clicando no menu **Exibir** e, em seguida, selecione **Gerenciador de servidores** / **Gerenciador de banco de dados**.</span><span class="sxs-lookup"><span data-stu-id="64d64-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="64d64-110">Clique com o botão direito do mouse em **conexões de dados** no **Gerenciador de servidores** / **Gerenciador de banco de dados**e clique em **Adicionar conexão**.</span><span class="sxs-lookup"><span data-stu-id="64d64-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="64d64-111">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="64d64-111">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="64d64-112">Para adicionar um projeto com um arquivo LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="64d64-112">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="64d64-113">No Visual Studio, no menu **arquivo** , aponte para **novo** e clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="64d64-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="64d64-114">Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="64d64-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="64d64-115">No menu **Projeto** , clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="64d64-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="64d64-116">Selecione o modelo de item **classes de LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="64d64-116">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="64d64-117">Atribua um nome ao arquivo `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="64d64-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="64d64-118">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="64d64-118">Click **Add**.</span></span> <span data-ttu-id="64d64-119">O Object Relational Designer (O/R Designer) é aberto para o `northwind.dbml` arquivo.</span><span class="sxs-lookup"><span data-stu-id="64d64-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="64d64-120">Para adicionar tabelas à consulta e modificar para o designer</span><span class="sxs-lookup"><span data-stu-id="64d64-120">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="64d64-121">Em **Gerenciador de servidores** / **Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="64d64-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="64d64-122">Expanda a pasta **Tabelas** .</span><span class="sxs-lookup"><span data-stu-id="64d64-122">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="64d64-123">Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no `northwind.dbml` arquivo que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="64d64-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="64d64-124">Clique na tabela clientes e arraste-a para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="64d64-124">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="64d64-125">O designer cria um novo objeto de cliente para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="64d64-125">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="64d64-126">Salve as alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="64d64-126">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="64d64-127">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="64d64-127">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="64d64-128">Para adicionar código para modificar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="64d64-128">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="64d64-129">Na **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário padrão do Windows para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="64d64-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="64d64-130">Quando você adicionou tabelas ao o/R Designer, o designer adicionou um <xref:System.Data.Linq.DataContext> objeto ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="64d64-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="64d64-131">Este objeto contém código que você pode usar para acessar a tabela Customers.</span><span class="sxs-lookup"><span data-stu-id="64d64-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="64d64-132">Ele também contém um código que define um objeto Customer local e uma coleção Customers para a tabela.</span><span class="sxs-lookup"><span data-stu-id="64d64-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="64d64-133">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="64d64-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="64d64-134">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="64d64-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="64d64-135">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> objeto em seu código e consultar e modificar a coleção Customers especificada pelo o/R Designer.</span><span class="sxs-lookup"><span data-stu-id="64d64-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="64d64-136">As alterações feitas na coleção clientes não são refletidas no banco de dados até que você as envie chamando o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método do <xref:System.Data.Linq.DataContext> objeto.</span><span class="sxs-lookup"><span data-stu-id="64d64-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="64d64-137">Clique duas vezes no Windows Form, Form1, para adicionar código ao <xref:System.Windows.Forms.Form.Load> evento para consultar a tabela Customers que é exposta como uma propriedade do seu <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="64d64-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="64d64-138">Adicione os códigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="64d64-138">Add the following code:</span></span>

    ```vb
    Private db As northwindDataContext

    Private Sub Form1_Load(ByVal sender As System.Object,
                           ByVal e As System.EventArgs
                          ) Handles MyBase.Load
      db = New northwindDataContext()

      RefreshData()
    End Sub

    Private Sub RefreshData()
      Dim customers = From cust In db.Customers
                      Where cust.City(0) = "W"
                      Select cust

      DataGridView1.DataSource = customers
    End Sub
    ```

3. <span data-ttu-id="64d64-139">Na **caixa de ferramentas**, arraste três <xref:System.Windows.Forms.Button> controles para o formulário.</span><span class="sxs-lookup"><span data-stu-id="64d64-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="64d64-140">Selecione o primeiro `Button` controle.</span><span class="sxs-lookup"><span data-stu-id="64d64-140">Select the first `Button` control.</span></span> <span data-ttu-id="64d64-141">Na janela **Propriedades** , defina o `Name` do `Button` controle como `AddButton` e o `Text` como `Add` .</span><span class="sxs-lookup"><span data-stu-id="64d64-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="64d64-142">Selecione o segundo botão e defina a `Name` propriedade como `UpdateButton` e a `Text` propriedade como `Update` .</span><span class="sxs-lookup"><span data-stu-id="64d64-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="64d64-143">Selecione o terceiro botão e defina a `Name` propriedade como `DeleteButton` e a `Text` propriedade como `Delete` .</span><span class="sxs-lookup"><span data-stu-id="64d64-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="64d64-144">Clique duas vezes no botão **Adicionar** para adicionar código ao seu `Click` evento.</span><span class="sxs-lookup"><span data-stu-id="64d64-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="64d64-145">Adicione os códigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="64d64-145">Add the following code:</span></span>

    ```vb
    Private Sub AddButton_Click(ByVal sender As System.Object,
                                ByVal e As System.EventArgs
                               ) Handles AddButton.Click
      Dim cust As New Customer With {
        .City = "Wellington",
        .CompanyName = "Blue Yonder Airlines",
        .ContactName = "Jill Frank",
        .Country = "New Zealand",
        .CustomerID = "JILLF"}

      db.Customers.InsertOnSubmit(cust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

5. <span data-ttu-id="64d64-146">Clique duas vezes no botão **Atualizar** para adicionar código ao seu `Click` evento.</span><span class="sxs-lookup"><span data-stu-id="64d64-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="64d64-147">Adicione os códigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="64d64-147">Add the following code:</span></span>

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. <span data-ttu-id="64d64-148">Clique duas vezes no botão **excluir** para adicionar código ao seu `Click` evento.</span><span class="sxs-lookup"><span data-stu-id="64d64-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="64d64-149">Adicione os códigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="64d64-149">Add the following code:</span></span>

    ```vb
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles DeleteButton.Click
      Dim deleteCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      db.Customers.DeleteOnSubmit(deleteCust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

7. <span data-ttu-id="64d64-150">Pressione F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="64d64-150">Press F5 to run your project.</span></span> <span data-ttu-id="64d64-151">Clique em **Adicionar** para adicionar um novo registro.</span><span class="sxs-lookup"><span data-stu-id="64d64-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="64d64-152">Clique em **Atualizar** para modificar o novo registro.</span><span class="sxs-lookup"><span data-stu-id="64d64-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="64d64-153">Clique em **excluir** para excluir o novo registro.</span><span class="sxs-lookup"><span data-stu-id="64d64-153">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="64d64-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="64d64-154">See also</span></span>

- [<span data-ttu-id="64d64-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="64d64-155">LINQ</span></span>](index.md)
- [<span data-ttu-id="64d64-156">Consultas</span><span class="sxs-lookup"><span data-stu-id="64d64-156">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="64d64-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="64d64-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="64d64-158">Métodos DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="64d64-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="64d64-159">Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)</span><span class="sxs-lookup"><span data-stu-id="64d64-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
