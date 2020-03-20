---
title: Estatísticas do provedor para SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 5e37a04ff731a99664d636e0d4175f99214c2646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174505"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="2452f-102">Estatísticas do provedor para SQL Server</span><span class="sxs-lookup"><span data-stu-id="2452f-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="2452f-103">A partir da versão 2.0 do .NET Framework, o provedor de dados do .NET Framework para SQL Server dá suporte a estatísticas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2452f-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="2452f-104">Você precisa habilitar as estatísticas configurando a propriedade <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> do objeto <xref:System.Data.SqlClient.SqlConnection> como `True` depois de criar um objeto de conexão válido.</span><span class="sxs-lookup"><span data-stu-id="2452f-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="2452f-105">Depois que as estatísticas forem habilitadas, você poderá examiná-las como um "instantâneo no tempo" ao recuperar uma referência de <xref:System.Collections.IDictionary> por meio do método <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> do objeto <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="2452f-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="2452f-106">Você enumera os itens na lista como um conjunto de entradas de dicionário de pares de nome/valor.</span><span class="sxs-lookup"><span data-stu-id="2452f-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="2452f-107">Esses pares de nome/valor não são ordenados.</span><span class="sxs-lookup"><span data-stu-id="2452f-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="2452f-108">A qualquer momento, você pode chamar o método <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> do objeto <xref:System.Data.SqlClient.SqlConnection> para redefinir os contadores.</span><span class="sxs-lookup"><span data-stu-id="2452f-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="2452f-109">Se a coleta de estatísticas não tiver sido habilitada, uma exceção não será gerada.</span><span class="sxs-lookup"><span data-stu-id="2452f-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="2452f-110">Além disso, se <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> for chamado sem <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> ter sido chamado primeiro, os valores recuperados serão os valores iniciais para cada entrada.</span><span class="sxs-lookup"><span data-stu-id="2452f-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="2452f-111">Se você habilitar estatísticas, execute seu aplicativo por um tempo e, em seguida, desabilite as estatísticas. Os valores recuperados refletirão os valores coletados até o ponto em que as estatísticas tiverem sido desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="2452f-112">Todos os valores estatísticos coletados são contabilizados por conexão.</span><span class="sxs-lookup"><span data-stu-id="2452f-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="2452f-113">Valores estatísticos disponíveis</span><span class="sxs-lookup"><span data-stu-id="2452f-113">Statistical Values Available</span></span>  
 <span data-ttu-id="2452f-114">Atualmente, há 18 itens diferentes disponíveis no provedor do Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2452f-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="2452f-115">O número de itens disponíveis pode ser acessado por meio da propriedade **Count** da referência da interface <xref:System.Collections.IDictionary> retornada pelo <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span><span class="sxs-lookup"><span data-stu-id="2452f-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="2452f-116">Todos os contadores para estatísticas do provedor usam o tipo de common language runtime <xref:System.Int64> (**long** no C# e no Visual Basic), que tem 64 bits de largura.</span><span class="sxs-lookup"><span data-stu-id="2452f-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="2452f-117">O valor máximo do tipo de dados **int64**, conforme definido pelo campo **int64.MaxValue**, é ((2^63)-1)).</span><span class="sxs-lookup"><span data-stu-id="2452f-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="2452f-118">Quando os valores para os contadores atingem esse valor máximo, eles não devem mais ser considerados precisos.</span><span class="sxs-lookup"><span data-stu-id="2452f-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="2452f-119">Isso significa que **int64.MaxValue**-1((2^63)-2) é efetivamente o maior valor válido para qualquer estatística.</span><span class="sxs-lookup"><span data-stu-id="2452f-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2452f-120">Um dicionário é usado para retornar estatísticas do provedor porque o número, os nomes e a ordem das estatísticas retornadas podem ser alterados no futuro.</span><span class="sxs-lookup"><span data-stu-id="2452f-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="2452f-121">Os aplicativos não devem depender de um valor específico encontrado no dicionário, mas devem verificar se o valor está lá e ramificar de acordo.</span><span class="sxs-lookup"><span data-stu-id="2452f-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="2452f-122">A tabela a seguir descreve os valores estatísticos atuais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2452f-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="2452f-123">Observe que os nomes de chave para os valores individuais não são localizados em versões regionais do Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2452f-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="2452f-124">Nome da Chave</span><span class="sxs-lookup"><span data-stu-id="2452f-124">Key Name</span></span>|<span data-ttu-id="2452f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="2452f-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="2452f-126">Retorna o número de pacotes de protocolo TDS recebidos pelo provedor de SQL Server depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="2452f-127">Retorna o número de pacotes TDS enviados ao SQL Server pelo provedor após as estatísticas terem sido habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="2452f-128">Comandos grandes podem exigir vários buffers.</span><span class="sxs-lookup"><span data-stu-id="2452f-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="2452f-129">Por exemplo, se um comando grande for enviado para o servidor e ele exigir seis pacotes, `ServerRoundtrips` será incrementado em um e `BuffersSent` será incrementado em seis.</span><span class="sxs-lookup"><span data-stu-id="2452f-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="2452f-130">Retorna o número de bytes de dados nos pacotes TDS recebidos pelo provedor do SQL Server depois que o aplicativo é iniciado usando o provedor e as estatísticas do aplicativo são habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="2452f-131">Retorna o número de bytes de dados enviados ao SQL Server em pacotes TDS depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="2452f-132">A quantidade de tempo (em milissegundos) durante o qual a conexão ficou aberta após a habilitação das estatísticas (tempo total de conexão se as estatísticas foram habilitadas antes de abrir a conexão).</span><span class="sxs-lookup"><span data-stu-id="2452f-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="2452f-133">Retorna o número de vezes que um cursor foi aberto por meio da conexão depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="2452f-134">Observe que os resultados somente leitura/somente encaminhamento retornados por instruções SELECT não são considerados cursores e, portanto, não afetam esse contador.</span><span class="sxs-lookup"><span data-stu-id="2452f-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="2452f-135">Retorna a quantidade cumulativa de tempo (em milissegundos) que o provedor gastou processando depois que as estatísticas foram habilitadas, incluindo o tempo gasto aguardando respostas do servidor, bem como o tempo gasto executando código no próprio provedor.</span><span class="sxs-lookup"><span data-stu-id="2452f-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="2452f-136">As classes que incluem o código de tempo são:</span><span class="sxs-lookup"><span data-stu-id="2452f-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="2452f-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="2452f-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="2452f-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="2452f-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="2452f-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="2452f-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="2452f-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="2452f-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="2452f-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="2452f-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="2452f-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="2452f-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="2452f-143">Para manter os membros críticos para o desempenho tão pequenos quanto possível, os seguintes membros não são cronometrados:</span><span class="sxs-lookup"><span data-stu-id="2452f-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="2452f-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="2452f-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="2452f-145">operador this[] (todas as sobrecargas)</span><span class="sxs-lookup"><span data-stu-id="2452f-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="2452f-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="2452f-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="2452f-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="2452f-147">GetChar</span></span><br /><br /> <span data-ttu-id="2452f-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="2452f-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="2452f-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="2452f-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="2452f-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="2452f-150">GetDouble</span></span><br /><br /> <span data-ttu-id="2452f-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="2452f-151">GetFloat</span></span><br /><br /> <span data-ttu-id="2452f-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="2452f-152">GetGuid</span></span><br /><br /> <span data-ttu-id="2452f-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="2452f-153">GetInt16</span></span><br /><br /> <span data-ttu-id="2452f-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="2452f-154">GetInt32</span></span><br /><br /> <span data-ttu-id="2452f-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="2452f-155">GetInt64</span></span><br /><br /> <span data-ttu-id="2452f-156">GetName</span><span class="sxs-lookup"><span data-stu-id="2452f-156">GetName</span></span><br /><br /> <span data-ttu-id="2452f-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="2452f-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="2452f-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="2452f-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="2452f-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="2452f-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="2452f-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="2452f-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="2452f-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="2452f-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="2452f-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="2452f-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="2452f-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="2452f-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="2452f-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="2452f-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="2452f-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="2452f-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="2452f-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="2452f-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="2452f-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="2452f-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="2452f-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="2452f-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="2452f-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="2452f-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="2452f-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="2452f-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="2452f-171">GetString</span><span class="sxs-lookup"><span data-stu-id="2452f-171">GetString</span></span><br /><br /> <span data-ttu-id="2452f-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="2452f-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="2452f-173">Retorna o número total de instruções INSERT, DELETE e UPDATE executadas por meio da conexão depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="2452f-174">Retorna o número total de linhas afetadas por instruções INSERT, DELETE e UPDATE executadas por meio da conexão depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="2452f-175">Retorna a quantidade cumulativa de tempo (em milissegundos) que o provedor gastou esperando por respostas do servidor depois que o aplicativo foi iniciado usando o provedor as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="2452f-176">Retorna o número de comandos preparados executados por meio da conexão depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="2452f-177">Retorna o número de instruções preparadas por meio da conexão depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="2452f-178">Retorna o número de instruções SELECT executadas por meio da conexão depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="2452f-179">Isso inclui instruções FETCH para recuperar linhas de cursores e a contagem de instruções SELECT é atualizada quando o final de um <xref:System.Data.SqlClient.SqlDataReader> é atingido.</span><span class="sxs-lookup"><span data-stu-id="2452f-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="2452f-180">Retorna o número de linhas selecionadas depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="2452f-181">Esse contador reflete todas as linhas geradas por instruções SQL, mesmo aquelas que não foram realmente consumidas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="2452f-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="2452f-182">Por exemplo, fechar um leitor de dados antes de ler o conjunto de resultados inteiro não afetaria a contagem.</span><span class="sxs-lookup"><span data-stu-id="2452f-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="2452f-183">Isso inclui as linhas recuperadas de cursores por meio de instruções FETCH.</span><span class="sxs-lookup"><span data-stu-id="2452f-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="2452f-184">Retorna o número de vezes que a conexão enviou comandos ao servidor e recebeu uma resposta depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="2452f-185">Retorna o número de conjuntos de resultados que foram usados depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="2452f-186">Por exemplo, isso inclui qualquer conjunto de resultados retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="2452f-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="2452f-187">Para cursores, cada operação de busca ou de busca de bloco é considerada um conjunto de resultados independente.</span><span class="sxs-lookup"><span data-stu-id="2452f-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="2452f-188">Retorna o número de transações de usuário iniciadas depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas, incluindo reversões.</span><span class="sxs-lookup"><span data-stu-id="2452f-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="2452f-189">Se uma conexão estiver em execução com a confirmação automática ativa, cada comando será considerado uma transação.</span><span class="sxs-lookup"><span data-stu-id="2452f-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="2452f-190">Esse contador incrementa a contagem de transações assim que uma instrução BEGIN TRAN é executada, independentemente de a transação ser confirmada ou revertida mais tarde.</span><span class="sxs-lookup"><span data-stu-id="2452f-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="2452f-191">Retorna o número de instruções cuja preparação foi cancelada que são executadas por meio da conexão depois que o aplicativo foi iniciado usando o provedor e as estatísticas do aplicativo foram habilitadas.</span><span class="sxs-lookup"><span data-stu-id="2452f-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="2452f-192">Recuperando um valor</span><span class="sxs-lookup"><span data-stu-id="2452f-192">Retrieving a Value</span></span>  
 <span data-ttu-id="2452f-193">O aplicativo de console a seguir mostra como habilitar estatísticas em uma conexão, recuperar quatro valores de estatística individuais e gravá-los na janela do console.</span><span class="sxs-lookup"><span data-stu-id="2452f-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2452f-194">O exemplo a seguir usa o banco de dados de exemplo **AdventureWorks** incluído com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2452f-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="2452f-195">A cadeia de conexão fornecida no código de exemplo pressupõe que o banco de dados está instalado e disponível no computador local.</span><span class="sxs-lookup"><span data-stu-id="2452f-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="2452f-196">Modifique a cadeia de conexão conforme necessário para o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="2452f-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="2452f-197">Recuperando todos os valores</span><span class="sxs-lookup"><span data-stu-id="2452f-197">Retrieving All Values</span></span>  
 <span data-ttu-id="2452f-198">O aplicativo de console a seguir mostra como habilitar estatísticas em uma conexão, recuperar todos os valores de estatística disponíveis usando o enumerador e gravá-los na janela do console.</span><span class="sxs-lookup"><span data-stu-id="2452f-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2452f-199">O exemplo a seguir usa o banco de dados de exemplo **AdventureWorks** incluído com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2452f-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="2452f-200">A cadeia de conexão fornecida no código de exemplo pressupõe que o banco de dados está instalado e disponível no computador local.</span><span class="sxs-lookup"><span data-stu-id="2452f-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="2452f-201">Modifique a cadeia de conexão conforme necessário para o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="2452f-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2452f-202">Confira também</span><span class="sxs-lookup"><span data-stu-id="2452f-202">See also</span></span>

- [<span data-ttu-id="2452f-203">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2452f-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="2452f-204">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2452f-204">ADO.NET Overview</span></span>](../ado-net-overview.md)
