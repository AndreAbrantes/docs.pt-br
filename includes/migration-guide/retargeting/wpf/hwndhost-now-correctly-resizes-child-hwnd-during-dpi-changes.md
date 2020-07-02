---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617783"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="1f643-101">Agora o HwndHost redimensiona corretamente HWND filho durante alterações de DPI</span><span class="sxs-lookup"><span data-stu-id="1f643-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="1f643-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1f643-102">Details</span></span>

<span data-ttu-id="1f643-103">No .NET Framework 4.7.2 e versões anteriores, quando o WPF estava sendo executado no modo Com reconhecimento por monitor, os controles hospedados em <xref:System.Windows.Interop.HwndHost> não foram dimensionados corretamente após alterações de DPI, por exemplo, ao migrar aplicativos de um monitor para outro.</span><span class="sxs-lookup"><span data-stu-id="1f643-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="1f643-104">Com essa correção, os controles hospedados são dimensionados apropriadamente.</span><span class="sxs-lookup"><span data-stu-id="1f643-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1f643-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1f643-105">Suggestion</span></span>

<span data-ttu-id="1f643-106">Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.7.2 ou posterior e aceitar esse comportamento definindo o seguinte comutador [AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) na seção `<runtime>` do arquivo de configuração do aplicativo `false`, conforme mostrado pelo exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1f643-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1f643-107">Name</span><span class="sxs-lookup"><span data-stu-id="1f643-107">Name</span></span>    | <span data-ttu-id="1f643-108">Valor</span><span class="sxs-lookup"><span data-stu-id="1f643-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1f643-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="1f643-109">Scope</span></span>   | <span data-ttu-id="1f643-110">Principal</span><span class="sxs-lookup"><span data-stu-id="1f643-110">Major</span></span>       |
| <span data-ttu-id="1f643-111">Versão</span><span class="sxs-lookup"><span data-stu-id="1f643-111">Version</span></span> | <span data-ttu-id="1f643-112">4.8</span><span class="sxs-lookup"><span data-stu-id="1f643-112">4.8</span></span>         |
| <span data-ttu-id="1f643-113">Type</span><span class="sxs-lookup"><span data-stu-id="1f643-113">Type</span></span>    | <span data-ttu-id="1f643-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="1f643-114">Retargeting</span></span> |
