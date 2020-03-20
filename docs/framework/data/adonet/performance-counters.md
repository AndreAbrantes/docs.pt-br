---
title: Contadores de desempenho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: b68787980a8b64d9ee90ed8d834fab2c5c69006b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149330"
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="76d2a-102">Contadores de desempenho no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76d2a-102">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="76d2a-103">ADO.NET 2.0 introduziu suporte expandido para contadores de <xref:System.Data.SqlClient> <xref:System.Data.OracleClient>desempenho que inclui suporte para ambos e .</span><span class="sxs-lookup"><span data-stu-id="76d2a-103">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="76d2a-104">Os <xref:System.Data.SqlClient> contadores de desempenho disponíveis em versões anteriores de ADO.NET foram preteridos e substituídos pelos novos contadores de desempenho discutidos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="76d2a-104">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="76d2a-105">Você pode usar contadores de desempenho ADO.NET para monitorar o status do seu aplicativo e os recursos de conexão que ele usa.</span><span class="sxs-lookup"><span data-stu-id="76d2a-105">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="76d2a-106">Os contadores de desempenho podem ser monitorados usando o <xref:System.Diagnostics.PerformanceCounter> <xref:System.Diagnostics> Windows Performance Monitor ou podem ser acessados programáticamente usando a classe no namespace.</span><span class="sxs-lookup"><span data-stu-id="76d2a-106">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="76d2a-107">Contadores de desempenho disponíveis</span><span class="sxs-lookup"><span data-stu-id="76d2a-107">Available Performance Counters</span></span>  
 <span data-ttu-id="76d2a-108">Atualmente existem 14 contadores de <xref:System.Data.SqlClient> <xref:System.Data.OracleClient> desempenho diferentes disponíveis para e conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="76d2a-108">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="76d2a-109">Observe que os nomes dos contadores individuais não estão localizados em versões regionais do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76d2a-109">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="76d2a-110">Contador de desempenho</span><span class="sxs-lookup"><span data-stu-id="76d2a-110">Performance counter</span></span>|<span data-ttu-id="76d2a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="76d2a-111">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="76d2a-112">O número de conexões por segundo que estão sendo feitas em um servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76d2a-112">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="76d2a-113">O número de desconexões por segundo que estão sendo feitas em um servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76d2a-113">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="76d2a-114">O número de grupos de pool de conexão exclusivos que estão ativos.</span><span class="sxs-lookup"><span data-stu-id="76d2a-114">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="76d2a-115">Este contador é controlado pelo número de strings de conexão exclusivas encontradas no AppDomain.</span><span class="sxs-lookup"><span data-stu-id="76d2a-115">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="76d2a-116">O número total de piscinas de conexão.</span><span class="sxs-lookup"><span data-stu-id="76d2a-116">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="76d2a-117">O número de conexões ativas que estão atualmente em uso.</span><span class="sxs-lookup"><span data-stu-id="76d2a-117">The number of active connections that are currently in use.</span></span> <span data-ttu-id="76d2a-118">**Nota:**  Este contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="76d2a-118">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="76d2a-119">Para habilitar este contador de desempenho, consulte [Ativando contadores fora do padrão](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="76d2a-119">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="76d2a-120">O número de conexões disponíveis para uso nos pools de conexão.</span><span class="sxs-lookup"><span data-stu-id="76d2a-120">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="76d2a-121">**Nota:**  Este contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="76d2a-121">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="76d2a-122">Para habilitar este contador de desempenho, consulte [Ativando contadores fora do padrão](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="76d2a-122">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="76d2a-123">O número de grupos de pool de conexão exclusivos que são marcados para poda.</span><span class="sxs-lookup"><span data-stu-id="76d2a-123">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="76d2a-124">Este contador é controlado pelo número de strings de conexão exclusivas encontradas no AppDomain.</span><span class="sxs-lookup"><span data-stu-id="76d2a-124">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="76d2a-125">O número de piscinas de conexão inativas que não tiveram nenhuma atividade recente e estão esperando para serem eliminados.</span><span class="sxs-lookup"><span data-stu-id="76d2a-125">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="76d2a-126">O número de conexões ativas que não estão agrupadas.</span><span class="sxs-lookup"><span data-stu-id="76d2a-126">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="76d2a-127">O número de conexões ativas que estão sendo gerenciadas pela infra-estrutura de pooling de conexões.</span><span class="sxs-lookup"><span data-stu-id="76d2a-127">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="76d2a-128">O número de conexões que foram recuperadas através da coleta de lixo onde `Close` ou `Dispose` não foi chamada pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76d2a-128">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="76d2a-129">Não fechar ou descartar conexões explicitamente prejudica o desempenho.</span><span class="sxs-lookup"><span data-stu-id="76d2a-129">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="76d2a-130">O número de conexões atualmente aguardando a conclusão de uma ação e que, portanto, não estão disponíveis para uso pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76d2a-130">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="76d2a-131">O número de conexões ativas sendo retiradas do pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="76d2a-131">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="76d2a-132">**Nota:**  Este contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="76d2a-132">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="76d2a-133">Para habilitar este contador de desempenho, consulte [Ativando contadores fora do padrão](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="76d2a-133">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="76d2a-134">O número de conexões ativas que estão sendo devolvidas ao pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="76d2a-134">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="76d2a-135">**Nota:**  Este contador de desempenho não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="76d2a-135">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="76d2a-136">Para habilitar este contador de desempenho, consulte [Ativando contadores fora do padrão](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="76d2a-136">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="76d2a-137">Grupos de pool de conexão e pools de conexão</span><span class="sxs-lookup"><span data-stu-id="76d2a-137">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="76d2a-138">Ao usar a Autenticação do Windows (segurança integrada), você deve monitorar os `NumberOfActiveConnectionPoolGroups` contadores de desempenho e `NumberOfActiveConnectionPools` os contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="76d2a-138">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="76d2a-139">A razão é que os grupos de pool de conexão mapeiam para cadeias de conexão únicas.</span><span class="sxs-lookup"><span data-stu-id="76d2a-139">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="76d2a-140">Quando a segurança integrada é usada, os pools de conexões mapeiam as strings de conexão e, além disso, criam pools separados para identidades individuais do Windows.</span><span class="sxs-lookup"><span data-stu-id="76d2a-140">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="76d2a-141">Por exemplo, se Fred e Julie, cada um dentro `"Data Source=MySqlServer;Integrated Security=true"`do mesmo AppDomain, ambos usarem a seqüência de conexões, um grupo de pool de conexão é criado para a seqüência de conexões, e dois pools adicionais são criados, um para Fred e um para Julie.</span><span class="sxs-lookup"><span data-stu-id="76d2a-141">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="76d2a-142">Se John e Martha usarem uma seqüência `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`de conexão com um login sql server idêntico, então apenas um único pool será criado para a identidade **lowPrivUser.**</span><span class="sxs-lookup"><span data-stu-id="76d2a-142">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="76d2a-143">Ativando contadores off-by-default</span><span class="sxs-lookup"><span data-stu-id="76d2a-143">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="76d2a-144">Os contadores `NumberOfFreeConnections`de `NumberOfActiveConnections` `SoftDisconnectsPerSecond`desempenho `SoftConnectsPerSecond` , , e estão desligados por padrão.</span><span class="sxs-lookup"><span data-stu-id="76d2a-144">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="76d2a-145">Adicione as seguintes informações ao arquivo de configuração do aplicativo para habilitá-las:</span><span class="sxs-lookup"><span data-stu-id="76d2a-145">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="76d2a-146">Recuperando valores do contador de desempenho</span><span class="sxs-lookup"><span data-stu-id="76d2a-146">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="76d2a-147">O aplicativo de console a seguir mostra como recuperar valores do contador de desempenho em sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="76d2a-147">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="76d2a-148">As conexões devem estar abertas e ativas para que as informações sejam devolvidas para todos os contadores de desempenho ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="76d2a-148">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76d2a-149">Este exemplo usa o banco de dados **AdventureWorks** de exemplo incluído no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="76d2a-149">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="76d2a-150">As strings de conexão fornecidas no código de amostra assumem que o banco de dados está instalado e disponível no computador local com um nome de ocorrência do SqlExpress, e que você criou logins do SQL Server que correspondem aos fornecidos nas strings de conexão.</span><span class="sxs-lookup"><span data-stu-id="76d2a-150">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="76d2a-151">Você pode precisar ativar logins do SQL Server se o servidor estiver configurado usando as configurações de segurança padrão que permitem apenas a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="76d2a-151">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="76d2a-152">Modifique as strings de conexão conforme necessário para se adequar ao seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="76d2a-152">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="76d2a-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76d2a-153">Example</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's
        'FriendlyName. Replace the line above that sets the instanceName with this:
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  

```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
          "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="76d2a-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="76d2a-154">See also</span></span>

- [<span data-ttu-id="76d2a-155">Conectando a uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="76d2a-155">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="76d2a-156">Conexão do Oracle, ODBC e OLE DB Pooling</span><span class="sxs-lookup"><span data-stu-id="76d2a-156">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="76d2a-157">[Contadores de Desempenho do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="76d2a-157">[Performance Counters for ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="76d2a-158">Perfil de execução</span><span class="sxs-lookup"><span data-stu-id="76d2a-158">Runtime Profiling</span></span>](../../debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="76d2a-159">[Introdução aos limites de desempenho de monitoramento](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="76d2a-159">[Introduction to Monitoring Performance Thresholds](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- [<span data-ttu-id="76d2a-160">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="76d2a-160">ADO.NET Overview</span></span>](ado-net-overview.md)
