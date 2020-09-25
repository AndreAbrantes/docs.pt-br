---
title: Relacionamentos de tipo em operações de consulta LINQ (C#)
description: Saiba como os tipos de variáveis em uma consulta LINQ se relacionam entre si. As operações de consulta LINQ são fortemente tipadas na fonte de dados, na consulta e na execução.
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 78cdb550e59bc82386d34f0e2bf6b1cae11d72de
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203976"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="5d54e-104">Relacionamentos de tipo em operações de consulta LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5d54e-104">Type Relationships in LINQ Query Operations (C#)</span></span>

<span data-ttu-id="5d54e-105">Para escrever consultas com eficiência, você precisa entender como os tipos de variáveis em uma operação de consulta completa se relacionam entre si.</span><span class="sxs-lookup"><span data-stu-id="5d54e-105">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="5d54e-106">Se você entender essas relações, compreenderá mais facilmente os exemplos de código e exemplos de LINQ na documentação.</span><span class="sxs-lookup"><span data-stu-id="5d54e-106">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="5d54e-107">Além disso, você compreenderá o que ocorre nos bastidores quando variáveis são tipadas de forma implícita usando `var`.</span><span class="sxs-lookup"><span data-stu-id="5d54e-107">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="5d54e-108">As operações de consulta LINQ são fortemente tipadas na fonte de dados, na própria consulta e na execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="5d54e-108">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="5d54e-109">O tipo das variáveis na consulta deve ser compatível com o tipo dos elementos na fonte de dados e com o tipo da variável de iteração na instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="5d54e-109">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="5d54e-110">Essa tipagem forte garante que erros de tipo sejam capturados em tempo de compilação, quando podem ser corrigidos antes que os usuários os encontrem.</span><span class="sxs-lookup"><span data-stu-id="5d54e-110">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="5d54e-111">Para demonstrar essas relações de tipo, a maioria dos exemplos a seguir usam tipagem explícita para todas as variáveis.</span><span class="sxs-lookup"><span data-stu-id="5d54e-111">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="5d54e-112">O último exemplo mostra como os mesmos princípios se aplicam mesmo quando você usa tipagem implícita usando [var](../../../language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="5d54e-112">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="5d54e-113">Consultas que não transformam os dados de origem</span><span class="sxs-lookup"><span data-stu-id="5d54e-113">Queries that do not Transform the Source Data</span></span>  

 <span data-ttu-id="5d54e-114">A ilustração a seguir mostra uma operação de consulta LINQ to Objects que não executa transformações nos dados.</span><span class="sxs-lookup"><span data-stu-id="5d54e-114">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="5d54e-115">A fonte contém uma sequência de cadeias de caracteres e a saída da consulta também é uma sequência de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5d54e-115">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagrama que mostra a relação dos tipos de dados em uma consulta LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="5d54e-117">O argumento de tipo da fonte de dados determina o tipo da variável de intervalo.</span><span class="sxs-lookup"><span data-stu-id="5d54e-117">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="5d54e-118">O tipo do objeto selecionado determina o tipo da variável de consulta.</span><span class="sxs-lookup"><span data-stu-id="5d54e-118">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="5d54e-119">Esta é uma cadeia de caracteres `name`.</span><span class="sxs-lookup"><span data-stu-id="5d54e-119">Here `name` is a string.</span></span> <span data-ttu-id="5d54e-120">Portanto, a variável de consulta é um `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="5d54e-120">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="5d54e-121">A variável de consulta é iterada na instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="5d54e-121">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="5d54e-122">Como a variável de consulta é uma sequência de cadeias de caracteres, a variável de iteração também é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5d54e-122">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="5d54e-123">Consultas que transformam os dados de origem</span><span class="sxs-lookup"><span data-stu-id="5d54e-123">Queries that Transform the Source Data</span></span>  

 <span data-ttu-id="5d54e-124">A ilustração a seguir mostra uma operação de consulta de [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] que executa transformações simples nos dados.</span><span class="sxs-lookup"><span data-stu-id="5d54e-124">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="5d54e-125">A consulta usa uma sequência de objetos `Customer` como entrada e seleciona somente a propriedade `Name` no resultado.</span><span class="sxs-lookup"><span data-stu-id="5d54e-125">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="5d54e-126">Como `Name` é uma cadeia de caracteres, a consulta produz uma sequência de cadeias de caracteres como saída.</span><span class="sxs-lookup"><span data-stu-id="5d54e-126">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagrama que mostra uma consulta que transforma o tipo de dados.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="5d54e-128">O argumento de tipo da fonte de dados determina o tipo da variável de intervalo.</span><span class="sxs-lookup"><span data-stu-id="5d54e-128">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="5d54e-129">A instrução `select` retorna a propriedade `Name` em vez do objeto `Customer` completo.</span><span class="sxs-lookup"><span data-stu-id="5d54e-129">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="5d54e-130">Como `Name` é uma cadeia de caracteres, o argumento de tipo de `custNameQuery` é `string` e não `Customer`.</span><span class="sxs-lookup"><span data-stu-id="5d54e-130">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="5d54e-131">Como `custNameQuery` é uma sequência de cadeias de caracteres, a variável de iteração do loop `foreach` também deve ser um `string`.</span><span class="sxs-lookup"><span data-stu-id="5d54e-131">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="5d54e-132">A ilustração a seguir mostra uma transformação um pouco mais complexa.</span><span class="sxs-lookup"><span data-stu-id="5d54e-132">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="5d54e-133">A instrução `select` retorna um tipo anônimo que captura apenas dois membros do objeto `Customer` original.</span><span class="sxs-lookup"><span data-stu-id="5d54e-133">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagrama que mostra uma consulta mais complexa que transforma o tipo de dados.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="5d54e-135">O argumento de tipo da fonte de dados sempre é o tipo da variável de intervalo na consulta.</span><span class="sxs-lookup"><span data-stu-id="5d54e-135">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="5d54e-136">Como a instrução `select` produz um tipo anônimo, a variável de consulta deve ser tipada implicitamente usando `var`.</span><span class="sxs-lookup"><span data-stu-id="5d54e-136">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="5d54e-137">Como o tipo da variável de consulta é implícito, a variável de iteração no loop `foreach` também deve ser implícito.</span><span class="sxs-lookup"><span data-stu-id="5d54e-137">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="5d54e-138">Deixando o compilador inferir informações de tipo</span><span class="sxs-lookup"><span data-stu-id="5d54e-138">Letting the compiler infer type information</span></span>  

 <span data-ttu-id="5d54e-139">Embora você precise entender as relações de tipo em uma operação de consulta, você tem a opção de permitir que o compilador fazer todo o trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d54e-139">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="5d54e-140">A palavra-chave [var](../../../language-reference/keywords/var.md) pode ser usada para qualquer variável local em uma operação de consulta.</span><span class="sxs-lookup"><span data-stu-id="5d54e-140">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="5d54e-141">A ilustração a seguir é semelhante ao exemplo número 2 que foi discutido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5d54e-141">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="5d54e-142">No entanto, o compilador fornece o tipo forte para cada variável na operação de consulta.</span><span class="sxs-lookup"><span data-stu-id="5d54e-142">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagrama que mostra o fluxo de tipo com tipagem implícita.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="5d54e-144">Para obter mais informações sobre `var`, consulte [Variáveis de local digitadas implicitamente](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="5d54e-144">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
