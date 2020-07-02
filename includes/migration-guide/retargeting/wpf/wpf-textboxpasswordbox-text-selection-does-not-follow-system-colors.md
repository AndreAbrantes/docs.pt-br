---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614419"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="382c3-101">A seleção de texto da caixa de TextBox/PasswordBox do WPF não segue as cores do sistema</span><span class="sxs-lookup"><span data-stu-id="382c3-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

#### <a name="details"></a><span data-ttu-id="382c3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="382c3-102">Details</span></span>

<span data-ttu-id="382c3-103">No .NET Framework 4.7.1 e nas versões anteriores, o `System.Windows.Controls.TextBox` e o `System.Windows.Controls.PasswordBox` do WPF somente podiam renderizar uma seleção de texto na camada de Adorno.</span><span class="sxs-lookup"><span data-stu-id="382c3-103">In .NET Framework 4.7.1 and earlier versions, WPF `System.Windows.Controls.TextBox` and `System.Windows.Controls.PasswordBox` could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="382c3-104">Em alguns temas do sistema, isso obstruía o texto, dificultando a leitura.</span><span class="sxs-lookup"><span data-stu-id="382c3-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="382c3-105">No .NET Framework 4.7.2 e nas versões posteriores, os desenvolvedores têm a opção de habilitar um esquema de renderização de seleção não baseado no Adorno que elimina esse problema.</span><span class="sxs-lookup"><span data-stu-id="382c3-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="382c3-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="382c3-106">Suggestion</span></span>

<span data-ttu-id="382c3-107">O desenvolvedor que desejar utilizar essa alteração precisará definir o seguinte sinalizador de AppContext adequadamente.</span><span class="sxs-lookup"><span data-stu-id="382c3-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="382c3-108">Para utilizar esse recurso, a versão instalada do .NET Framework precisará ser a 4.7.2 ou superior. Para habilitar a seleção não baseada em Adorno, use o sinalizador de AppContext a seguir.</span><span class="sxs-lookup"><span data-stu-id="382c3-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="382c3-109">Name</span><span class="sxs-lookup"><span data-stu-id="382c3-109">Name</span></span>    | <span data-ttu-id="382c3-110">Valor</span><span class="sxs-lookup"><span data-stu-id="382c3-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="382c3-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="382c3-111">Scope</span></span>   | <span data-ttu-id="382c3-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="382c3-112">Edge</span></span>        |
| <span data-ttu-id="382c3-113">Versão</span><span class="sxs-lookup"><span data-stu-id="382c3-113">Version</span></span> | <span data-ttu-id="382c3-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="382c3-114">4.7.2</span></span>       |
| <span data-ttu-id="382c3-115">Type</span><span class="sxs-lookup"><span data-stu-id="382c3-115">Type</span></span>    | <span data-ttu-id="382c3-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="382c3-116">Retargeting</span></span> |
