---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032248"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="abc69-101">Identity: o Construtor SignInManager aceita o novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="abc69-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="abc69-102">A partir do ASP.NET Core 3,0, um novo `IUserConfirmation<TUser>` parâmetro foi adicionado ao `SignInManager` Construtor.</span><span class="sxs-lookup"><span data-stu-id="abc69-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="abc69-103">Para obter mais informações, consulte [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="abc69-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="abc69-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="abc69-104">Version introduced</span></span>

<span data-ttu-id="abc69-105">3.0</span><span class="sxs-lookup"><span data-stu-id="abc69-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="abc69-106">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="abc69-106">Reason for change</span></span>

<span data-ttu-id="abc69-107">A motivação para a alteração foi adicionar suporte a novos fluxos de email/confirmação em identidade.</span><span class="sxs-lookup"><span data-stu-id="abc69-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="abc69-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="abc69-108">Recommended action</span></span>

<span data-ttu-id="abc69-109">Se você construir manualmente um `SignInManager` , forneça uma implementação de `IUserConfirmation` ou pegue uma de injeção de dependência a ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="abc69-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="abc69-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="abc69-110">Category</span></span>

<span data-ttu-id="abc69-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="abc69-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abc69-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="abc69-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
