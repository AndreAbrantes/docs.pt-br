---
title: SQL Server e ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: 6e88c35936de72f0d426c23493bbe5a08e707ee1
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979970"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="426b8-102">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="426b8-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="426b8-103">Esta seção descreve os recursos e os comportamentos que são específicos ao Provedor de Dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="426b8-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="426b8-104">O <xref:System.Data.SqlClient> fornece acesso às versões do SQL Server, o que encapsula protocolos específicos ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="426b8-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="426b8-105">A funcionalidade do provedor de dados foi criada para ser semelhante aos provedores de dados .NET Framework para OLE DB, ODBC e Oracle.</span><span class="sxs-lookup"><span data-stu-id="426b8-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="426b8-106">O <xref:System.Data.SqlClient> inclui um analisador de protocolo TDS para se comunicar diretamente com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="426b8-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="426b8-107">Para usar o Provedor de Dados .NET Framework para SQL Server, um aplicativo deve fazer referência ao namespace <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="426b8-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="426b8-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="426b8-108">In This Section</span></span>  
 <span data-ttu-id="426b8-109">[SQL Server Security](sql-server-security.md) (Segurança do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="426b8-109">[SQL Server Security](sql-server-security.md)</span></span>  
 <span data-ttu-id="426b8-110">Fornece uma visão geral dos recursos de segurança do SQL Server e cenários de aplicativos para criar aplicativos ADO.NET seguros que direcionam o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="426b8-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 <span data-ttu-id="426b8-111">[SQL Server Data Types and ADO.NET](sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="426b8-111">[SQL Server Data Types and ADO.NET](sql-server-data-types.md)</span></span>  
 <span data-ttu-id="426b8-112">Descreve como trabalhar com tipos de dados do SQL Server e como interagir com os tipos de dados do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="426b8-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 <span data-ttu-id="426b8-113">[SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="426b8-113">[SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md)</span></span>  
 <span data-ttu-id="426b8-114">Descreve como trabalhar com dados de valor grande no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="426b8-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 <span data-ttu-id="426b8-115">[SQL Server Data Operations in ADO.NET](sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="426b8-115">[SQL Server Data Operations in ADO.NET](sql-server-data-operations.md)</span></span>  
 <span data-ttu-id="426b8-116">Descreve como trabalhar com dados no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="426b8-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="426b8-117">Contém seções sobre operações de cópia em massa, MARS, operações assíncronas e parâmetros com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="426b8-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 <span data-ttu-id="426b8-118">[SQL Server Features and ADO.NET](sql-server-features-and-adonet.md) (Recursos do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="426b8-118">[SQL Server Features and ADO.NET](sql-server-features-and-adonet.md)</span></span>  
 <span data-ttu-id="426b8-119">Descreve os recursos do SQL Server que são úteis para desenvolvedores de aplicativos ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="426b8-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="426b8-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="426b8-120">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="426b8-121">Descreve os blocos de construção, os processos e as técnicas básicas necessários para criar aplicativos LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="426b8-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="426b8-122">Para obter a documentação completa do Mecanismo de Banco de Dados do SQL Server, consulte os Manuais Online do SQL Server relativos à versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="426b8-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="426b8-123">[SQL Server Books Online](/sql/sql-server/sql-server-technical-documentation) (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="426b8-123">[SQL Server Books Online](/sql/sql-server/sql-server-technical-documentation)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="426b8-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="426b8-124">See also</span></span>

- <span data-ttu-id="426b8-125">[Securing ADO.NET Applications](../securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="426b8-125">[Securing ADO.NET Applications](../securing-ado-net-applications.md)</span></span>
- <span data-ttu-id="426b8-126">[Data Type Mappings in ADO.NET](../data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="426b8-126">[Data Type Mappings in ADO.NET](../data-type-mappings-in-ado-net.md)</span></span>
- <span data-ttu-id="426b8-127">[DataSets, DataTables, and DataViews](../dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="426b8-127">[DataSets, DataTables, and DataViews](../dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="426b8-128">[Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="426b8-128">[Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="426b8-129">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="426b8-129">[ADO.NET Overview](../ado-net-overview.md)</span></span>
