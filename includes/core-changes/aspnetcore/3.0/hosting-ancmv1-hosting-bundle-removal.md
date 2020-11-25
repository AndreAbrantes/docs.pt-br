---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032236"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="777b9-101">Hospedagem: AspNetCoreModule v1 removido do pacote de hospedagem do Windows</span><span class="sxs-lookup"><span data-stu-id="777b9-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="777b9-102">A partir do ASP.NET Core 3,0, o grupo de hospedagem do Windows não conterá AspNetCoreModule (ANCM) v1.</span><span class="sxs-lookup"><span data-stu-id="777b9-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="777b9-103">O ANCM V2 é compatível com versões anteriores com ANCM OutOfProcess e é recomendado para uso com ASP.NET Core aplicativos 3,0.</span><span class="sxs-lookup"><span data-stu-id="777b9-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="777b9-104">Para obter uma discussão, consulte [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="777b9-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="777b9-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="777b9-105">Version introduced</span></span>

<span data-ttu-id="777b9-106">3.0</span><span class="sxs-lookup"><span data-stu-id="777b9-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="777b9-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="777b9-107">Old behavior</span></span>

<span data-ttu-id="777b9-108">O ANCM v1 está incluído no pacote de hospedagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="777b9-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="777b9-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="777b9-109">New behavior</span></span>

<span data-ttu-id="777b9-110">O ANCM v1 não está incluído no pacote de hospedagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="777b9-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="777b9-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="777b9-111">Reason for change</span></span>

<span data-ttu-id="777b9-112">O ANCM V2 é compatível com versões anteriores com ANCM OutOfProcess e é recomendado para uso com ASP.NET Core aplicativos 3,0.</span><span class="sxs-lookup"><span data-stu-id="777b9-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="777b9-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="777b9-113">Recommended action</span></span>

<span data-ttu-id="777b9-114">Use o ANCM V2 com aplicativos ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="777b9-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="777b9-115">Se o ANCM v1 for necessário, ele poderá ser instalado usando o pacote de hospedagem ASP.NET Core 2,1 ou 2,2 do Windows.</span><span class="sxs-lookup"><span data-stu-id="777b9-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="777b9-116">Essa alteração interromperá ASP.NET Core aplicativos 3,0 que:</span><span class="sxs-lookup"><span data-stu-id="777b9-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="777b9-117">Optamos explicitamente por usar o ANCM v1 com `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` .</span><span class="sxs-lookup"><span data-stu-id="777b9-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="777b9-118">Ter um arquivo de *web.config* personalizado com `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` .</span><span class="sxs-lookup"><span data-stu-id="777b9-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="777b9-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="777b9-119">Category</span></span>

<span data-ttu-id="777b9-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="777b9-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="777b9-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="777b9-121">Affected APIs</span></span>

<span data-ttu-id="777b9-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="777b9-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
