---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621768"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="64ef8-101">A Verificação Ortográfica do WPF falha de formas inesperadas</span><span class="sxs-lookup"><span data-stu-id="64ef8-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="64ef8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="64ef8-102">Details</span></span>

<span data-ttu-id="64ef8-103">Isso inclui alguns problemas da Verificação Ortográfica do WPF:</span><span class="sxs-lookup"><span data-stu-id="64ef8-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="64ef8-104">Às vezes, a Verificação Ortográfica do WPF gera <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64ef8-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="64ef8-105">A Verificação Ortográfica do WPF falha com <xref:System.UnauthorizedAccessException> quando aplicativos são iniciados usando "Executar como usuário diferente"</span><span class="sxs-lookup"><span data-stu-id="64ef8-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="64ef8-106">O Verificador Ortográfico do WPF identifica incorretamente erros ortográficos em palavras compostas, como "Hausnummer" em alemão.</span><span class="sxs-lookup"><span data-stu-id="64ef8-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="64ef8-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="64ef8-107">Suggestion</span></span>

<span data-ttu-id="64ef8-108">Problema nº 1 – esse problema foi corrigido no .NET Framework 4.6.2 Problema nº 2 – a Verificação Ortográfica do WPF deixou de ter suporte quando aplicativos são iniciados usando "Executar como usuário diferente".</span><span class="sxs-lookup"><span data-stu-id="64ef8-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="64ef8-109">A partir do .NET Framework 4.6.2, aplicativos iniciados dessa maneira não falharão inesperadamente, em vez disso, a Verificação Ortográfica será desabilitada silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="64ef8-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="64ef8-110">Problema nº 3 – esse problema foi corrigido no .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="64ef8-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="64ef8-111">Name</span><span class="sxs-lookup"><span data-stu-id="64ef8-111">Name</span></span>    | <span data-ttu-id="64ef8-112">Valor</span><span class="sxs-lookup"><span data-stu-id="64ef8-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="64ef8-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="64ef8-113">Scope</span></span>   |<span data-ttu-id="64ef8-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="64ef8-114">Edge</span></span>|
|<span data-ttu-id="64ef8-115">Versão</span><span class="sxs-lookup"><span data-stu-id="64ef8-115">Version</span></span>|<span data-ttu-id="64ef8-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="64ef8-116">4.6.1</span></span>|
|<span data-ttu-id="64ef8-117">Type</span><span class="sxs-lookup"><span data-stu-id="64ef8-117">Type</span></span>|<span data-ttu-id="64ef8-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="64ef8-118">Runtime</span></span>|
