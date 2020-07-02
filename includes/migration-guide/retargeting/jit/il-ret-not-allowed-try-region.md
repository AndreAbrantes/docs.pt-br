---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615592"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="2be53-101">IL ret não é permitido em uma região try</span><span class="sxs-lookup"><span data-stu-id="2be53-101">IL ret not allowed in a try region</span></span>

#### <a name="details"></a><span data-ttu-id="2be53-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2be53-102">Details</span></span>

<span data-ttu-id="2be53-103">Ao contrário do compilador Just-In-Time JIT64, o RyuJIT (usado no .NET Framework 4.6) não permite que uma instrução IL ret em uma região try.</span><span class="sxs-lookup"><span data-stu-id="2be53-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="2be53-104">Retornar de uma região try não é permitido pela especificação ECMA-335, e nenhum compilador gerenciado conhecido gera tal IL.</span><span class="sxs-lookup"><span data-stu-id="2be53-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="2be53-105">No entanto, o compilador JIT64 executará essa IL se ela for gerada usando emissão de reflexo.</span><span class="sxs-lookup"><span data-stu-id="2be53-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2be53-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2be53-106">Suggestion</span></span>

<span data-ttu-id="2be53-107">Se um aplicativo estiver gerando uma IL que inclua um opcode ret em uma região try, o aplicativo poderá ser direcionado ao .NET Framework 4.5 para usar o JIT antigo e evitar essa interrupção.</span><span class="sxs-lookup"><span data-stu-id="2be53-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="2be53-108">Como alternativa, a IL gerada pode ser atualizado para retornar após a região try.</span><span class="sxs-lookup"><span data-stu-id="2be53-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>

| <span data-ttu-id="2be53-109">Name</span><span class="sxs-lookup"><span data-stu-id="2be53-109">Name</span></span>    | <span data-ttu-id="2be53-110">Valor</span><span class="sxs-lookup"><span data-stu-id="2be53-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2be53-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="2be53-111">Scope</span></span>   | <span data-ttu-id="2be53-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2be53-112">Edge</span></span>        |
| <span data-ttu-id="2be53-113">Versão</span><span class="sxs-lookup"><span data-stu-id="2be53-113">Version</span></span> | <span data-ttu-id="2be53-114">4.6</span><span class="sxs-lookup"><span data-stu-id="2be53-114">4.6</span></span>         |
| <span data-ttu-id="2be53-115">Type</span><span class="sxs-lookup"><span data-stu-id="2be53-115">Type</span></span>    | <span data-ttu-id="2be53-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="2be53-116">Retargeting</span></span> |
