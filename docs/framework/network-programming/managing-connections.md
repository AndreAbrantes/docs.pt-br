---
title: Gerenciando conexões
description: Saiba como os aplicativos que usam HTTP para recursos de dados podem usar as classes .NET Framework do ServicePointManager e do ponto de extremidade para gerenciar conexões.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 00db05c99cf232a31b10bbd0356e6d43d3bc3e28
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282854"
---
# <a name="managing-connections"></a><span data-ttu-id="f35dd-103">Gerenciando conexões</span><span class="sxs-lookup"><span data-stu-id="f35dd-103">Managing Connections</span></span>

<span data-ttu-id="f35dd-104">Aplicativos que usam HTTP para se conectar aos recursos de dados podem usar as classes <xref:System.Net.ServicePoint> e <xref:System.Net.ServicePointManager> do .NET Framework para gerenciar conexões com a Internet e para ajudá-las a obter a melhor escala e desempenho.</span><span class="sxs-lookup"><span data-stu-id="f35dd-104">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="f35dd-105">A classe **ServicePoint** fornece um aplicativo com um ponto de extremidade ao qual o aplicativo pode se conectar para acessar recursos da Internet.</span><span class="sxs-lookup"><span data-stu-id="f35dd-105">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="f35dd-106">Cada **ServicePoint** contém informações que ajudam a otimizar a conexões com um servidor de Internet compartilhando informações de otimização entre as conexões para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="f35dd-106">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="f35dd-107">Cada **ServicePoint** é identificado por um URI (identificador de recurso uniforme) e é categorizado de acordo com o identificador do esquema e os fragmentos de host do URI.</span><span class="sxs-lookup"><span data-stu-id="f35dd-107">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="f35dd-108">Por exemplo, a mesma instância de **ServicePoint** oferece solicitações para os URIs `http://www.contoso.com/index.htm` e `http://www.contoso.com/news.htm?date=today`, já que eles têm o mesmo identificador de esquema (http) e fragmentos de host (`www.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="f35dd-108">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="f35dd-109">Se o aplicativo já tem uma conexão persistente para o servidor `www.contoso.com`, ele usa essa conexão para recuperar as solicitações, evitando a necessidade de criar duas conexões.</span><span class="sxs-lookup"><span data-stu-id="f35dd-109">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="f35dd-110">**ServicePointManager** é uma classe estática que gerencia a criação e destruição de instâncias de **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="f35dd-110">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="f35dd-111">O **ServicePointManager** cria um **ServicePoint** quando o aplicativo solicita um recurso de Internet que não está na coleção de instâncias **ServicePoint** existentes.</span><span class="sxs-lookup"><span data-stu-id="f35dd-111">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="f35dd-112">As instâncias **ServicePoint** são destruídas quando ultrapassaram o tempo ocioso máximo ou quando o número de instâncias **ServicePoint** existentes excede o número máximo de instâncias **ServicePoint** para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f35dd-112">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="f35dd-113">Você pode controlar o tempo ocioso máximo padrão e o número máximo de instâncias **ServicePoint** definindo as propriedades <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> e <xref:System.Net.ServicePointManager.MaxServicePoints%2A> no **ServicePointManager**.</span><span class="sxs-lookup"><span data-stu-id="f35dd-113">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="f35dd-114">O número de conexões entre um cliente e um servidor pode ter um impacto significativo na taxa de transferência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f35dd-114">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="f35dd-115">Por padrão, um aplicativo usando a classe <xref:System.Net.HttpWebRequest> usa um máximo de duas conexões persistentes para um determinado servidor, mas você pode definir o número máximo de conexões usando o aplicativo como critério.</span><span class="sxs-lookup"><span data-stu-id="f35dd-115">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f35dd-116">A especificação HTTP/1.1 limita o número de conexões de um aplicativo para duas conexões por servidor.</span><span class="sxs-lookup"><span data-stu-id="f35dd-116">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="f35dd-117">O número ideal de conexões depende das reais condições em que o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="f35dd-117">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="f35dd-118">Aumentar o número de conexões disponíveis para o aplicativo pode não afetar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f35dd-118">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="f35dd-119">Para determinar o impacto de mais conexões, execute testes de desempenho enquanto varia o número de conexões.</span><span class="sxs-lookup"><span data-stu-id="f35dd-119">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="f35dd-120">Você pode alterar o número de conexões que um aplicativo usa alterando a propriedade <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> estática na classe **ServicePointManager** na inicialização do aplicativo, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f35dd-120">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="f35dd-121">Alterar a propriedade **ServicePointManager.DefaultConnectionLimit** não afeta instâncias de **ServicePoint** inicializadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f35dd-121">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="f35dd-122">O código a seguir demonstra como alterar o limite de conexão em um **ServicePoint** existente para o servidor `http://www.contoso.com` para o valor armazenado em `newLimit`.</span><span class="sxs-lookup"><span data-stu-id="f35dd-122">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a><span data-ttu-id="f35dd-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="f35dd-123">See also</span></span>

- [<span data-ttu-id="f35dd-124">Agrupamento de conexão</span><span class="sxs-lookup"><span data-stu-id="f35dd-124">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="f35dd-125">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f35dd-125">Using Application Protocols</span></span>](using-application-protocols.md)
