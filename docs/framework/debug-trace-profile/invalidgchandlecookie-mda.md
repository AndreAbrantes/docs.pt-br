---
title: MDA invalidGCHandleCookie
description: Examine o MDA (Assistente de depuração gerenciada) invalidGCHandleCookie, que é ativado quando uma conversão de um cookie IntPtr inválido para um GCHandle é tentada.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 36806498445da78c8d9dd5c51c1903b253a39da0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272599"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="72171-103">MDA invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="72171-103">invalidGCHandleCookie MDA</span></span>

<span data-ttu-id="72171-104">O MDA (Assistente de Depuração Gerenciado) de `invalidGCHandleCookie` é ativado quando há uma tentativa de conversão de um cookie <xref:System.IntPtr> inválido em um <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="72171-104">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="72171-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="72171-105">Symptoms</span></span>  

 <span data-ttu-id="72171-106">Um comportamento indefinido, tal como violações de acesso e corrupção de memória, durante a tentativa de usar ou recuperar um <xref:System.Runtime.InteropServices.GCHandle> de um <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="72171-106">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="72171-107">Causa</span><span class="sxs-lookup"><span data-stu-id="72171-107">Cause</span></span>  

 <span data-ttu-id="72171-108">O cookie é provavelmente inválido porque ele não foi criado originalmente de um <xref:System.Runtime.InteropServices.GCHandle>, representa um <xref:System.Runtime.InteropServices.GCHandle> que já foi liberado, é um cookie para um <xref:System.Runtime.InteropServices.GCHandle> em um domínio do aplicativo diferente ou então realizou-se marshaling dele para código nativo como um <xref:System.Runtime.InteropServices.GCHandle> mas ele foi passado de volta para o CLR como um <xref:System.IntPtr>, ponto em que foi tentada uma conversão.</span><span class="sxs-lookup"><span data-stu-id="72171-108">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="72171-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="72171-109">Resolution</span></span>  

 <span data-ttu-id="72171-110">Especifique um cookie <xref:System.IntPtr> válido para o <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="72171-110">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="72171-111">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="72171-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="72171-112">Quando esse MDA está habilitado, o depurador não é capaz de rastrear as raízes de volta para seus objetos porque os valores de cookie passados de volta são diferentes daqueles retornados quando o MDA não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="72171-112">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="72171-113">Saída</span><span class="sxs-lookup"><span data-stu-id="72171-113">Output</span></span>  

 <span data-ttu-id="72171-114">O valor do cookie <xref:System.IntPtr> inválido é relatado.</span><span class="sxs-lookup"><span data-stu-id="72171-114">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="72171-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="72171-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72171-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="72171-116">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="72171-117">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="72171-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
