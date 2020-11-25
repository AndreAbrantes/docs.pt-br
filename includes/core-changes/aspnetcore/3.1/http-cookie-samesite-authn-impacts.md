---
ms.openlocfilehash: 8b6d334677991382d235fd53cd3c98e3a77d650d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032224"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="51d1c-101">HTTP: navegador SameSite alterações de impacto na autenticação</span><span class="sxs-lookup"><span data-stu-id="51d1c-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="51d1c-102">Alguns navegadores, como Chrome e Firefox, fizeram alterações significativas em suas implementações de `SameSite` cookies.</span><span class="sxs-lookup"><span data-stu-id="51d1c-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="51d1c-103">As alterações afetam os cenários de autenticação remota, como OpenID Connect e WS-Federation, que devem ser recusadas enviando `SameSite=None` .</span><span class="sxs-lookup"><span data-stu-id="51d1c-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="51d1c-104">No entanto, o `SameSite=None` interrompe o IOS 12 e algumas versões mais antigas de outros navegadores.</span><span class="sxs-lookup"><span data-stu-id="51d1c-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="51d1c-105">O aplicativo precisa farejar essas versões e omitir `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="51d1c-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="51d1c-106">Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="51d1c-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="51d1c-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="51d1c-107">Version introduced</span></span>

<span data-ttu-id="51d1c-108">3,1 visualização 1</span><span class="sxs-lookup"><span data-stu-id="51d1c-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="51d1c-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="51d1c-109">Old behavior</span></span>

<span data-ttu-id="51d1c-110">`SameSite` é uma extensão padrão de rascunho 2016 para cookies HTTP.</span><span class="sxs-lookup"><span data-stu-id="51d1c-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="51d1c-111">Ele se destina a reduzir a falsificação de solicitação entre sites (CSRF).</span><span class="sxs-lookup"><span data-stu-id="51d1c-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="51d1c-112">Isso foi originalmente projetado como um recurso que os servidores optaram por adicionar os novos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="51d1c-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="51d1c-113">ASP.NET Core 2,0 adicionou suporte inicial para `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="51d1c-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="51d1c-114">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="51d1c-114">New behavior</span></span>

<span data-ttu-id="51d1c-115">O Google propôs um novo padrão de rascunho que não é compatível com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="51d1c-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="51d1c-116">O padrão altera o modo padrão para `Lax` e adiciona uma nova entrada `None` a ser recusada. `Lax` é suficiente para a maioria dos cookies de aplicativo; no entanto, ele quebra cenários entre sites como o OpenID Connect e WS-Federation logon.</span><span class="sxs-lookup"><span data-stu-id="51d1c-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="51d1c-117">A maioria dos logons OAuth não é afetada devido a diferenças em como a solicitação flui.</span><span class="sxs-lookup"><span data-stu-id="51d1c-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="51d1c-118">O novo `None` parâmetro causa problemas de compatibilidade com clientes que implementaram o rascunho padrão anterior (por exemplo, IOS 12).</span><span class="sxs-lookup"><span data-stu-id="51d1c-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="51d1c-119">O Chrome 80 incluirá as alterações.</span><span class="sxs-lookup"><span data-stu-id="51d1c-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="51d1c-120">Consulte [atualizações do SameSite](https://www.chromium.org/updates/same-site) para a linha do tempo de lançamento do produto Chrome.</span><span class="sxs-lookup"><span data-stu-id="51d1c-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="51d1c-121">ASP.NET Core 3,1 foi atualizado para implementar o novo `SameSite` comportamento.</span><span class="sxs-lookup"><span data-stu-id="51d1c-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="51d1c-122">A atualização redefine o comportamento de `SameSiteMode.None` para emissão `SameSite=None` e adiciona um novo valor `SameSiteMode.Unspecified` para omitir o `SameSite` atributo.</span><span class="sxs-lookup"><span data-stu-id="51d1c-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="51d1c-123">Todas as APIs de cookie agora são padronizadas para `Unspecified` , embora alguns componentes que usam os cookies definam valores mais específicos para seus cenários, como a correlação do OpenID Connect e os cookies de nonce.</span><span class="sxs-lookup"><span data-stu-id="51d1c-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="51d1c-124">Para outras alterações recentes nessa área, consulte [http: alguns padrões de SameSite de cookie foram alterados para nenhum](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="51d1c-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="51d1c-125">No ASP.NET Core 3,0, a maioria dos padrões foi alterada de <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> para <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (mas ainda usando o padrão anterior).</span><span class="sxs-lookup"><span data-stu-id="51d1c-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="51d1c-126">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="51d1c-126">Reason for change</span></span>

<span data-ttu-id="51d1c-127">Alterações de navegador e especificação, conforme descrito no texto anterior.</span><span class="sxs-lookup"><span data-stu-id="51d1c-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="51d1c-128">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="51d1c-128">Recommended action</span></span>

