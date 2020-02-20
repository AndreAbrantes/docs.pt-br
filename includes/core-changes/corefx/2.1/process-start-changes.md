---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449381"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="3b11d-101">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="3b11d-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="3b11d-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> tem um valor padrão de `false` no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b11d-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="3b11d-103">Em .NET Framework, seu valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="3b11d-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3b11d-104">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="3b11d-104">Change description</span></span>

<span data-ttu-id="3b11d-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> permite que você inicie um aplicativo diretamente, por exemplo, com um código como `Process.Start("mspaint.exe")` que inicia o Paint.</span><span class="sxs-lookup"><span data-stu-id="3b11d-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="3b11d-106">Ele também permite que você inicie indiretamente um aplicativo associado se <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> estiver definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="3b11d-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="3b11d-107">No .NET Framework, o valor padrão de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> é `true`, o que significa que o código como `Process.Start("mytextfile.txt")` iniciaria o bloco de notas, se você tiver associado arquivos *. txt* com esse editor.</span><span class="sxs-lookup"><span data-stu-id="3b11d-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="3b11d-108">Para evitar a inicialização indireta de um aplicativo no .NET Framework, você deve definir explicitamente <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> como `false`.</span><span class="sxs-lookup"><span data-stu-id="3b11d-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="3b11d-109">No .NET Core, o valor padrão para <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="3b11d-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="3b11d-110">Isso significa que, por padrão, os aplicativos associados não são iniciados quando você chama `Process.Start`.</span><span class="sxs-lookup"><span data-stu-id="3b11d-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="3b11d-111">Essa alteração foi introduzida no .NET Core por motivos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="3b11d-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="3b11d-112">Normalmente, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> é usado para iniciar um aplicativo diretamente.</span><span class="sxs-lookup"><span data-stu-id="3b11d-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="3b11d-113">Iniciar um aplicativo diretamente não precisa envolver o Shell do Windows e incorrer no custo de desempenho associado.</span><span class="sxs-lookup"><span data-stu-id="3b11d-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="3b11d-114">Para tornar esse caso padrão mais rápido, o .NET Core altera o valor padrão de <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> para `false`.</span><span class="sxs-lookup"><span data-stu-id="3b11d-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="3b11d-115">Você pode aceitar o caminho mais lento se precisar dele.</span><span class="sxs-lookup"><span data-stu-id="3b11d-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3b11d-116">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="3b11d-116">Version introduced</span></span>

<span data-ttu-id="3b11d-117">2.1</span><span class="sxs-lookup"><span data-stu-id="3b11d-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="3b11d-118">Em versões anteriores do .NET Core, `UseShellExecute` não foi implementada para o Windows.</span><span class="sxs-lookup"><span data-stu-id="3b11d-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3b11d-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="3b11d-119">Recommended action</span></span>

<span data-ttu-id="3b11d-120">Se seu aplicativo depender do comportamento antigo, chame <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> com <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> definido como `true` no objeto <xref:System.Diagnostics.ProcessStartInfo>.</span><span class="sxs-lookup"><span data-stu-id="3b11d-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="3b11d-121">Categoria</span><span class="sxs-lookup"><span data-stu-id="3b11d-121">Category</span></span>

<span data-ttu-id="3b11d-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="3b11d-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3b11d-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3b11d-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
