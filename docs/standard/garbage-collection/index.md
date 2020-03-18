---
title: Coleta de lixo
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: 846df5ecb1e681e8d0440e627586a681bf071efa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160138"
---
# <a name="garbage-collection"></a><span data-ttu-id="395ed-102">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="395ed-102">Garbage Collection</span></span>
<span data-ttu-id="395ed-103">O coletor de lixo do .NET gerencia a alocação e a liberação de memória para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="395ed-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="395ed-104">Toda vez que você cria um novo objeto, o Common Language Runtime aloca memória para o objeto do heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="395ed-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="395ed-105">Desde que exista espaço de endereço disponível no heap gerenciado, o runtime continua alocando espaço para novos objetos.</span><span class="sxs-lookup"><span data-stu-id="395ed-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="395ed-106">No entanto, a memória não é infinita.</span><span class="sxs-lookup"><span data-stu-id="395ed-106">However, memory is not infinite.</span></span> <span data-ttu-id="395ed-107">No fim das contas, o coletor de lixo deve realizar uma coleta para liberar algum espaço na memória.</span><span class="sxs-lookup"><span data-stu-id="395ed-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="395ed-108">O mecanismo de otimização do coletor de lixo determina o melhor momento para executar uma coleta com base nas alocações que estão sendo feitas.</span><span class="sxs-lookup"><span data-stu-id="395ed-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="395ed-109">Quando o coletor de lixo executa uma coleta, ele verifica se há objetos no heap gerenciado que não estão mais sendo usados pelo aplicativo e realiza as operações necessárias para recuperar sua memória.</span><span class="sxs-lookup"><span data-stu-id="395ed-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
<a name="related_topics"></a>
## <a name="related-topics"></a><span data-ttu-id="395ed-110">Tópicos Relacionados</span><span class="sxs-lookup"><span data-stu-id="395ed-110">Related Topics</span></span>  
  
|<span data-ttu-id="395ed-111">Title</span><span class="sxs-lookup"><span data-stu-id="395ed-111">Title</span></span>|<span data-ttu-id="395ed-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="395ed-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="395ed-113">Noções básicas sobre a coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="395ed-113">Fundamentals of Garbage Collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="395ed-114">Descreve como funciona a coleta de lixo, como os objetos são alocados no heap gerenciado e outros conceitos principais.</span><span class="sxs-lookup"><span data-stu-id="395ed-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="395ed-115">Coleta de lixo e desempenho</span><span class="sxs-lookup"><span data-stu-id="395ed-115">Garbage Collection and Performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="395ed-116">Descreve as verificações de desempenho que você pode usar para diagnosticar problemas de desempenho e de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="395ed-116">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="395ed-117">Coletas Induzidas</span><span class="sxs-lookup"><span data-stu-id="395ed-117">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="395ed-118">Descreve como fazer uma coleta de lixo ocorrer.</span><span class="sxs-lookup"><span data-stu-id="395ed-118">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="395ed-119">Modos de latência</span><span class="sxs-lookup"><span data-stu-id="395ed-119">Latency Modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="395ed-120">Descreve os modos de determinam o grau de intrusão da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="395ed-120">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="395ed-121">Otimização da hospedagem Web compartilhada</span><span class="sxs-lookup"><span data-stu-id="395ed-121">Optimization for Shared Web Hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="395ed-122">Descreve como otimizar a coleta de lixo em servidores compartilhados por vários sites pequenos.</span><span class="sxs-lookup"><span data-stu-id="395ed-122">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="395ed-123">Notificações sobre a coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="395ed-123">Garbage Collection Notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="395ed-124">Descreve como determinar quando uma coleta de lixo completa está se aproximando e quando ela é concluída.</span><span class="sxs-lookup"><span data-stu-id="395ed-124">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="395ed-125">Monitoramento de recursos de domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="395ed-125">Application Domain Resource Monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="395ed-126">Descreve como monitorar o uso de CPU e memória por um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="395ed-126">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="395ed-127">Referências fracas</span><span class="sxs-lookup"><span data-stu-id="395ed-127">Weak References</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="395ed-128">Descreve os recursos que permitem que um objeto seja, simultaneamente, coletado pelo coletor de lixo e acessado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="395ed-128">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="395ed-129">Referência</span><span class="sxs-lookup"><span data-stu-id="395ed-129">Reference</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="395ed-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="395ed-130">See also</span></span>

- [<span data-ttu-id="395ed-131">Limpando recursos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="395ed-131">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
