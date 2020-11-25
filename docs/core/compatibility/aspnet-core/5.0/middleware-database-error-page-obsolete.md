---
title: 'Alteração significativa: middleware: página de erro do banco de dados marcada como obsoleta'
description: 'Saiba mais sobre a alteração significativa no ASP.NET Core 5,0 intitulado middleware: página de erro do banco de dados marcada como obsoleta'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f828b5e20c2a9a709d675e435caa99727aebd5b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760487"
---
# <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="25841-103">Middleware: página de erro do banco de dados marcada como obsoleta</span><span class="sxs-lookup"><span data-stu-id="25841-103">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="25841-104">O [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) e seus métodos de extensão associados foram marcados como obsoletos no ASP.NET Core 5,0.</span><span class="sxs-lookup"><span data-stu-id="25841-104">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="25841-105">Os métodos de middleware e de extensão serão removidos no ASP.NET Core 6,0.</span><span class="sxs-lookup"><span data-stu-id="25841-105">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="25841-106">Em vez disso, a funcionalidade será fornecida por `DatabaseDeveloperPageExceptionFilter` e seus métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="25841-106">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="25841-107">Para obter uma discussão, consulte o problema do GitHub em [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987).</span><span class="sxs-lookup"><span data-stu-id="25841-107">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="25841-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="25841-108">Version introduced</span></span>

<span data-ttu-id="25841-109">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="25841-109">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="25841-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="25841-110">Old behavior</span></span>

<span data-ttu-id="25841-111">`DatabaseErrorPageMiddleware` e seus métodos de extensão associados não estavam obsoletos.</span><span class="sxs-lookup"><span data-stu-id="25841-111">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="25841-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="25841-112">New behavior</span></span>

<span data-ttu-id="25841-113">`DatabaseErrorPageMiddleware` e seus métodos de extensão associados são obsoletos.</span><span class="sxs-lookup"><span data-stu-id="25841-113">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="25841-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="25841-114">Reason for change</span></span>

<span data-ttu-id="25841-115">`DatabaseErrorPageMiddleware` foi migrado para uma API extensível para a [página de exceção do desenvolvedor](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span><span class="sxs-lookup"><span data-stu-id="25841-115">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="25841-116">Para obter mais informações sobre a API extensível, consulte o problema do GitHub [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).</span><span class="sxs-lookup"><span data-stu-id="25841-116">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="25841-117">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="25841-117">Recommended action</span></span>

<span data-ttu-id="25841-118">Conclua as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="25841-118">Complete the following steps:</span></span>

1. <span data-ttu-id="25841-119">Pare `DatabaseErrorPageMiddleware` de usar no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="25841-119">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="25841-120">Por exemplo, remova a `UseDatabaseErrorPage` chamada de método de `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="25841-120">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="25841-121">Adicione a página de exceção do desenvolvedor ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="25841-121">Add the developer exception page to your project.</span></span> <span data-ttu-id="25841-122">Por exemplo, chame o <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> método em `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="25841-122">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="25841-123">Adicione o pacote NuGet [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) ao arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="25841-123">Add the [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet package to the project file.</span></span>

1. <span data-ttu-id="25841-124">Adicione o filtro de exceção da página do desenvolvedor de banco de dados à coleção de serviços.</span><span class="sxs-lookup"><span data-stu-id="25841-124">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="25841-125">Por exemplo, chame o `AddDatabaseDeveloperPageExceptionFilter` método em `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="25841-125">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a><span data-ttu-id="25841-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="25841-126">Affected APIs</span></span>

- [<span data-ttu-id="25841-127">Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="25841-127">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="25841-128">Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="25841-128">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