<span data-ttu-id="51d1c-129">Os aplicativos que interagem com sites remotos, como por logon de terceiros, precisam:</span><span class="sxs-lookup"><span data-stu-id="51d1c-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="51d1c-130">Teste esses cenários em vários navegadores.</span><span class="sxs-lookup"><span data-stu-id="51d1c-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="51d1c-131">Aplique o navegador de política de cookie a mitigação de detecção discutida em [suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="51d1c-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="51d1c-132">Para testar e obter instruções de detecção de navegador, consulte a seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="51d1c-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="51d1c-133">Determine se você é afetado</span><span class="sxs-lookup"><span data-stu-id="51d1c-133">Determine if you're affected</span></span>

<span data-ttu-id="51d1c-134">Teste seu aplicativo Web usando uma versão do cliente que pode optar pelo novo comportamento.</span><span class="sxs-lookup"><span data-stu-id="51d1c-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="51d1c-135">O Chrome, o Firefox e o Microsoft Edge Chromium têm novos sinalizadores de recurso de aceitação que podem ser usados para teste.</span><span class="sxs-lookup"><span data-stu-id="51d1c-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="51d1c-136">Verifique se seu aplicativo é compatível com versões mais antigas do cliente depois de aplicar os patches, especialmente o Safari.</span><span class="sxs-lookup"><span data-stu-id="51d1c-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="51d1c-137">Para obter mais informações, consulte [suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="51d1c-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="51d1c-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="51d1c-138">Chrome</span></span>

<span data-ttu-id="51d1c-139">O Chrome 78 e posterior geram resultados de teste enganosos.</span><span class="sxs-lookup"><span data-stu-id="51d1c-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="51d1c-140">Essas versões têm uma mitigação temporária em vigor e permitem cookies com menos de dois minutos de idade.</span><span class="sxs-lookup"><span data-stu-id="51d1c-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="51d1c-141">Com os sinalizadores de teste apropriados habilitados, o Chrome 76 e o 77 geram resultados mais precisos.</span><span class="sxs-lookup"><span data-stu-id="51d1c-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="51d1c-142">Para testar o novo comportamento, alterne `chrome://flags/#same-site-by-default-cookies` para habilitado.</span><span class="sxs-lookup"><span data-stu-id="51d1c-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="51d1c-143">O Chrome 75 e versões anteriores são relatados para falha com a nova `None` configuração.</span><span class="sxs-lookup"><span data-stu-id="51d1c-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="51d1c-144">Para obter mais informações, consulte [suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="51d1c-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="51d1c-145">O Google não disponibiliza versões mais antigas do Chrome.</span><span class="sxs-lookup"><span data-stu-id="51d1c-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="51d1c-146">No entanto, você pode baixar versões mais antigas do Chromium, o que será suficiente para teste.</span><span class="sxs-lookup"><span data-stu-id="51d1c-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="51d1c-147">Siga as instruções em [baixar o Chromium](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="51d1c-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="51d1c-148">Chromium 76 Win64</span><span class="sxs-lookup"><span data-stu-id="51d1c-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="51d1c-149">Chromium 74 Win64</span><span class="sxs-lookup"><span data-stu-id="51d1c-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="51d1c-150">Safari</span><span class="sxs-lookup"><span data-stu-id="51d1c-150">Safari</span></span>

<span data-ttu-id="51d1c-151">O Safari 12 implementou estritamente o rascunho anterior e falha se ele vê o novo `None` valor em cookies.</span><span class="sxs-lookup"><span data-stu-id="51d1c-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="51d1c-152">Isso deve ser evitado por meio do código de detecção do navegador mostrado em [suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="51d1c-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="51d1c-153">Certifique-se de testar o Safari 12 e 13, bem como OS logons de estilo do sistema operacional baseados em WebKit usando a MSAL (biblioteca de autenticação da Microsoft), a ADAL (Biblioteca de Autenticação do Active Directory) ou qualquer biblioteca que você esteja usando.</span><span class="sxs-lookup"><span data-stu-id="51d1c-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="51d1c-154">O problema depende da versão subjacente do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="51d1c-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="51d1c-155">O OSX Mojave 10,14 e o iOS 12 são conhecidos por ter problemas de compatibilidade com o novo comportamento.</span><span class="sxs-lookup"><span data-stu-id="51d1c-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="51d1c-156">A atualização para OSX Catalina 10,15 ou iOS 13 corrige o problema.</span><span class="sxs-lookup"><span data-stu-id="51d1c-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="51d1c-157">No momento, o Safari não tem um sinalizador de aceitação para testar o novo comportamento de especificação.</span><span class="sxs-lookup"><span data-stu-id="51d1c-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="51d1c-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="51d1c-158">Firefox</span></span>

<span data-ttu-id="51d1c-159">O suporte do Firefox para o novo padrão pode ser testado na versão 68 e posterior, optando na `about:config` página pelo sinalizador de recurso `network.cookie.sameSite.laxByDefault` .</span><span class="sxs-lookup"><span data-stu-id="51d1c-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="51d1c-160">Nenhum problema de compatibilidade foi relatado em versões mais antigas do Firefox.</span><span class="sxs-lookup"><span data-stu-id="51d1c-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="51d1c-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="51d1c-161">Microsoft Edge</span></span>

<span data-ttu-id="51d1c-162">Embora o Microsoft Edge dê suporte ao antigo `SameSite` padrão, a partir da versão 44, não havia nenhum problema de compatibilidade com o novo padrão.</span><span class="sxs-lookup"><span data-stu-id="51d1c-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="51d1c-163">Chromium do Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="51d1c-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="51d1c-164">O sinalizador de recurso é `edge://flags/#same-site-by-default-cookies` .</span><span class="sxs-lookup"><span data-stu-id="51d1c-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="51d1c-165">Nenhum problema de compatibilidade foi observado durante o teste com o Microsoft Edge Chromium 78.</span><span class="sxs-lookup"><span data-stu-id="51d1c-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="51d1c-166">Digital</span><span class="sxs-lookup"><span data-stu-id="51d1c-166">Electron</span></span>

<span data-ttu-id="51d1c-167">As versões do at-SS são versões mais antigas do Chromium.</span><span class="sxs-lookup"><span data-stu-id="51d1c-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="51d1c-168">Por exemplo, a versão do at-SS de uso da Microsoft Teams é Chromium 66, que exibe o comportamento mais antigo.</span><span class="sxs-lookup"><span data-stu-id="51d1c-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="51d1c-169">Execute seus próprios testes de compatibilidade com a versão do uso de digital que seu produto usa.</span><span class="sxs-lookup"><span data-stu-id="51d1c-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="51d1c-170">Para obter mais informações, consulte [suporte a navegadores mais antigos](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="51d1c-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="51d1c-171">Suporte a navegadores mais antigos</span><span class="sxs-lookup"><span data-stu-id="51d1c-171">Support older browsers</span></span>

<span data-ttu-id="51d1c-172">O `SameSite` padrão 2016 obrigatório que valores desconhecidos sejam tratados como `SameSite=Strict` valores.</span><span class="sxs-lookup"><span data-stu-id="51d1c-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="51d1c-173">Consequentemente, todos os navegadores mais antigos que dão suporte ao padrão original podem ser interrompidos quando veem uma `SameSite` propriedade com um valor de `None` .</span><span class="sxs-lookup"><span data-stu-id="51d1c-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="51d1c-174">Os aplicativos Web devem implementar a detecção de navegador se pretenderem dar suporte a esses navegadores antigos.</span><span class="sxs-lookup"><span data-stu-id="51d1c-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="51d1c-175">ASP.NET Core não implementa a detecção de navegador para você porque `User-Agent` os valores de cabeçalho de solicitação são altamente instáveis e mudam semanalmente.</span><span class="sxs-lookup"><span data-stu-id="51d1c-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="51d1c-176">Em vez disso, um ponto de extensão na política de cookie permite que você adicione `User-Agent` lógica específica.</span><span class="sxs-lookup"><span data-stu-id="51d1c-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="51d1c-177">No *Startup.cs*, adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="51d1c-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None)
    {
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here.
        if (/* UserAgent doesn't support new behavior */)
        {
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services)
{
    services.Configure<CookiePolicyOptions>(options =>
    {
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    });
}

public void Configure(IApplicationBuilder app)
{
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication();
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="51d1c-178">Opções de recusa</span><span class="sxs-lookup"><span data-stu-id="51d1c-178">Opt-out switches</span></span>

<span data-ttu-id="51d1c-179">A `Microsoft.AspNetCore.SuppressSameSiteNone` opção de compatibilidade permite recusar temporariamente o novo comportamento de cookie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="51d1c-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="51d1c-180">Adicione o JSON a seguir a um *runtimeconfig.template.jsno* arquivo em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="51d1c-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="51d1c-181">Outras versões</span><span class="sxs-lookup"><span data-stu-id="51d1c-181">Other Versions</span></span>

<span data-ttu-id="51d1c-182">`SameSite`Patches relacionados estão prestes a:</span><span class="sxs-lookup"><span data-stu-id="51d1c-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="51d1c-183">ASP.NET Core 2,1, 2,2 e 3,0</span><span class="sxs-lookup"><span data-stu-id="51d1c-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="51d1c-184">`Microsoft.Owin` 4,1</span><span class="sxs-lookup"><span data-stu-id="51d1c-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="51d1c-185">`System.Web` (para .NET Framework 4.7.2 e posterior)</span><span class="sxs-lookup"><span data-stu-id="51d1c-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="51d1c-186">Categoria</span><span class="sxs-lookup"><span data-stu-id="51d1c-186">Category</span></span>

<span data-ttu-id="51d1c-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="51d1c-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="51d1c-188">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="51d1c-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
