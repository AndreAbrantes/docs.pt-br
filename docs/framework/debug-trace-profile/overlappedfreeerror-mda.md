---
title: MDA overlappedFreeError
description: Examine o MDA (Assistente de depuração gerenciada) do overlappedFreeError no .NET, que pode ser ativado em violações de acesso ou corrupção do heap coletado por lixo.
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 1bedb8ad3b9801f0d235371a397c8951ff8723b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254526"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="5e772-103">MDA overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="5e772-103">overlappedFreeError MDA</span></span>

<span data-ttu-id="5e772-104">O MDA (Assistente de Depuração Gerenciado) de `overlappedFreeError` é ativado quando o método <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> é chamado antes da conclusão da operação sobreposta.</span><span class="sxs-lookup"><span data-stu-id="5e772-104">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5e772-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="5e772-105">Symptoms</span></span>  

 <span data-ttu-id="5e772-106">Violações de acesso ou corrupção de heap coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="5e772-106">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5e772-107">Causa</span><span class="sxs-lookup"><span data-stu-id="5e772-107">Cause</span></span>  

 <span data-ttu-id="5e772-108">Uma estrutura sobreposta foi liberada antes da operação ter sido concluída.</span><span class="sxs-lookup"><span data-stu-id="5e772-108">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="5e772-109">A função que está usando o ponteiro sobreposto pode gravar a estrutura mais tarde, depois de ele ter sido liberado.</span><span class="sxs-lookup"><span data-stu-id="5e772-109">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="5e772-110">Isso pode causar corrupção de heap porque outro objeto agora pode ocupar essa região.</span><span class="sxs-lookup"><span data-stu-id="5e772-110">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="5e772-111">Esse MDA poderá não representar um erro se a operação sobreposta não for iniciada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5e772-111">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5e772-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="5e772-112">Resolution</span></span>  

 <span data-ttu-id="5e772-113">Verifique se a operação de E/S usando a estrutura sobreposta foi concluída antes de chamar o método <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29>.</span><span class="sxs-lookup"><span data-stu-id="5e772-113">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5e772-114">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="5e772-114">Effect on the Runtime</span></span>  

 <span data-ttu-id="5e772-115">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="5e772-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5e772-116">Saída</span><span class="sxs-lookup"><span data-stu-id="5e772-116">Output</span></span>  

 <span data-ttu-id="5e772-117">O demonstrado a seguir é uma saída de exemplo para esse MDA.</span><span class="sxs-lookup"><span data-stu-id="5e772-117">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="5e772-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="5e772-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e772-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="5e772-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5e772-120">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="5e772-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5e772-121">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5e772-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
