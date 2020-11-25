---
title: 'Alteração significativa: arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões'
description: 'Saiba mais sobre a alteração significativa no ASP.NET Core 5,0 intitulado arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c94a0cf213970d20559b7c061d8be220b43961e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760540"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="905ea-103">Arquivos estáticos: tipo de conteúdo CSV alterado para compatível com padrões</span><span class="sxs-lookup"><span data-stu-id="905ea-103">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="905ea-104">No ASP.NET Core 5,0, o `Content-Type` valor de cabeçalho de resposta padrão que o middleware de [arquivo estático](/aspnet/core/fundamentals/static-files) usa para arquivos *. csv* foi alterado para o valor em conformidade com os padrões `text/csv` .</span><span class="sxs-lookup"><span data-stu-id="905ea-104">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="905ea-105">Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="905ea-105">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="905ea-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="905ea-106">Version introduced</span></span>

<span data-ttu-id="905ea-107">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="905ea-107">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="905ea-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="905ea-108">Old behavior</span></span>

<span data-ttu-id="905ea-109">O `Content-Type` valor do cabeçalho `application/octet-stream` foi usado.</span><span class="sxs-lookup"><span data-stu-id="905ea-109">The `Content-Type` header value `application/octet-stream` was used.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="905ea-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="905ea-110">New behavior</span></span>

<span data-ttu-id="905ea-111">O `Content-Type` valor do cabeçalho `text/csv` é usado.</span><span class="sxs-lookup"><span data-stu-id="905ea-111">The `Content-Type` header value `text/csv` is used.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="905ea-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="905ea-112">Reason for change</span></span>

<span data-ttu-id="905ea-113">Conformidade com o padrão [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) .</span><span class="sxs-lookup"><span data-stu-id="905ea-113">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="905ea-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="905ea-114">Recommended action</span></span>

<span data-ttu-id="905ea-115">Se essa alteração impactar seu aplicativo, você poderá personalizar o mapeamento de tipo de extensão para MIME do arquivo.</span><span class="sxs-lookup"><span data-stu-id="905ea-115">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="905ea-116">Para reverter para o `application/octet-stream` tipo MIME, modifique a <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> chamada do método em `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="905ea-116">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="905ea-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="905ea-117">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="905ea-118">Para obter mais informações sobre como personalizar o mapeamento, consulte [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="905ea-118">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="905ea-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="905ea-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
