---
title: Enumerando instâncias do sql server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a707df533216613e34d9f357c7b9e035f73b9561
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148680"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="0f8e1-102">Enumerando instâncias do SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0f8e1-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="0f8e1-103">O SQL Server permite que aplicativos localizem instâncias do SQL Server na rede atual.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="0f8e1-104">A classe <xref:System.Data.Sql.SqlDataSourceEnumerator> expõe essas informações ao desenvolvedor de aplicativos, fornecendo um <xref:System.Data.DataTable> que contém informações sobre todos os servidores visíveis.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="0f8e1-105">Esta tabela retornada contém uma lista de instâncias de servidor disponíveis na rede que corresponde à lista fornecida quando um usuário tenta criar uma nova conexão, e expande a lista suspensa que contém todos os servidores disponíveis na caixa de diálogo **Propriedades da Conexão**.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="0f8e1-106">Os resultados exibidos nem sempre estão completos.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f8e1-107">Assim como na maioria dos serviços Windows, é melhor executar o serviço do SQL Browser com o mínimo possível de privilégios.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="0f8e1-108">Confira os Manuais Online do SQL Server para obter mais informações sobre o serviço do navegador do SQL e sobre como gerenciar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="0f8e1-109">Recuperando uma instância de enumerador</span><span class="sxs-lookup"><span data-stu-id="0f8e1-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="0f8e1-110">Para recuperar a tabela que contém informações sobre as instâncias disponíveis do SQL Server, primeiro recupere um enumerador, usando a propriedade compartilhada/estática <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A>:</span><span class="sxs-lookup"><span data-stu-id="0f8e1-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="0f8e1-111">Depois de recuperar a instância estática, você pode chamar o método <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A>, que retorna um <xref:System.Data.DataTable> que contém informações sobre os servidores disponíveis:</span><span class="sxs-lookup"><span data-stu-id="0f8e1-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="0f8e1-112">A tabela retornada da chamada de método contém as seguintes colunas e todas elas contêm valores `string`:</span><span class="sxs-lookup"><span data-stu-id="0f8e1-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="0f8e1-113">Coluna</span><span class="sxs-lookup"><span data-stu-id="0f8e1-113">Column</span></span>|<span data-ttu-id="0f8e1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f8e1-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0f8e1-115">**Servername**</span><span class="sxs-lookup"><span data-stu-id="0f8e1-115">**ServerName**</span></span>|<span data-ttu-id="0f8e1-116">O nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-116">Name of the server.</span></span>|  
|<span data-ttu-id="0f8e1-117">**Instancename**</span><span class="sxs-lookup"><span data-stu-id="0f8e1-117">**InstanceName**</span></span>|<span data-ttu-id="0f8e1-118">Nome da instância do servidor.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-118">Name of the server instance.</span></span> <span data-ttu-id="0f8e1-119">Em branco se o servidor estiver sendo executado como a instância padrão.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="0f8e1-120">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="0f8e1-120">**IsClustered**</span></span>|<span data-ttu-id="0f8e1-121">Indica se o servidor faz parte de um cluster.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="0f8e1-122">**Versão**</span><span class="sxs-lookup"><span data-stu-id="0f8e1-122">**Version**</span></span>|<span data-ttu-id="0f8e1-123">Versão do servidor.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-123">Version of the server.</span></span> <span data-ttu-id="0f8e1-124">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="0f8e1-124">For example:</span></span><br /><br /> <span data-ttu-id="0f8e1-125">-   9.00.x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="0f8e1-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="0f8e1-126">– 10.0.xx (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="0f8e1-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="0f8e1-127">-   10.50.x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="0f8e1-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="0f8e1-128">– 11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="0f8e1-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="0f8e1-129">Limitações de enumeração</span><span class="sxs-lookup"><span data-stu-id="0f8e1-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="0f8e1-130">Todos os servidores disponíveis podem ou não estar listados.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="0f8e1-131">A lista pode variar dependendo de fatores como tempos limite e tráfego de rede.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="0f8e1-132">Isso pode fazer com que a lista seja diferente em duas chamadas consecutivas.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="0f8e1-133">Somente os servidores na mesma rede serão listados.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="0f8e1-134">Os pacotes de difusão normalmente não percorrerão roteadores, motivo pelo qual você não verá um servidor listado, mas ele será estável em chamadas.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="0f8e1-135">Os servidores listados podem ou não ter informações adicionais, como `IsClustered` e versão.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="0f8e1-136">Isso depende de como a lista foi obtida.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="0f8e1-137">Servidores listados através do serviço do navegador do SQL Server terão mais detalhes do que os encontrados pela infraestrutura do Windows, que listarão somente o nome.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f8e1-138">A enumeração de servidor só está disponível quando executada em confiança total.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="0f8e1-139">Os assemblies em execução em um ambiente parcialmente confiável não poderão usá-lo, mesmo que tenham a permissão de CAS (segurança de acesso ao código) do <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="0f8e1-140">O SQL Server fornece informações para <xref:System.Data.Sql.SqlDataSourceEnumerator> usando um serviço Windows externo chamado SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="0f8e1-141">Esse serviço é habilitado por padrão, mas os administradores podem desativá-lo ou desabilitá-lo, tornando a instância do servidor invisível para essa classe.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f8e1-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f8e1-142">Example</span></span>  
 <span data-ttu-id="0f8e1-143">O aplicativo de console a seguir recupera informações sobre todas as instâncias visíveis do SQL Server e exibe as informações na janela do console.</span><span class="sxs-lookup"><span data-stu-id="0f8e1-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f8e1-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f8e1-144">See also</span></span>

- [<span data-ttu-id="0f8e1-145">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0f8e1-145">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="0f8e1-146">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0f8e1-146">ADO.NET Overview</span></span>](../ado-net-overview.md)
