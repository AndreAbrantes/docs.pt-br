---
title: Construtores de cadeia de conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 8cadeac0bcbf301f7d973e93435885de82052603
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151657"
---
# <a name="connection-string-builders"></a><span data-ttu-id="1fb1d-102">Construtores de cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="1fb1d-102">Connection String Builders</span></span>
<span data-ttu-id="1fb1d-103">Em versões anteriores de ADO.NET, a verificação de tempo de compilação de strings de conexão com <xref:System.ArgumentException>valores de seqüência concatenadas não ocorreu, de modo que, em tempo de execução, uma palavra-chave incorreta gerou um .</span><span class="sxs-lookup"><span data-stu-id="1fb1d-103">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="1fb1d-104">Cada um dos provedores de dados do .NET Framework suportava sintaxe diferente para palavras-chave de seqüência de conexão, o que dificultava a construção de strings de conexão válidas se feito manualmente.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-104">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="1fb1d-105">Para resolver esse problema, ADO.NET 2.0 introduziu novos construtores de strings de conexão para cada provedor de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-105">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="1fb1d-106">Cada provedor de dados inclui uma classe de construtor de cadeia de conexão fortemente tipada que herda de <xref:System.Data.Common.DbConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="1fb1d-107">A tabela a seguir lista os provedores de dados .NET Framework e suas classes de construtor de strings de conexão associadas.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-107">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="1fb1d-108">Provedor</span><span class="sxs-lookup"><span data-stu-id="1fb1d-108">Provider</span></span>|<span data-ttu-id="1fb1d-109">Classe ConnectionStringBuilder</span><span class="sxs-lookup"><span data-stu-id="1fb1d-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="1fb1d-110">Ataques de injeção de cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="1fb1d-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="1fb1d-111">Um ataque de injeção de cadeia de conexão pode ocorrer quando a concatenação de cadeias dinâmicas é usada para criar cadeias de conexão com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="1fb1d-112">Se a cadeia de caracteres não for validada e o texto mal-intencionado ou os caracteres não forem escapados, um invasor poderá potencialmente acessar dados confidenciais ou outros recursos no servidor.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="1fb1d-113">Por exemplo, um invasor pode montar um ataque fornecendo um ponto e vírgula e acrescentando outro valor.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="1fb1d-114">A cadeia de conexão é analisada usando o algoritmo "o último vence", e a entrada hostil é substituída por um valor legítimo.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="1fb1d-115">As classes de construtores de cadeias de conexão são criadas para eliminar hipóteses e proteger contra erros de sintaxe e vulnerabilidades à segurança.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="1fb1d-116">Elas fornecem métodos e propriedades que correspondem a pares chave-valor conhecidos e permitidos por cada provedor de dados.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="1fb1d-117">Cada classe mantém uma coleção fixa de sinônimos e pode converter um sinônimo no nome da chave conhecida correspondente.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="1fb1d-118">As verificações são executadas para pares chave-valor válidos e um par inválido gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="1fb1d-119">Além disso, os valores injetados são tratados de maneira segura.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="1fb1d-120">O exemplo a seguir demonstra como <xref:System.Data.SqlClient.SqlConnectionStringBuilder> trata um valor adicional inserido para a configuração `Initial Catalog`.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 <span data-ttu-id="1fb1d-121">A saída mostra que <xref:System.Data.SqlClient.SqlConnectionStringBuilder> tratou esse valor corretamente colocando em uma sequência de escape, entre aspas duplas, o valor adicional, em vez de acrescentá-lo à cadeia de conexão como um novo par chave-valor.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="1fb1d-122">Construindo cadeias de conexão a partir de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="1fb1d-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="1fb1d-123">Se determinados elementos de uma cadeia de conexão forem conhecidos antecipadamente, eles poderão ser armazenados em um arquivo de configuração e recuperados em tempo de execução para construir uma cadeia de conexão completa.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="1fb1d-124">Por exemplo, o nome do banco de dados pode ser conhecido com antecedência, mas não o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="1fb1d-125">Ou, talvez, você deseje que um usuário forneça um nome e uma senha em tempo de execução, sem que possa injetar outros valores na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="1fb1d-126">Um dos construtores sobrecarregados de um construtor de cadeias de conexão obtém um <xref:System.String> como argumento, o que permite a você fornecer uma cadeia de conexão parcial que depois poderá ser concluída pela entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="1fb1d-127">A cadeia de conexão parcial pode ser armazenada em um arquivo de configuração e recuperada em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fb1d-128">O namespace <xref:System.Configuration> permite acesso programático aos arquivos de configuração que usam <xref:System.Web.Configuration.WebConfigurationManager> para aplicativos Web e <xref:System.Configuration.ConfigurationManager> para aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="1fb1d-129">Para obter mais informações sobre como trabalhar com strings de conexão e arquivos de configuração, consulte [Strings de conexão e arquivos de configuração](connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="1fb1d-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="1fb1d-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fb1d-130">Example</span></span>  
 <span data-ttu-id="1fb1d-131">Este exemplo demonstra como recuperar uma cadeia de conexão parcial de um arquivo de configuração e concluí-la definindo as propriedades <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A> e <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> do <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="1fb1d-132">O arquivo de configuração é definido como a seguir.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="1fb1d-133">Você deve definir uma referência à `System.Configuration.dll` em seu projeto para que o código seja executado.</span><span class="sxs-lookup"><span data-stu-id="1fb1d-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1fb1d-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="1fb1d-134">See also</span></span>

- [<span data-ttu-id="1fb1d-135">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="1fb1d-135">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="1fb1d-136">Privacidade e segurança de dados</span><span class="sxs-lookup"><span data-stu-id="1fb1d-136">Privacy and Data Security</span></span>](privacy-and-data-security.md)
- [<span data-ttu-id="1fb1d-137">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1fb1d-137">ADO.NET Overview</span></span>](ado-net-overview.md)
