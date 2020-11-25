---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032242"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="f2502-101">Constantes HTTP: Headernames alteradas para static readonly</span><span class="sxs-lookup"><span data-stu-id="f2502-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="f2502-102">A partir do ASP.NET Core 3,0 Preview 5, os campos em <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> alterados de `const` para `static readonly` .</span><span class="sxs-lookup"><span data-stu-id="f2502-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="f2502-103">Para obter uma discussão, consulte [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="f2502-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f2502-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="f2502-104">Version introduced</span></span>

<span data-ttu-id="f2502-105">3.0</span><span class="sxs-lookup"><span data-stu-id="f2502-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f2502-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="f2502-106">Old behavior</span></span>

<span data-ttu-id="f2502-107">Esses campos costumava ser `const` .</span><span class="sxs-lookup"><span data-stu-id="f2502-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f2502-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="f2502-108">New behavior</span></span>

<span data-ttu-id="f2502-109">Esses campos agora são `static readonly` .</span><span class="sxs-lookup"><span data-stu-id="f2502-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f2502-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="f2502-110">Reason for change</span></span>

<span data-ttu-id="f2502-111">A alteração:</span><span class="sxs-lookup"><span data-stu-id="f2502-111">The change:</span></span>

* <span data-ttu-id="f2502-112">Impede que os valores sejam inseridos entre limites de assembly, permitindo correções de valor conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="f2502-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="f2502-113">Permite verificações de igualdade de referência mais rápidas.</span><span class="sxs-lookup"><span data-stu-id="f2502-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f2502-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="f2502-114">Recommended action</span></span>

<span data-ttu-id="f2502-115">Recompile em relação a 3,0.</span><span class="sxs-lookup"><span data-stu-id="f2502-115">Recompile against 3.0.</span></span> <span data-ttu-id="f2502-116">O código-fonte que usa esses campos das seguintes maneiras não pode mais fazer isso:</span><span class="sxs-lookup"><span data-stu-id="f2502-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="f2502-117">Como um argumento de atributo</span><span class="sxs-lookup"><span data-stu-id="f2502-117">As an attribute argument</span></span>
* <span data-ttu-id="f2502-118">Como um `case` em uma `switch` instrução</span><span class="sxs-lookup"><span data-stu-id="f2502-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="f2502-119">Ao definir outro `const`</span><span class="sxs-lookup"><span data-stu-id="f2502-119">When defining another `const`</span></span>

<span data-ttu-id="f2502-120">Para contornar a alteração significativa, alterne para usando constantes de nome de cabeçalho autodefinido ou literais de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f2502-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="f2502-121">Categoria</span><span class="sxs-lookup"><span data-stu-id="f2502-121">Category</span></span>

<span data-ttu-id="f2502-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f2502-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f2502-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f2502-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
