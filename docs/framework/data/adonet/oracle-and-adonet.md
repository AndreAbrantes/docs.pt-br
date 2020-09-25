---
title: Oracle e ADO.NET
description: Saiba mais sobre os recursos e comportamentos do .NET Framework Provedor de Dados para Oracle, que fornece acesso a um banco de dados Oracle usando a interface de chamada Oracle.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 736b8dc5179a15ec219c1dae06b9ee6b5d6c3ef3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166619"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="43fd1-103">Oracle e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43fd1-103">Oracle and ADO.NET</span></span>

> [!NOTE]
> <span data-ttu-id="43fd1-104">Os tipos em <xref:System.Data.OracleClient> são preteridos.</span><span class="sxs-lookup"><span data-stu-id="43fd1-104">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="43fd1-105">Os tipos permanecem com suporte na versão atual do .NET Framework, mas serão removidos em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="43fd1-105">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="43fd1-106">A Microsoft recomenda que você use um provedor Oracle de terceiros.</span><span class="sxs-lookup"><span data-stu-id="43fd1-106">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="43fd1-107">Esta seção descreve os recursos e comportamentos específicos para o .NET Framework Provedor de Dados para Oracle.</span><span class="sxs-lookup"><span data-stu-id="43fd1-107">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="43fd1-108">O .NET Framework Provedor de Dados para Oracle fornece acesso a um banco de dados Oracle usando a interface de chamada Oracle (OCI), conforme fornecido pelo software cliente Oracle.</span><span class="sxs-lookup"><span data-stu-id="43fd1-108">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="43fd1-109">A funcionalidade do provedor de dados foi projetada para ser semelhante à do .NET Framework provedores de dados para SQL Server, OLE DB e ODBC.</span><span class="sxs-lookup"><span data-stu-id="43fd1-109">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="43fd1-110">Para usar o .NET Framework Provedor de Dados para Oracle, um aplicativo deve fazer referência ao <xref:System.Data.OracleClient> namespace da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="43fd1-110">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="43fd1-111">Você também deve incluir uma referência à DLL ao compilar seu código.</span><span class="sxs-lookup"><span data-stu-id="43fd1-111">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="43fd1-112">Por exemplo, se você estiver criando um programa C#, sua linha de comando deverá incluir:</span><span class="sxs-lookup"><span data-stu-id="43fd1-112">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="43fd1-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="43fd1-113">In This Section</span></span>  

 [<span data-ttu-id="43fd1-114">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="43fd1-114">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="43fd1-115">Descreve os requisitos para usar o .NET Framework Provedor de Dados para Oracle e descreve uma série de problemas que você deve saber ao usá-lo.</span><span class="sxs-lookup"><span data-stu-id="43fd1-115">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="43fd1-116">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="43fd1-116">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="43fd1-117">Descreve a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada no trabalho com o tipo de dados Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="43fd1-117">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="43fd1-118">Oracle LOBs</span><span class="sxs-lookup"><span data-stu-id="43fd1-118">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="43fd1-119">Descreve a classe <xref:System.Data.OracleClient.OracleLob>, que é usada para no trabalho com tipos de dados Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="43fd1-119">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="43fd1-120">REF CURSORs do Oracle</span><span class="sxs-lookup"><span data-stu-id="43fd1-120">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="43fd1-121">Descreve o suporte para o tipo de dados REF CURSOR Oracle.</span><span class="sxs-lookup"><span data-stu-id="43fd1-121">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="43fd1-122">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="43fd1-122">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="43fd1-123">Descreve estruturas que você pode usar para trabalhar com tipos de dados Oracle, incluindo <xref:System.Data.OracleClient.OracleNumber> e <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="43fd1-123">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="43fd1-124">Sequências da Oracle</span><span class="sxs-lookup"><span data-stu-id="43fd1-124">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="43fd1-125">Descreve o suporte para recuperar os principais valores de sequência Oracle gerados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="43fd1-125">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="43fd1-126">Mapeamentos de tipo de dados Oracle</span><span class="sxs-lookup"><span data-stu-id="43fd1-126">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="43fd1-127">Lista tipos de dados Oracle e seus mapeamentos para <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="43fd1-127">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="43fd1-128">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="43fd1-128">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="43fd1-129">Descreve como o objeto <xref:System.Data.OracleClient.OracleConnection> automaticamente se inscreve em uma transação distribuída existente caso determine que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="43fd1-129">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="43fd1-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="43fd1-130">Related Sections</span></span>  

 [<span data-ttu-id="43fd1-131">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43fd1-131">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="43fd1-132">Descreve práticas seguras de codificação ao usar o ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="43fd1-132">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="43fd1-133">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="43fd1-133">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="43fd1-134">Descreve como criar e usar `DataSets`, `DataSets` tipados, `DataTables` e `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="43fd1-134">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="43fd1-135">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43fd1-135">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="43fd1-136">Descreve como trabalhar com dados no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="43fd1-136">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="43fd1-137">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43fd1-137">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="43fd1-138">Descreve como trabalhar com recursos e funcionalidades que são específicos ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="43fd1-138">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="43fd1-139">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="43fd1-139">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="43fd1-140">Descreve classes genéricas que permitem que você grave código independente de provedor em ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="43fd1-140">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43fd1-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="43fd1-141">See also</span></span>

- [<span data-ttu-id="43fd1-142">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43fd1-142">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="43fd1-143">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43fd1-143">ADO.NET Overview</span></span>](ado-net-overview.md)
