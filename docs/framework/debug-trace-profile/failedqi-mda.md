---
title: MDA failedQI
description: Examine o MDA (Assistente de depuração gerenciada) do failedQI no .NET, que pode ser ativado quando uma conversão ativa ou uma chamada COM de um RCW (Runtime Callable Wrapper) falhar.
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: bbd8d5644f8620444d80845b9920b925b6891176
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244321"
---
# <a name="failedqi-mda"></a><span data-ttu-id="5cdec-103">MDA failedQI</span><span class="sxs-lookup"><span data-stu-id="5cdec-103">failedQI MDA</span></span>

<span data-ttu-id="5cdec-104">O MDA (assistente para depuração gerenciada) `failedQI` é ativado quando o tempo de execução chama `QueryInterface` em um ponteiro de interface COM em nome de um RCW (Runtime Callable Wrapper) e a chamada `QueryInterface` falha.</span><span class="sxs-lookup"><span data-stu-id="5cdec-104">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5cdec-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="5cdec-105">Symptoms</span></span>  

 <span data-ttu-id="5cdec-106">Uma conversão em um RCW falha ou uma chamada ao COM em um RCW falha inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="5cdec-106">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5cdec-107">Causa</span><span class="sxs-lookup"><span data-stu-id="5cdec-107">Cause</span></span>  
  
- <span data-ttu-id="5cdec-108">A chamada é feita do contexto incorreto.</span><span class="sxs-lookup"><span data-stu-id="5cdec-108">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="5cdec-109">O proxy registrado está falhando a chamada `QueryInterface` porque houve uma tentativa de realizar a chamada no contexto incorreto.</span><span class="sxs-lookup"><span data-stu-id="5cdec-109">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="5cdec-110">Um proxy de propriedade do OLE retornou uma falha HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5cdec-110">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5cdec-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="5cdec-111">Resolution</span></span>  

 <span data-ttu-id="5cdec-112">Consulte a documentação do MSDN sobre as regras do COM.</span><span class="sxs-lookup"><span data-stu-id="5cdec-112">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5cdec-113">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="5cdec-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="5cdec-114">Se uma chamada `QueryInterface` falhar, o contexto será alternado e haverá uma tentativa de realizar a chamada `QueryInterface` novamente para ver se um contexto incorreto estava com uma falha.</span><span class="sxs-lookup"><span data-stu-id="5cdec-114">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5cdec-115">Saída</span><span class="sxs-lookup"><span data-stu-id="5cdec-115">Output</span></span>  

 <span data-ttu-id="5cdec-116">O nome gerenciado da interface, o GUID da interface e o HRESULT da falha.</span><span class="sxs-lookup"><span data-stu-id="5cdec-116">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5cdec-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="5cdec-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cdec-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="5cdec-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5cdec-119">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="5cdec-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5cdec-120">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5cdec-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
