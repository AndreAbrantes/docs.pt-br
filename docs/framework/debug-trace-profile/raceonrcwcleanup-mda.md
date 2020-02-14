---
title: MDA raceOnRCWCleanup
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: edf1fe3ee5be631f7f3c42f4a6cdb17f1be722cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216189"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="2e016-102">MDA raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="2e016-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="2e016-103">O MDA (Assistente de Depuração Gerenciado) de `raceOnRCWCleanup` é ativado quando o CLR (Common Language Runtime) detecta que um [RCW](../../standard/native-interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper) está em uso quando uma chamada para liberá-lo é feita usando um comando, assim como o método <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e016-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2e016-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="2e016-104">Symptoms</span></span>  
 <span data-ttu-id="2e016-105">Violações de acesso ou corrupção de memória durante após liberar um RCW usando <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ou um método semelhante.</span><span class="sxs-lookup"><span data-stu-id="2e016-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2e016-106">Causa</span><span class="sxs-lookup"><span data-stu-id="2e016-106">Cause</span></span>  
 <span data-ttu-id="2e016-107">O RCW está em uso em outro thread ou na pilha do thread de liberação.</span><span class="sxs-lookup"><span data-stu-id="2e016-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="2e016-108">Não é possível liberar um RCW que está em uso.</span><span class="sxs-lookup"><span data-stu-id="2e016-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2e016-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="2e016-109">Resolution</span></span>  
 <span data-ttu-id="2e016-110">Não libere um RCW que possa estar em uso no thread atual ou em outros.</span><span class="sxs-lookup"><span data-stu-id="2e016-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2e016-111">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="2e016-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="2e016-112">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="2e016-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2e016-113">Saída</span><span class="sxs-lookup"><span data-stu-id="2e016-113">Output</span></span>  
 <span data-ttu-id="2e016-114">Uma mensagem que descreve o erro.</span><span class="sxs-lookup"><span data-stu-id="2e016-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2e016-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="2e016-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e016-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e016-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="2e016-117">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="2e016-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2e016-118">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="2e016-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
