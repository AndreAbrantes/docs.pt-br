---
title: escrever consultas
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 25905d7ac3ca4bb66a22ad1df421b400eaa6b08f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413265"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="f2ef4-102">Instruções passo a passo: escrevendo consultas em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2ef4-102">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="f2ef4-103">Este tutorial demonstra como você pode usar Visual Basic recursos de idioma para escrever expressões de consulta LINQ (consulta integrada à linguagem).</span><span class="sxs-lookup"><span data-stu-id="f2ef4-103">This walkthrough demonstrates how you can use Visual Basic language features to write Language-Integrated Query (LINQ) query expressions.</span></span> <span data-ttu-id="f2ef4-104">O tutorial demonstra como criar consultas em uma lista de objetos de aluno, como executar as consultas e como modificá-las.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="f2ef4-105">As consultas incorporam vários recursos, incluindo inicializadores de objeto, inferência de tipo local e tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="f2ef4-106">Depois de concluir este passo a passos, você estará pronto para passar para os exemplos e a documentação do provedor LINQ específico no qual você está interessado.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific LINQ provider you are interested in.</span></span> <span data-ttu-id="f2ef4-107">Os provedores de LINQ incluem [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , LINQ to DataSet e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f2ef4-107">LINQ providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="f2ef4-108">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="f2ef4-108">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="f2ef4-109">Para criar um projeto de aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="f2ef4-109">To create a console application project</span></span>

1. <span data-ttu-id="f2ef4-110">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-110">Start Visual Studio.</span></span>

2. <span data-ttu-id="f2ef4-111">No menu **Arquivo** , aponte para **Novo**e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="f2ef4-112">Na lista **modelos instalados** , clique em **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="f2ef4-113">Na lista de tipos de projeto, clique em **aplicativo de console**.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="f2ef4-114">Na caixa **nome** , digite um nome para o projeto e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="f2ef4-115">Um projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-115">A project is created.</span></span> <span data-ttu-id="f2ef4-116">Por padrão, ele contém uma referência a System. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="f2ef4-117">Além disso, a lista de **namespaces importados** na [página referências, designer de projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) inclui o <xref:System.Linq?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="f2ef4-118">Na [página compilar, designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), verifique se **Option Infer** está definida como **on**.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="f2ef4-119">Adicionar uma Fonte de Dados na Memória</span><span class="sxs-lookup"><span data-stu-id="f2ef4-119">Add an In-Memory Data Source</span></span>

<span data-ttu-id="f2ef4-120">A fonte de dados para as consultas neste passo a passos é uma lista de `Student` objetos.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="f2ef4-121">Cada `Student` objeto contém um nome, um sobrenome, um ano de classe e uma classificação acadêmica no corpo do aluno.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="f2ef4-122">Para adicionar a fonte de dados</span><span class="sxs-lookup"><span data-stu-id="f2ef4-122">To add the data source</span></span>

- <span data-ttu-id="f2ef4-123">Defina uma `Student` classe e crie uma lista de instâncias da classe.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-123">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="f2ef4-124">O código necessário para definir a `Student` classe e criar a lista usada nos exemplos explicativos é fornecido em [como: criar uma lista de itens](how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="f2ef4-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="f2ef4-125">Você pode copiá-lo de lá e colá-lo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="f2ef4-126">O novo código substitui o código que apareceu quando você criou o projeto.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-126">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="f2ef4-127">Para adicionar um novo aluno à lista de alunos</span><span class="sxs-lookup"><span data-stu-id="f2ef4-127">To add a new student to the students list</span></span>

- <span data-ttu-id="f2ef4-128">Siga o padrão no `getStudents` método para adicionar outra instância da `Student` classe à lista.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="f2ef4-129">Adicionar o aluno apresentará a você os inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="f2ef4-130">Para obter mais informações, consulte [inicializadores de objeto: tipos nomeados e anônimos](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f2ef4-130">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="f2ef4-131">Criar uma consulta</span><span class="sxs-lookup"><span data-stu-id="f2ef4-131">Create a Query</span></span>

<span data-ttu-id="f2ef4-132">Quando executado, a consulta adicionada nesta seção produz uma lista dos alunos cuja classificação acadêmica os coloca nos dez principais.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="f2ef4-133">Como a consulta seleciona o objeto completo a `Student` cada vez, o tipo do resultado da consulta é `IEnumerable(Of Student)` .</span><span class="sxs-lookup"><span data-stu-id="f2ef4-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="f2ef4-134">No entanto, o tipo da consulta normalmente não é especificado nas definições de consulta.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="f2ef4-135">Em vez disso, o compilador usa a inferência de tipo local para determinar o tipo.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="f2ef4-136">Para obter mais informações, consulte [inferência de tipo local](../../language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="f2ef4-136">For more information, see [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="f2ef4-137">A variável de intervalo da consulta, `currentStudent` , serve como uma referência a cada `Student` instância na origem, `students` , fornecendo acesso às propriedades de cada objeto no `students` .</span><span class="sxs-lookup"><span data-stu-id="f2ef4-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="f2ef4-138">Para criar uma consulta simples</span><span class="sxs-lookup"><span data-stu-id="f2ef4-138">To create a simple query</span></span>

1. <span data-ttu-id="f2ef4-139">Localize o local no `Main` método do projeto que está marcado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f2ef4-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="f2ef4-140">Copie o código a seguir e cole-o em.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-140">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="f2ef4-141">Posicione o ponteiro do mouse sobre `studentQuery` em seu código para verificar se o tipo atribuído ao compilador é `IEnumerable(Of Student)` .</span><span class="sxs-lookup"><span data-stu-id="f2ef4-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="f2ef4-142">Executar a Consulta</span><span class="sxs-lookup"><span data-stu-id="f2ef4-142">Run the Query</span></span>

<span data-ttu-id="f2ef4-143">A variável `studentQuery` contém a definição da consulta, não os resultados da execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="f2ef4-144">Um mecanismo típico para executar uma consulta é um `For Each` loop.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="f2ef4-145">Cada elemento na sequência retornada é acessado por meio da variável de iteração de loop.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="f2ef4-146">Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="f2ef4-146">For more information about query execution, see [Writing Your First LINQ Query](writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="f2ef4-147">Para executar a consulta</span><span class="sxs-lookup"><span data-stu-id="f2ef4-147">To run the query</span></span>

1. <span data-ttu-id="f2ef4-148">Adicione o seguinte `For Each` loop abaixo da consulta em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-148">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="f2ef4-149">Posicione o ponteiro do mouse sobre a variável de controle de loop `studentRecord` para ver seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="f2ef4-150">O tipo de `studentRecord` é inferido como `Student` , porque `studentQuery` retorna uma coleção de `Student` instâncias.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="f2ef4-151">Crie e execute o aplicativo pressionando CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="f2ef4-152">Observe os resultados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-152">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="f2ef4-153">Modificar a Consulta</span><span class="sxs-lookup"><span data-stu-id="f2ef4-153">Modify the Query</span></span>

<span data-ttu-id="f2ef4-154">É mais fácil verificar os resultados da consulta se eles estiverem em uma ordem especificada.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="f2ef4-155">Você pode classificar a sequência retornada com base em qualquer campo disponível.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-155">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="f2ef4-156">Para ordenar os resultados</span><span class="sxs-lookup"><span data-stu-id="f2ef4-156">To order the results</span></span>

1. <span data-ttu-id="f2ef4-157">Adicione a seguinte `Order By` cláusula entre a `Where` instrução e a `Select` instrução da consulta.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="f2ef4-158">A `Order By` cláusula solicitará os resultados em ordem alfabética de a a Z, de acordo com o sobrenome de cada aluno.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="f2ef4-159">Para ordenar por sobrenome e, em seguida, primeiro nome, adicione os dois campos à consulta:</span><span class="sxs-lookup"><span data-stu-id="f2ef4-159">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="f2ef4-160">Você também pode especificar `Descending` para ordenar de Z A a.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-160">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="f2ef4-161">Crie e execute o aplicativo pressionando CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="f2ef4-162">Observe os resultados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-162">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="f2ef4-163">Para introduzir um identificador local</span><span class="sxs-lookup"><span data-stu-id="f2ef4-163">To introduce a local identifier</span></span>

1. <span data-ttu-id="f2ef4-164">Adicione o código nesta seção para introduzir um identificador local na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="f2ef4-165">O identificador local manterá um resultado intermediário.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="f2ef4-166">No exemplo a seguir, `name` é um identificador que contém uma concatenação dos nomes e sobrenomes do aluno.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="f2ef4-167">Um identificador local pode ser usado para conveniência ou pode melhorar o desempenho armazenando os resultados de uma expressão que, de outra forma, seriam calculados várias vezes.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="f2ef4-168">Crie e execute o aplicativo pressionando CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="f2ef4-169">Observe os resultados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-169">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="f2ef4-170">Para projetar um campo na cláusula Select</span><span class="sxs-lookup"><span data-stu-id="f2ef4-170">To project one field in the Select clause</span></span>

1. <span data-ttu-id="f2ef4-171">Adicione a consulta e o `For Each` loop desta seção para criar uma consulta que produza uma sequência cujos elementos diferem dos elementos na origem.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="f2ef4-172">No exemplo a seguir, a origem é uma coleção de `Student` objetos, mas apenas um membro de cada objeto é retornado: o primeiro nome de alunos cujo sobrenome é Garcia.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="f2ef4-173">Como `currentStudent.First` é uma cadeia de caracteres, o tipo de dados da sequência retornada por `studentQuery3` é `IEnumerable(Of String)` , uma sequência de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="f2ef4-174">Como nos exemplos anteriores, a atribuição de um tipo de dados para `studentQuery3` é deixada para o compilador determinar usando a inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="f2ef4-175">Posicione o ponteiro do mouse sobre `studentQuery3` em seu código para verificar se o tipo atribuído é `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="f2ef4-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="f2ef4-176">Crie e execute o aplicativo pressionando CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="f2ef4-177">Observe os resultados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-177">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="f2ef4-178">Para criar um tipo anônimo na cláusula Select</span><span class="sxs-lookup"><span data-stu-id="f2ef4-178">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="f2ef4-179">Adicione o código desta seção para ver como os tipos anônimos são usados em consultas.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="f2ef4-180">Você os usa em consultas quando deseja retornar vários campos da fonte de dados em vez de registros completos ( `currentStudent` registros nos exemplos anteriores) ou campos únicos ( `First` na seção anterior).</span><span class="sxs-lookup"><span data-stu-id="f2ef4-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="f2ef4-181">Em vez de definir um novo tipo nomeado que contém os campos que você deseja incluir no resultado, você especifica os campos na `Select` cláusula e o compilador cria um tipo anônimo com esses campos como suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="f2ef4-182">Para obter mais informações, consulte [Tipos Anônimos](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f2ef4-182">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="f2ef4-183">O exemplo a seguir cria uma consulta que retorna o nome e a classificação dos seniores cuja classificação acadêmica está entre 1 e 10, em ordem de classificação acadêmica.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="f2ef4-184">Neste exemplo, o tipo de `studentQuery4` deve ser inferido porque a `Select` cláusula retorna uma instância de um tipo anônimo e um tipo anônimo não tem nenhum nome utilizável.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="f2ef4-185">Crie e execute o aplicativo pressionando CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="f2ef4-186">Observe os resultados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-186">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="f2ef4-187">Exemplos adicionais</span><span class="sxs-lookup"><span data-stu-id="f2ef4-187">Additional Examples</span></span>

<span data-ttu-id="f2ef4-188">Agora que você entende os conceitos básicos, veja a seguir uma lista de exemplos adicionais para ilustrar a flexibilidade e a potência das consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of LINQ queries.</span></span> <span data-ttu-id="f2ef4-189">Cada exemplo é precedido por uma breve descrição do que ele faz.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="f2ef4-190">Posicione o ponteiro do mouse sobre a variável de resultado da consulta para cada consulta para ver o tipo inferido.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="f2ef4-191">Use um `For Each` loop para produzir os resultados.</span><span class="sxs-lookup"><span data-stu-id="f2ef4-191">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="f2ef4-192">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="f2ef4-192">Additional Information</span></span>

<span data-ttu-id="f2ef4-193">Depois de se familiarizar com os conceitos básicos do trabalho com consultas, você estará pronto para ler a documentação e os exemplos para o tipo específico de provedor de LINQ em que você está interessado:</span><span class="sxs-lookup"><span data-stu-id="f2ef4-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of LINQ provider that you are interested in:</span></span>

- [<span data-ttu-id="f2ef4-194">Objetos LINQ to</span><span class="sxs-lookup"><span data-stu-id="f2ef4-194">LINQ to Objects</span></span>](linq-to-objects.md)

- [<span data-ttu-id="f2ef4-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f2ef4-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="f2ef4-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="f2ef4-196">LINQ to XML</span></span>](linq-to-xml.md)

- [<span data-ttu-id="f2ef4-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f2ef4-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="f2ef4-198">Confira também</span><span class="sxs-lookup"><span data-stu-id="f2ef4-198">See also</span></span>

- [<span data-ttu-id="f2ef4-199">LINQ (consulta integrada à linguagem) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2ef4-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="f2ef4-200">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2ef4-200">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="f2ef4-201">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="f2ef4-201">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="f2ef4-202">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="f2ef4-202">Object Initializers: Named and Anonymous Types</span></span>](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f2ef4-203">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="f2ef4-203">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f2ef4-204">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2ef4-204">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f2ef4-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="f2ef4-205">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="f2ef4-206">Consultas</span><span class="sxs-lookup"><span data-stu-id="f2ef4-206">Queries</span></span>](../../../language-reference/queries/index.md)
