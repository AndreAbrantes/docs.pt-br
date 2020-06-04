---
title: Como filtrar resultados de consulta usando LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 4d91783429f24abfe4149217542f8f7a6073bfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404985"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="72159-102">Como filtrar resultados de consulta usando LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72159-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="72159-103">A consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados e a execução de consultas.</span><span class="sxs-lookup"><span data-stu-id="72159-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="72159-104">O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados SQL Server e filtra os resultados por um valor específico usando a `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="72159-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="72159-105">Para obter mais informações, consulte a [cláusula WHERE](../../../language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="72159-105">For more information, see [Where Clause](../../../language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="72159-106">Os exemplos neste tópico usam o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="72159-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="72159-107">Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="72159-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="72159-108">Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="72159-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="72159-109">Para criar uma conexão com um banco de dados</span><span class="sxs-lookup"><span data-stu-id="72159-109">To create a connection to a database</span></span>

1. <span data-ttu-id="72159-110">No Visual Studio, abra **Gerenciador de servidores** / **Gerenciador de banco de dados** clicando em **Gerenciador de servidores** / **Gerenciador de banco de dados** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="72159-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="72159-111">Clique com o botão direito do mouse em **conexões de dados** em **Gerenciador de servidores** / **Gerenciador de banco de dados** e clique em **Adicionar conexão**.</span><span class="sxs-lookup"><span data-stu-id="72159-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="72159-112">Especifique uma conexão válida para o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="72159-112">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="72159-113">Para adicionar um projeto que contém um arquivo de LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="72159-113">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="72159-114">No Visual Studio, no menu **arquivo** , aponte para **novo** e clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="72159-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="72159-115">Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="72159-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="72159-116">No menu **Projeto** , clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="72159-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="72159-117">Selecione o modelo de item **classes de LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="72159-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="72159-118">Atribua um nome ao arquivo `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="72159-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="72159-119">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="72159-119">Click **Add**.</span></span> <span data-ttu-id="72159-120">O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="72159-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="72159-121">Para adicionar tabelas para consulta ao o/R Designer</span><span class="sxs-lookup"><span data-stu-id="72159-121">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="72159-122">Em **Gerenciador de servidores** / **Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="72159-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="72159-123">Expanda a pasta **Tabelas** .</span><span class="sxs-lookup"><span data-stu-id="72159-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="72159-124">Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no arquivo Northwind. dbml que você adicionou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="72159-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="72159-125">Clique na tabela clientes e arraste-a para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="72159-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="72159-126">Clique na tabela Orders e arraste-a para o painel esquerdo do designer.</span><span class="sxs-lookup"><span data-stu-id="72159-126">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="72159-127">O designer cria novos `Customer` `Order` objetos e para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="72159-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="72159-128">Observe que o designer detecta automaticamente as relações entre as tabelas e cria propriedades filhas para objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="72159-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="72159-129">Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem uma `Orders` propriedade para todos os pedidos relacionados a esse cliente.</span><span class="sxs-lookup"><span data-stu-id="72159-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="72159-130">Salve as alterações e feche o designer.</span><span class="sxs-lookup"><span data-stu-id="72159-130">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="72159-131">Salve seu projeto.</span><span class="sxs-lookup"><span data-stu-id="72159-131">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="72159-132">Para adicionar código para consultar o banco de dados e exibir os resultados</span><span class="sxs-lookup"><span data-stu-id="72159-132">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="72159-133">Na **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário padrão do Windows para seu projeto, Form1.</span><span class="sxs-lookup"><span data-stu-id="72159-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="72159-134">Clique duas vezes em Form1 para adicionar código ao `Load` evento do formulário.</span><span class="sxs-lookup"><span data-stu-id="72159-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="72159-135">Quando você adicionou tabelas ao o/R Designer, o designer adicionou um <xref:System.Data.Linq.DataContext> objeto ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="72159-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="72159-136">Esse objeto contém o código que você deve ter para acessar essas tabelas, além de objetos individuais e coleções para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="72159-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="72159-137">O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="72159-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="72159-138">Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="72159-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="72159-139">Você pode criar uma instância do <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo o/R Designer.</span><span class="sxs-lookup"><span data-stu-id="72159-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="72159-140">Adicione o seguinte código ao `Load` evento para consultar as tabelas que são expostas como propriedades do seu contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="72159-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="72159-141">A consulta filtra os resultados e retorna somente os clientes que estão localizados no `London` .</span><span class="sxs-lookup"><span data-stu-id="72159-141">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="72159-142">Pressione F5 para executar o projeto e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="72159-142">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="72159-143">A seguir estão alguns outros filtros que você pode tentar.</span><span class="sxs-lookup"><span data-stu-id="72159-143">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="72159-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="72159-144">See also</span></span>

- [<span data-ttu-id="72159-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="72159-145">LINQ</span></span>](index.md)
- [<span data-ttu-id="72159-146">Consultas</span><span class="sxs-lookup"><span data-stu-id="72159-146">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="72159-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="72159-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="72159-148">Métodos DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="72159-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
