---
title: 'Mitigação: período de bloqueio de pool'
description: Saiba como atenuar os problemas causados pelo período de bloqueio do pool de conexões que está sendo removido para conexões com bancos de dados SQL do Azure.
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 270a71790f7a602df003415e9dc6dbf784cffdd7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276562"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="83073-103">Mitigação: período de bloqueio de pool</span><span class="sxs-lookup"><span data-stu-id="83073-103">Mitigation: Pool Blocking Period</span></span>

<span data-ttu-id="83073-104">O pool de conexão no período de bloqueio foi removido para conexões com bancos de dados SQL do Azure.</span><span class="sxs-lookup"><span data-stu-id="83073-104">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="83073-105">Descrição adicional</span><span class="sxs-lookup"><span data-stu-id="83073-105">Additional description</span></span>  

 <span data-ttu-id="83073-106">No .NET Framework 4.6.1 e versões anteriores, quando um aplicativo encontra uma falha de conexão transitória ao se conectar a um banco de dados, a tentativa de conexão não pode ser recuperada rapidamente, pois o pool de conexões armazena em cache o erro e o gera novamente por 5 segundos a 1 minuto. Para saber mais, confira [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md) (Pool de conexão do SQL Server (ADO.NET)).</span><span class="sxs-lookup"><span data-stu-id="83073-106">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="83073-107">Esse comportamento é problemático para conexões com bancos de dados SQL do Azure que, muitas vezes, falham com erros transitórios que normalmente são recuperados em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="83073-107">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="83073-108">O recurso de bloqueio do pool de conexões significa que o aplicativo não pode se conectar ao banco de dados por um período extenso, mesmo que o banco de dados esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="83073-108">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="83073-109">Esse comportamento é especialmente problemático para aplicativos Web que se conectam aos bancos de dados SQL do Azure e que precisam renderizar em poucos segundos.</span><span class="sxs-lookup"><span data-stu-id="83073-109">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="83073-110">Do .NET Framework 4.6.2 em diante, para solicitações de abertura da conexão com bancos de dados SQL do Azure conhecidos (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), os erros de abertura da conexão não são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="83073-110">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="83073-111">Para todas as outras tentativas de conexão, o período de bloqueio do pool de conexões continuará sendo imposto.</span><span class="sxs-lookup"><span data-stu-id="83073-111">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="83073-112">Impacto</span><span class="sxs-lookup"><span data-stu-id="83073-112">Impact</span></span>  

 <span data-ttu-id="83073-113">Essa alteração permite que a tentativa de abertura da conexão seja repetida imediatamente para bancos de dados SQL do Azure, melhorando, assim, o desempenho dos aplicativos habilitados para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="83073-113">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="83073-114">Atenuação</span><span class="sxs-lookup"><span data-stu-id="83073-114">Mitigation</span></span>  

 <span data-ttu-id="83073-115">Para aplicativos que são afetados negativamente por essa alteração, o período de bloqueio do pool de conexões pode ser configurado pela definição da nova propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83073-115">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="83073-116">O valor da propriedade é membro da enumeração <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> que pode assumir um dos três valores:</span><span class="sxs-lookup"><span data-stu-id="83073-116">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="83073-117">É possível restaurar o comportamento anterior definindo a propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> como <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83073-117">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83073-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="83073-118">See also</span></span>

- [<span data-ttu-id="83073-119">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="83073-119">Application compatibility</span></span>](application-compatibility.md)
