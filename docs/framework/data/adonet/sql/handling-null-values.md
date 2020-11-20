---
title: Manipulando valores nulos
description: Saiba mais sobre como o Provedor de Dados de .NET Framework para SQL Server lida com NULL e leia sobre nulo e SqlBoolean, lógica de três valores e atribuindo valores nulos.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 2dda65f605ea9de616f01d6e52eb4e0e5def4db7
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982512"
---
# <a name="handling-null-values"></a><span data-ttu-id="61ef1-103">Manipulando valores nulos</span><span class="sxs-lookup"><span data-stu-id="61ef1-103">Handling Null Values</span></span>

<span data-ttu-id="61ef1-104">Um valor nulo em um banco de dados relacional é usado quando o valor em uma coluna é desconhecido ou está ausente.</span><span class="sxs-lookup"><span data-stu-id="61ef1-104">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="61ef1-105">Um valor nulo não é uma cadeia de caracteres vazia (para tipos de dados character ou datetime) nem um valor zero (para tipos de dados numéricos).</span><span class="sxs-lookup"><span data-stu-id="61ef1-105">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="61ef1-106">A especificação ANSI SQL-92 declara que um valor nulo deve ser o mesmo para todos os tipos de dados, para que todos os nulos sejam manipulados consistentemente.</span><span class="sxs-lookup"><span data-stu-id="61ef1-106">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="61ef1-107">O namespace <xref:System.Data.SqlTypes> fornece semântica nula ao implementar a interface <xref:System.Data.SqlTypes.INullable>.</span><span class="sxs-lookup"><span data-stu-id="61ef1-107">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="61ef1-108">Cada um dos tipos de dados no <xref:System.Data.SqlTypes> tem uma propriedade própria `IsNull` e um valor `Null` que pode ser atribuído a uma instância desse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="61ef1-108">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61ef1-109">O .NET Framework versão 2,0 introduziu suporte para tipos de valor anulável, que permitem aos programadores estender um tipo de valor para representar todos os valores do tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="61ef1-109">The .NET Framework version 2.0 introduced support for nullable value types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="61ef1-110">Esses tipos de valor anuláveis CLR representam uma instância da <xref:System.Nullable> estrutura.</span><span class="sxs-lookup"><span data-stu-id="61ef1-110">These CLR nullable value types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="61ef1-111">Essa funcionalidade é especialmente útil quando os tipos de valor são boxed e unboxed, fornecendo compatibilidade aprimorada com tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="61ef1-111">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="61ef1-112">Os tipos de valores anuláveis CLR não se destinam ao armazenamento de nulos de banco de dados porque um nulo SQL ANSI não se comporta da mesma forma que uma `null` referência (ou `Nothing` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="61ef1-112">CLR nullable value types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="61ef1-113">Para trabalhar com valores nulos ANSI SQL de banco de dados, use nulos <xref:System.Data.SqlTypes> em vez de <xref:System.Nullable>.</span><span class="sxs-lookup"><span data-stu-id="61ef1-113">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="61ef1-114">Para obter mais informações sobre como trabalhar com tipos anuláveis de valor CLR em Visual Basic consulte [tipos de valor anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)e para C#, consulte [tipos de valor anulável](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="61ef1-114">For more information on working with CLR value nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Nullable value types](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="61ef1-115">Valores nulos e lógica de três valores</span><span class="sxs-lookup"><span data-stu-id="61ef1-115">Nulls and Three-Valued Logic</span></span>  

 <span data-ttu-id="61ef1-116">Permitir valores nulos em definições de coluna apresenta uma lógica de três valores em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61ef1-116">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="61ef1-117">Uma comparação pode ser avaliada como uma das três condições:</span><span class="sxs-lookup"><span data-stu-id="61ef1-117">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="61ef1-118">True</span><span class="sxs-lookup"><span data-stu-id="61ef1-118">True</span></span>  
  
- <span data-ttu-id="61ef1-119">Falso</span><span class="sxs-lookup"><span data-stu-id="61ef1-119">False</span></span>  
  
