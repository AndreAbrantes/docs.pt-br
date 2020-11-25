---
title: 'Como: criar tarefas pré-computadas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: e83b467e23013b5690db7cc63d061cab4d5d0e31
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734498"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="b2ac6-102">Como: criar tarefas pré-computadas</span><span class="sxs-lookup"><span data-stu-id="b2ac6-102">How to: Create Pre-Computed Tasks</span></span>

<span data-ttu-id="b2ac6-103">Esse documento descreve como usar o método <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> para recuperar os resultados das operações de download assíncronas armazenados em um cache.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="b2ac6-104">O método <xref:System.Threading.Tasks.Task.FromResult%2A> retorna um objeto <xref:System.Threading.Tasks.Task%601> que contém o valor fornecido como sua propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="b2ac6-105">Este método é útil quando você executa uma operação assíncrona que retorna um objeto <xref:System.Threading.Tasks.Task%601> e o resultado do objeto <xref:System.Threading.Tasks.Task%601> já está calculado.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2ac6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2ac6-106">Example</span></span>  

 <span data-ttu-id="b2ac6-107">O exemplo a seguir faz o download de cadeias de caracteres da Web.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="b2ac6-108">Ele define o método `DownloadStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="b2ac6-109">Esse método faz o download das cadeias de caracteres da Web de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="b2ac6-110">Este exemplo também usa um objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> para armazenar em cache os resultados de operações anteriores.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="b2ac6-111">Se o endereço de entrada for mantido no cache, o `DownloadStringAsync` usará o método <xref:System.Threading.Tasks.Task.FromResult%2A> para produzir um objeto <xref:System.Threading.Tasks.Task%601> que manterá o conteúdo nesse endereço.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="b2ac6-112">Caso contrário, o `DownloadStringAsync` baixará o arquivo da Web e adicionará o resultado ao cache.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="b2ac6-113">Esse exemplo calcula o tempo necessário para baixar várias cadeias de caracteres duas vezes.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="b2ac6-114">O segundo conjunto de operações de download deve levar menos tempo do que o primeiro conjunto porque os resultados são mantidos no cache.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="b2ac6-115">O método <xref:System.Threading.Tasks.Task.FromResult%2A> permite que o método `DownloadStringAsync` crie objetos <xref:System.Threading.Tasks.Task%601> que contêm esses resultados pré-computados.</span><span class="sxs-lookup"><span data-stu-id="b2ac6-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ac6-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b2ac6-116">See also</span></span>

- [<span data-ttu-id="b2ac6-117">Programação assíncrona baseada em tarefas</span><span class="sxs-lookup"><span data-stu-id="b2ac6-117">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
