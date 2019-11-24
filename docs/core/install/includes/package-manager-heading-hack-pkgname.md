---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450880"
---

<span data-ttu-id="6ef95-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="6ef95-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="6ef95-102">**product**</span><span class="sxs-lookup"><span data-stu-id="6ef95-102">**product**</span></span>\
<span data-ttu-id="6ef95-103">The type of .NET product to install.</span><span class="sxs-lookup"><span data-stu-id="6ef95-103">The type of .NET product to install.</span></span> <span data-ttu-id="6ef95-104">Valid options are:</span><span class="sxs-lookup"><span data-stu-id="6ef95-104">Valid options are:</span></span>

  - <span data-ttu-id="6ef95-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="6ef95-105">dotnet</span></span>
  - <span data-ttu-id="6ef95-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="6ef95-106">aspnetcore</span></span>

- <span data-ttu-id="6ef95-107">**type**</span><span class="sxs-lookup"><span data-stu-id="6ef95-107">**type**</span></span>\
<span data-ttu-id="6ef95-108">Chooses the SDK or the runtime.</span><span class="sxs-lookup"><span data-stu-id="6ef95-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="6ef95-109">Valid options are:</span><span class="sxs-lookup"><span data-stu-id="6ef95-109">Valid options are:</span></span>

  - <span data-ttu-id="6ef95-110">sdk</span><span class="sxs-lookup"><span data-stu-id="6ef95-110">sdk</span></span>
  - <span data-ttu-id="6ef95-111">runtime</span><span class="sxs-lookup"><span data-stu-id="6ef95-111">runtime</span></span>

- <span data-ttu-id="6ef95-112">**version**</span><span class="sxs-lookup"><span data-stu-id="6ef95-112">**version**</span></span>\
<span data-ttu-id="6ef95-113">The version of the SDK or runtime to install.</span><span class="sxs-lookup"><span data-stu-id="6ef95-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="6ef95-114">This article will always give the instructions for the latest supported version.</span><span class="sxs-lookup"><span data-stu-id="6ef95-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="6ef95-115">Valid options are any released version, such as:</span><span class="sxs-lookup"><span data-stu-id="6ef95-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="6ef95-116">3.0</span><span class="sxs-lookup"><span data-stu-id="6ef95-116">3.0</span></span>
  - <span data-ttu-id="6ef95-117">2.2</span><span class="sxs-lookup"><span data-stu-id="6ef95-117">2.2</span></span>
  - <span data-ttu-id="6ef95-118">2.1</span><span class="sxs-lookup"><span data-stu-id="6ef95-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="6ef95-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6ef95-119">Examples</span></span>

- <span data-ttu-id="6ef95-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="6ef95-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="6ef95-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span><span class="sxs-lookup"><span data-stu-id="6ef95-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span></span>
- <span data-ttu-id="6ef95-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="6ef95-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="6ef95-123">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="6ef95-123">Troubleshoot</span></span>

<span data-ttu-id="6ef95-124">If the package combination doesn't work, it's not available.</span><span class="sxs-lookup"><span data-stu-id="6ef95-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="6ef95-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6ef95-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="6ef95-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="6ef95-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>