---
ms.openlocfilehash: 7bf5f7e8a49acc2918dd0d68a1c54a5c277091b0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496793"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="df07f-101">Pop-ups encadeados com StaysOpen=False</span><span class="sxs-lookup"><span data-stu-id="df07f-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="df07f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="df07f-102">Details</span></span>

<span data-ttu-id="df07f-103">Um pop-up com StaysOpen=False deve fechar quando você clica fora dele.</span><span class="sxs-lookup"><span data-stu-id="df07f-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="df07f-104">Quando dois ou mais pop-ups do tipo estão encadeados (por exemplo, quando um contém o outro), há muitos problemas, incluindo:</span><span class="sxs-lookup"><span data-stu-id="df07f-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="df07f-105">Abra dois níveis, clique fora do P2, mas dentro do P1.</span><span class="sxs-lookup"><span data-stu-id="df07f-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="df07f-106">Nada acontecerá.</span><span class="sxs-lookup"><span data-stu-id="df07f-106">Nothing happens.</span></span></li><li><span data-ttu-id="df07f-107">Abra dois níveis, clique fora do P1.</span><span class="sxs-lookup"><span data-stu-id="df07f-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="df07f-108">Ambos pop-ups serão fechados.</span><span class="sxs-lookup"><span data-stu-id="df07f-108">Both popups close.</span></span></li><li><span data-ttu-id="df07f-109">Abra e feche dois níveis.</span><span class="sxs-lookup"><span data-stu-id="df07f-109">Open and close two levels.</span></span>  <span data-ttu-id="df07f-110">Em seguida, tente abrir novamente o P2.</span><span class="sxs-lookup"><span data-stu-id="df07f-110">Then try to open P2 again.</span></span>  <span data-ttu-id="df07f-111">Nada acontecerá.</span><span class="sxs-lookup"><span data-stu-id="df07f-111">Nothing happens.</span></span></li><li><span data-ttu-id="df07f-112">Tente abrir três níveis.</span><span class="sxs-lookup"><span data-stu-id="df07f-112">Try to open three levels.</span></span>  <span data-ttu-id="df07f-113">Não é possível.</span><span class="sxs-lookup"><span data-stu-id="df07f-113">You can't.</span></span>  <span data-ttu-id="df07f-114">(Nada acontece ou os dois primeiros níveis fecham, dependendo de onde você clica.) Esses casos (e outras variantes) agora funcionam conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="df07f-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="df07f-115">Nome</span><span class="sxs-lookup"><span data-stu-id="df07f-115">Name</span></span>    | <span data-ttu-id="df07f-116">Valor</span><span class="sxs-lookup"><span data-stu-id="df07f-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df07f-117">Escopo</span><span class="sxs-lookup"><span data-stu-id="df07f-117">Scope</span></span>   |<span data-ttu-id="df07f-118">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="df07f-118">Edge</span></span>|
|<span data-ttu-id="df07f-119">Versão</span><span class="sxs-lookup"><span data-stu-id="df07f-119">Version</span></span>|<span data-ttu-id="df07f-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="df07f-120">4.7.1</span></span>|
|<span data-ttu-id="df07f-121">Tipo</span><span class="sxs-lookup"><span data-stu-id="df07f-121">Type</span></span>|<span data-ttu-id="df07f-122">Runtime</span><span class="sxs-lookup"><span data-stu-id="df07f-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="df07f-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="df07f-123">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.Popup.StaysOpen`

-->