- <span data-ttu-id="61ef1-120">Unknown (desconhecido)</span><span class="sxs-lookup"><span data-stu-id="61ef1-120">Unknown</span></span>  
  
 <span data-ttu-id="61ef1-121">Como um nulo é considerado desconhecido, dois valores nulos comparados entre si não são considerados iguais.</span><span class="sxs-lookup"><span data-stu-id="61ef1-121">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="61ef1-122">Em expressões que usam operadores aritméticos, se um dos operandos for nulo, o resultado será nulo também.</span><span class="sxs-lookup"><span data-stu-id="61ef1-122">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="61ef1-123">Nulos e SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="61ef1-123">Nulls and SqlBoolean</span></span>  

 <span data-ttu-id="61ef1-124">A comparação entre um <xref:System.Data.SqlTypes> retornará um <xref:System.Data.SqlTypes.SqlBoolean>.</span><span class="sxs-lookup"><span data-stu-id="61ef1-124">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="61ef1-125">A função `IsNull` para cada `SqlType` retorna um <xref:System.Data.SqlTypes.SqlBoolean> e pode ser usada para verificar se há valores nulos.</span><span class="sxs-lookup"><span data-stu-id="61ef1-125">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="61ef1-126">As tabelas da verdade a seguir mostram como os operadores AND, OR e NOT funcionam na presença de um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="61ef1-126">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="61ef1-127">(T = verdadeiro, F = falso e U = desconhecido ou nulo.)</span><span class="sxs-lookup"><span data-stu-id="61ef1-127">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="61ef1-128">![Tabela da verdade](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="61ef1-128">![Truth Table](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="61ef1-129">Noções básicas sobre a opção ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="61ef1-129">Understanding the ANSI_NULLS Option</span></span>  

 <span data-ttu-id="61ef1-130">O <xref:System.Data.SqlTypes> fornece a mesma semântica que quando a opção ANSI_NULLS é definida no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="61ef1-130"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="61ef1-131">Todos os operadores aritméticos (+,-, \* ,/,%), operadores de bit (~, &, \| ) e a maioria das funções retornarão NULL se qualquer um dos operandos ou argumentos for nulo, exceto para a propriedade `IsNull` .</span><span class="sxs-lookup"><span data-stu-id="61ef1-131">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, \|), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="61ef1-132">O padrão ANSI SQL-92 não oferece suporte a *columnName* = NULL em uma cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="61ef1-132">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="61ef1-133">No SQL Server, a opção ANSI_NULLS controla a nulabilidade padrão no banco de dados e a avaliação de comparações com valores nulos.</span><span class="sxs-lookup"><span data-stu-id="61ef1-133">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="61ef1-134">Se ANSI_NULLS estiver ativado (o padrão), o operador IS NULL deverá ser usado em expressões ao testar valores nulos.</span><span class="sxs-lookup"><span data-stu-id="61ef1-134">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="61ef1-135">Por exemplo, a comparação seguinte sempre retorna unknown quando ANSI_NULLS for on:</span><span class="sxs-lookup"><span data-stu-id="61ef1-135">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```sql
colname > NULL  
```  
  
 <span data-ttu-id="61ef1-136">A comparação com uma variável que contém um valor nulo também produz valores desconhecidos:</span><span class="sxs-lookup"><span data-stu-id="61ef1-136">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```sql
colname > @MyVariable  
```  
  
 <span data-ttu-id="61ef1-137">Use o predicado IS NULL ou IS NOT NULL para testar um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="61ef1-137">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="61ef1-138">Isso pode adicionar complexidade à cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="61ef1-138">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="61ef1-139">Por exemplo, a coluna TerritoryID na tabela Cliente AdventureWorks permite valores nulos.</span><span class="sxs-lookup"><span data-stu-id="61ef1-139">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="61ef1-140">Se uma instrução SELECT for testada para obter valores nulos além de outros, ela deverá incluir um predicado IS NULL:</span><span class="sxs-lookup"><span data-stu-id="61ef1-140">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="61ef1-141">Se você desativar ANSI_NULLS no SQL Server, poderá criar expressões que usam o operador de igualdade para comparar com o valor nulo.</span><span class="sxs-lookup"><span data-stu-id="61ef1-141">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="61ef1-142">No entanto, você não pode impedir que diferentes conexões configurem opções nulas para essa conexão.</span><span class="sxs-lookup"><span data-stu-id="61ef1-142">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="61ef1-143">Usar IS NULL para testar valores nulos sempre funciona, independentemente das configurações de ANSI_NULLS para uma conexão.</span><span class="sxs-lookup"><span data-stu-id="61ef1-143">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="61ef1-144">A desativação de ANSI_NULLS não é compatível em um `DataSet`, que sempre segue o padrão ANSI SQL-92 para manipular valores nulos no <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="61ef1-144">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="61ef1-145">Atribuindo valores nulos</span><span class="sxs-lookup"><span data-stu-id="61ef1-145">Assigning Null Values</span></span>  

 <span data-ttu-id="61ef1-146">Os valores nulos são especiais e suas semânticas de armazenamento e atribuição diferem em sistemas de tipos e sistemas de armazenamento diferentes.</span><span class="sxs-lookup"><span data-stu-id="61ef1-146">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="61ef1-147">Um `Dataset` foi projetado para ser usado com diferentes sistemas de tipo e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="61ef1-147">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="61ef1-148">Esta seção descreve a semântica nula para atribuir valores nulos a um <xref:System.Data.DataColumn> em um <xref:System.Data.DataRow> entre os diferentes sistemas de tipos.</span><span class="sxs-lookup"><span data-stu-id="61ef1-148">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="61ef1-149">Essa atribuição é válida para um `DataColumn` de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="61ef1-149">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="61ef1-150">Se o tipo implementa `INullable`, o `DBNull.Value` é forçado no valor nulo fortemente tipado apropriado.</span><span class="sxs-lookup"><span data-stu-id="61ef1-150">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="61ef1-151">Todos os tipos de dados <xref:System.Data.SqlTypes> implementam `INullable`.</span><span class="sxs-lookup"><span data-stu-id="61ef1-151">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="61ef1-152">Se o valor nulo fortemente tipado puder ser convertido no tipo de dados da coluna usando operadores de conversão implícitos, a atribuição deverá passar.</span><span class="sxs-lookup"><span data-stu-id="61ef1-152">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="61ef1-153">Caso contrário, uma exceção de conversão inválida será lançada.</span><span class="sxs-lookup"><span data-stu-id="61ef1-153">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="61ef1-154">Se nulo for um valor válido para o tipo de dados `DataColumn` especificado, ele será forçado no `DbNull.Value` ou no `Null` apropriado associado ao tipo `INullable` (`SqlType.Null`)</span><span class="sxs-lookup"><span data-stu-id="61ef1-154">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="61ef1-155">Para colunas UDT, os nulos são sempre armazenados com base no tipo associado à `DataColumn`.</span><span class="sxs-lookup"><span data-stu-id="61ef1-155">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="61ef1-156">Considere o caso de um UDT associado a um `DataColumn` que não implementa `INullable`, enquanto sua subclasse faz a implementação.</span><span class="sxs-lookup"><span data-stu-id="61ef1-156">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="61ef1-157">Nesse caso, se um valor nulo fortemente tipado associado à classe derivada for atribuído, ele será armazenado como um `DbNull.Value` não tipado, porque o armazenamento nulo é sempre consistente com o tipo de dados de DataColumn.</span><span class="sxs-lookup"><span data-stu-id="61ef1-157">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61ef1-158">No momento, a estrutura `Nullable<T>` ou <xref:System.Nullable> não é compatível no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="61ef1-158">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="61ef1-159">Atribuição de várias colunas (linha)</span><span class="sxs-lookup"><span data-stu-id="61ef1-159">Multiple Column (Row) Assignment</span></span>  

 <span data-ttu-id="61ef1-160">`DataTable.Add`, `DataTable.LoadDataRow` ou outras APIs que aceitam um <xref:System.Data.DataRow.ItemArray%2A> que é mapeado para uma linha, mapeiam "nulo" para o valor padrão da DataColumn.</span><span class="sxs-lookup"><span data-stu-id="61ef1-160">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="61ef1-161">Se um objeto na matriz contiver `DbNull.Value` ou sua contraparte fortemente tipada, as mesmas regras descritas acima serão aplicadas.</span><span class="sxs-lookup"><span data-stu-id="61ef1-161">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="61ef1-162">Além disso, as seguintes regras se aplicam a uma instância de atribuições nulas de `DataRow.["columnName"]`:</span><span class="sxs-lookup"><span data-stu-id="61ef1-162">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="61ef1-163">O valor *padrão* é `DbNull.Value` para todos, exceto para as colunas nulas com rigidez de tipos, em que é o valor NULL com rigidez de tipos apropriado.</span><span class="sxs-lookup"><span data-stu-id="61ef1-163">The *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="61ef1-164">Os valores nulos nunca são gravados durante a serialização para arquivos XML (como em "xsi:nil").</span><span class="sxs-lookup"><span data-stu-id="61ef1-164">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="61ef1-165">Todos os valores não nulos, incluindo os padrões, sempre são gravados durante a serialização para XML.</span><span class="sxs-lookup"><span data-stu-id="61ef1-165">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="61ef1-166">Isso é diferente da semântica XSD/XML em que um valor nulo (xsi:nil) é explícito e o valor padrão é implícito (se não estiver presente em XML, um analisador de validação poderá obtê-lo de um esquema XSD associado).</span><span class="sxs-lookup"><span data-stu-id="61ef1-166">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="61ef1-167">O oposto é verdadeiro para um `DataTable`: um valor nulo é implícito e o valor padrão é explícito.</span><span class="sxs-lookup"><span data-stu-id="61ef1-167">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="61ef1-168">Todos os valores de coluna ausentes para linhas lidas da entrada XML são atribuídos como NULL.</span><span class="sxs-lookup"><span data-stu-id="61ef1-168">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="61ef1-169">As linhas criadas usando <xref:System.Data.DataTable.NewRow%2A> ou métodos semelhantes recebem o valor padrão de DataColumn.</span><span class="sxs-lookup"><span data-stu-id="61ef1-169">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="61ef1-170">O método <xref:System.Data.DataRow.IsNull%2A> retorna `true` para `DbNull.Value` e `INullable.Null`.</span><span class="sxs-lookup"><span data-stu-id="61ef1-170">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="61ef1-171">Atribuindo valores nulos</span><span class="sxs-lookup"><span data-stu-id="61ef1-171">Assigning Null Values</span></span>  

 <span data-ttu-id="61ef1-172">O valor padrão para uma instância <xref:System.Data.SqlTypes> é nulo.</span><span class="sxs-lookup"><span data-stu-id="61ef1-172">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="61ef1-173">Os valores nulos em <xref:System.Data.SqlTypes> são específicos do tipo e não podem ser representados por um valor, como `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="61ef1-173">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="61ef1-174">Use a propriedade `IsNull` para verificar valores nulos.</span><span class="sxs-lookup"><span data-stu-id="61ef1-174">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="61ef1-175">Os valores nulos podem ser atribuídos a um <xref:System.Data.DataColumn>, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="61ef1-175">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="61ef1-176">Você pode atribuir diretamente valores nulos a variáveis `SqlTypes` sem disparar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="61ef1-176">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="61ef1-177">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61ef1-177">Example</span></span>  

 <span data-ttu-id="61ef1-178">O exemplo de código a seguir cria um <xref:System.Data.DataTable> com duas colunas definidas como <xref:System.Data.SqlTypes.SqlInt32> e <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="61ef1-178">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="61ef1-179">O código adiciona uma linha de valores conhecidos, uma linha de valores nulos e, em seguida, itera por <xref:System.Data.DataTable>, atribuindo os valores a variáveis e exibindo a saída na janela do console.</span><span class="sxs-lookup"><span data-stu-id="61ef1-179">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="61ef1-180">Esse exemplo mostra os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="61ef1-180">This example displays the following results:</span></span>  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="61ef1-181">Comparando valores nulos com SqlTypes e os tipos CLR</span><span class="sxs-lookup"><span data-stu-id="61ef1-181">Comparing Null Values with SqlTypes and CLR Types</span></span>  

 <span data-ttu-id="61ef1-182">Ao comparar valores nulos, é importante entender a diferença entre a maneira como o método `Equals` avalia valores nulos em <xref:System.Data.SqlTypes> em comparação com o modo como ele funciona com tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="61ef1-182">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="61ef1-183">Todos os métodos <xref:System.Data.SqlTypes>`Equals` usam semânticas de banco de dados para avaliar valores nulos: se um ou ambos os valores forem nulos, a comparação produzirá um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="61ef1-183">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="61ef1-184">Por outro lado, usar o método CLR `Equals` em dois <xref:System.Data.SqlTypes> produzirá true se ambos forem valores nulos.</span><span class="sxs-lookup"><span data-stu-id="61ef1-184">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="61ef1-185">Isso reflete a diferença entre usar um método de instância, como o método CLR `String.Equals`, e usar o método estático/compartilhado, `SqlString.Equals`.</span><span class="sxs-lookup"><span data-stu-id="61ef1-185">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="61ef1-186">O exemplo a seguir demonstra a diferença nos resultados entre o método `SqlString.Equals` e o método `String.Equals` quando cada um é passado por um par de valores nulos e, em seguida, um par de cadeias de caracteres vazias.</span><span class="sxs-lookup"><span data-stu-id="61ef1-186">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="61ef1-187">O código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="61ef1-187">The code produces the following output:</span></span>  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a><span data-ttu-id="61ef1-188">Confira também</span><span class="sxs-lookup"><span data-stu-id="61ef1-188">See also</span></span>

- [<span data-ttu-id="61ef1-189">Tipos de dados do SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="61ef1-189">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="61ef1-190">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="61ef1-190">ADO.NET Overview</span></span>](../ado-net-overview.md)
