---
title: MDA gcUnmanagedToManaged
description: Examine o assistente de depuração gerenciada do gcManagedToUnmanaged no .NET. Este MDA pode ser ativado devido à corrupção do heap de lixo durante a transição para o código gerenciado.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
ms.openlocfilehash: 320d55224e6a204d330447d6c68eabe0fa6cf892
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415895"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="114c1-104">MDA gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="114c1-104">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="114c1-105">O MDA (assistente para depuração gerenciada) `gcUnmanagedToManaged` causa uma coleta de lixo sempre que um thread faz a transição de código não gerenciado para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="114c1-105">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="114c1-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="114c1-106">Symptoms</span></span>  
 <span data-ttu-id="114c1-107">Um aplicativo que executa componentes de usuário não gerenciados usando o COM e a invocação de plataforma está causando uma violação de acesso não determinístico no CLR.</span><span class="sxs-lookup"><span data-stu-id="114c1-107">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="114c1-108">Causa</span><span class="sxs-lookup"><span data-stu-id="114c1-108">Cause</span></span>  
 <span data-ttu-id="114c1-109">Se um aplicativo estiver executando componentes de usuário não gerenciados, esses componentes poderão ter corrompido o heap coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="114c1-109">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="114c1-110">Isso causa uma violação de acesso no CLR quando o coletor de lixo tenta percorrer o gráfico do objeto.</span><span class="sxs-lookup"><span data-stu-id="114c1-110">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="114c1-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="114c1-111">Resolution</span></span>  
 <span data-ttu-id="114c1-112">A habilitação desse assistente reduz o tempo entre o período em que o componente não gerenciado corrompe o heap coletado como lixo e o período em que ocorre a violação de acesso, forçando uma coleta de lixo antes de cada transição gerenciada.</span><span class="sxs-lookup"><span data-stu-id="114c1-112">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="114c1-113">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="114c1-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="114c1-114">Causa uma coleta de lixo sempre que um thread faz a transição de código não gerenciado para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="114c1-114">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="114c1-115">Saída</span><span class="sxs-lookup"><span data-stu-id="114c1-115">Output</span></span>  
 <span data-ttu-id="114c1-116">Esse MDA não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="114c1-116">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="114c1-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="114c1-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="114c1-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="114c1-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="114c1-119">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="114c1-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="114c1-120">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="114c1-120">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="114c1-121">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="114c1-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
