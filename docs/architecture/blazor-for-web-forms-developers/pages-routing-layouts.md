---
title: Páginas, roteamento e layouts
description: Saiba como criar páginas no Blazor , trabalhar com o roteamento do lado do cliente e gerenciar layouts de página.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/19/2019
ms.openlocfilehash: fc1f6f9420c7149b6e67123f2f68bef75667aa0c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173101"
---
# <a name="pages-routing-and-layouts"></a><span data-ttu-id="80f3f-103">Páginas, roteamento e layouts</span><span class="sxs-lookup"><span data-stu-id="80f3f-103">Pages, routing, and layouts</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="80f3f-104">ASP.NET Web Forms aplicativos são compostos de páginas definidas em arquivos *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="80f3f-104">ASP.NET Web Forms apps are composed of pages defined in *.aspx* files.</span></span> <span data-ttu-id="80f3f-105">O endereço de cada página é baseado em seu caminho de arquivo físico no projeto.</span><span class="sxs-lookup"><span data-stu-id="80f3f-105">Each page's address is based on its physical file path in the project.</span></span> <span data-ttu-id="80f3f-106">Quando um navegador faz uma solicitação para a página, o conteúdo da página é processado dinamicamente no servidor.</span><span class="sxs-lookup"><span data-stu-id="80f3f-106">When a browser makes a request to the page, the contents of the page are dynamically rendered on the server.</span></span> <span data-ttu-id="80f3f-107">As contas de renderização para a marcação HTML da página e seus controles de servidor.</span><span class="sxs-lookup"><span data-stu-id="80f3f-107">The rendering accounts for both the page's HTML markup and its server controls.</span></span>

<span data-ttu-id="80f3f-108">No Blazor , cada página no aplicativo é um componente, normalmente definido em um arquivo *. Razor* , com uma ou mais rotas especificadas.</span><span class="sxs-lookup"><span data-stu-id="80f3f-108">In Blazor, each page in the app is a component, typically defined in a *.razor* file, with one or more specified routes.</span></span> <span data-ttu-id="80f3f-109">O roteamento ocorre principalmente no lado do cliente sem envolver uma solicitação de servidor específica.</span><span class="sxs-lookup"><span data-stu-id="80f3f-109">Routing mostly happens client-side without involving a specific server request.</span></span> <span data-ttu-id="80f3f-110">O navegador primeiro faz uma solicitação para o endereço raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80f3f-110">The browser first makes a request to the root address of the app.</span></span> <span data-ttu-id="80f3f-111">Um `Router` componente raiz no Blazor aplicativo, em seguida, lida com a interceptação de solicitações de navegação e com o componente correto.</span><span class="sxs-lookup"><span data-stu-id="80f3f-111">A root `Router` component in the Blazor app then handles intercepting navigation requests and them to the correct component.</span></span>

Blazor<span data-ttu-id="80f3f-112">também dá suporte à *vinculação profunda*.</span><span class="sxs-lookup"><span data-stu-id="80f3f-112"> also supports *deep linking*.</span></span> <span data-ttu-id="80f3f-113">A vinculação profunda ocorre quando o navegador faz uma solicitação para uma rota específica diferente da raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80f3f-113">Deep linking occurs when the browser makes a request to a specific route other than the root of the app.</span></span> <span data-ttu-id="80f3f-114">As solicitações de links profundos enviados ao servidor são roteadas para o Blazor aplicativo, que roteia a solicitação do lado do cliente para o componente correto.</span><span class="sxs-lookup"><span data-stu-id="80f3f-114">Requests for deep links sent to the server are routed to the Blazor app, which then routes the request client-side to the correct component.</span></span>

<span data-ttu-id="80f3f-115">Uma página simples no ASP.NET Web Forms pode conter a seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="80f3f-115">A simple page in ASP.NET Web Forms might contain the following markup:</span></span>

<span data-ttu-id="80f3f-116">*Name. aspx*</span><span class="sxs-lookup"><span data-stu-id="80f3f-116">*Name.aspx*</span></span>

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

<span data-ttu-id="80f3f-117">*Name.aspx.cs*</span><span class="sxs-lookup"><span data-stu-id="80f3f-117">*Name.aspx.cs*</span></span>

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

<span data-ttu-id="80f3f-118">A página equivalente em um Blazor aplicativo ficaria assim:</span><span class="sxs-lookup"><span data-stu-id="80f3f-118">The equivalent page in a Blazor app would look like this:</span></span>

<span data-ttu-id="80f3f-119">*Nome. Razor*</span><span class="sxs-lookup"><span data-stu-id="80f3f-119">*Name.razor*</span></span>

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a><span data-ttu-id="80f3f-120">Criar páginas</span><span class="sxs-lookup"><span data-stu-id="80f3f-120">Create pages</span></span>

<span data-ttu-id="80f3f-121">Para criar uma página no Blazor , crie um componente e adicione a `@page` diretiva Razor para especificar a rota para o componente.</span><span class="sxs-lookup"><span data-stu-id="80f3f-121">To create a page in Blazor, create a component and add the `@page` Razor directive to specify the route for the component.</span></span> <span data-ttu-id="80f3f-122">A `@page` diretiva usa um único parâmetro, que é o modelo de rota a ser adicionado a esse componente.</span><span class="sxs-lookup"><span data-stu-id="80f3f-122">The `@page` directive takes a single parameter, which is the route template to add to that component.</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="80f3f-123">O parâmetro de modelo de rota é necessário.</span><span class="sxs-lookup"><span data-stu-id="80f3f-123">The route template parameter is required.</span></span> <span data-ttu-id="80f3f-124">Ao contrário de ASP.NET Web Forms, a rota para um Blazor componente *não é* inferida de seu local de arquivo (embora isso possa ser um recurso adicionado no futuro).</span><span class="sxs-lookup"><span data-stu-id="80f3f-124">Unlike ASP.NET Web Forms, the route to a Blazor component *isn't* inferred from its file location (although that may be a feature added in the future).</span></span>

<span data-ttu-id="80f3f-125">A sintaxe do modelo de rota é a mesma sintaxe básica usada para roteamento no ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="80f3f-125">The route template syntax is the same basic syntax used for routing in ASP.NET Web Forms.</span></span> <span data-ttu-id="80f3f-126">Os parâmetros de rota são especificados no modelo usando chaves.</span><span class="sxs-lookup"><span data-stu-id="80f3f-126">Route parameters are specified in the template using braces.</span></span> Blazor<span data-ttu-id="80f3f-127">associará valores de rota a parâmetros de componente com o mesmo nome (não diferencia maiúsculas de minúsculas).</span><span class="sxs-lookup"><span data-stu-id="80f3f-127"> will bind route values to component parameters with the same name (case-insensitive).</span></span>

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

<span data-ttu-id="80f3f-128">Você também pode especificar restrições no valor do parâmetro de rota.</span><span class="sxs-lookup"><span data-stu-id="80f3f-128">You can also specify constraints on the value of the route parameter.</span></span> <span data-ttu-id="80f3f-129">Por exemplo, para restringir a ID do produto a `int` :</span><span class="sxs-lookup"><span data-stu-id="80f3f-129">For example, to constrain the product ID to be an `int`:</span></span>

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

<span data-ttu-id="80f3f-130">Para obter uma lista completa das restrições de rota com suporte pelo Blazor , consulte [restrições de rota](/aspnet/core/blazor/routing#route-constraints).</span><span class="sxs-lookup"><span data-stu-id="80f3f-130">For a full list of the route constraints supported by Blazor, see [Route constraints](/aspnet/core/blazor/routing#route-constraints).</span></span>

## <a name="router-component"></a><span data-ttu-id="80f3f-131">Componente do roteador</span><span class="sxs-lookup"><span data-stu-id="80f3f-131">Router component</span></span>

<span data-ttu-id="80f3f-132">O roteamento no Blazor é tratado pelo `Router` componente.</span><span class="sxs-lookup"><span data-stu-id="80f3f-132">Routing in Blazor is handled by the `Router` component.</span></span> <span data-ttu-id="80f3f-133">O `Router` componente é normalmente usado no componente raiz do aplicativo (*app. Razor*).</span><span class="sxs-lookup"><span data-stu-id="80f3f-133">The `Router` component is typically used in the app's root component (*App.razor*).</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

<span data-ttu-id="80f3f-134">O `Router` componente descobre os componentes roteáveis no especificado `AppAssembly` e na opção especificada `AdditionalAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="80f3f-134">The `Router` component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`.</span></span> <span data-ttu-id="80f3f-135">Quando o navegador navega, o `Router` intercepta a navegação e renderiza o conteúdo de seu `Found` parâmetro com o extraído `RouteData` se uma rota corresponde ao endereço, caso contrário, o `Router` renderiza seu `NotFound` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="80f3f-135">When the browser navigates, the `Router` intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the `Router` renders its `NotFound` parameter.</span></span>

<span data-ttu-id="80f3f-136">O `RouteView` componente lida com a renderização do componente correspondente especificado pelo `RouteData` com seu layout, se ele tiver um.</span><span class="sxs-lookup"><span data-stu-id="80f3f-136">The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one.</span></span> <span data-ttu-id="80f3f-137">Se o componente correspondente não tiver um layout, a opção opcionalmente especificada `DefaultLayout` será usada.</span><span class="sxs-lookup"><span data-stu-id="80f3f-137">If the matched component doesn't have a layout, then the optionally specified `DefaultLayout` is used.</span></span>

<span data-ttu-id="80f3f-138">O `LayoutView` componente renderiza seu conteúdo filho dentro do layout especificado.</span><span class="sxs-lookup"><span data-stu-id="80f3f-138">The `LayoutView` component renders its child content within the specified layout.</span></span> <span data-ttu-id="80f3f-139">Veremos os layouts mais detalhadamente mais adiante neste capítulo.</span><span class="sxs-lookup"><span data-stu-id="80f3f-139">We'll look at layouts more in detail later in this chapter.</span></span>

## <a name="navigation"></a><span data-ttu-id="80f3f-140">Navegação</span><span class="sxs-lookup"><span data-stu-id="80f3f-140">Navigation</span></span>

<span data-ttu-id="80f3f-141">No ASP.NET Web Forms, você dispara a navegação para uma página diferente retornando uma resposta de redirecionamento para o navegador.</span><span class="sxs-lookup"><span data-stu-id="80f3f-141">In ASP.NET Web Forms, you trigger navigation to a different page by returning a redirect response to the browser.</span></span> <span data-ttu-id="80f3f-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="80f3f-142">For example:</span></span>

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

<span data-ttu-id="80f3f-143">O retorno de uma resposta de redirecionamento geralmente não é possível no Blazor .</span><span class="sxs-lookup"><span data-stu-id="80f3f-143">Returning a redirect response isn't typically possible in Blazor.</span></span> Blazor<span data-ttu-id="80f3f-144">Não usa um modelo de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="80f3f-144"> doesn't use a request-reply model.</span></span> <span data-ttu-id="80f3f-145">No entanto, é possível disparar navegações do navegador diretamente, como você pode com o JavaScript.</span><span class="sxs-lookup"><span data-stu-id="80f3f-145">You can, however, trigger browser navigations directly, as you can with JavaScript.</span></span>

Blazor<span data-ttu-id="80f3f-146">fornece um `NavigationManager` serviço que pode ser usado para:</span><span class="sxs-lookup"><span data-stu-id="80f3f-146"> provides a `NavigationManager` service that can be used to:</span></span>

- <span data-ttu-id="80f3f-147">Obter o endereço do navegador atual</span><span class="sxs-lookup"><span data-stu-id="80f3f-147">Get the current browser address</span></span>
- <span data-ttu-id="80f3f-148">Obter o endereço base</span><span class="sxs-lookup"><span data-stu-id="80f3f-148">Get the base address</span></span>
- <span data-ttu-id="80f3f-149">Disparar navegações</span><span class="sxs-lookup"><span data-stu-id="80f3f-149">Trigger navigations</span></span>
- <span data-ttu-id="80f3f-150">Seja notificado quando o endereço for alterado</span><span class="sxs-lookup"><span data-stu-id="80f3f-150">Get notified when the address changes</span></span>

<span data-ttu-id="80f3f-151">Para navegar para um endereço diferente, use o `NavigateTo` método:</span><span class="sxs-lookup"><span data-stu-id="80f3f-151">To navigate to a different address, use the `NavigateTo` method:</span></span>

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

<span data-ttu-id="80f3f-152">Para obter uma descrição de todos os `NavigationManager` Membros, consulte [URI e auxiliares de estado de navegação](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span><span class="sxs-lookup"><span data-stu-id="80f3f-152">For a description of all `NavigationManager` members, see [URI and navigation state helpers](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span></span>

## <a name="base-urls"></a><span data-ttu-id="80f3f-153">URLs base</span><span class="sxs-lookup"><span data-stu-id="80f3f-153">Base URLs</span></span>

<span data-ttu-id="80f3f-154">Se seu Blazor aplicativo for implantado em um caminho base, você precisará especificar a URL base nos metadados da página usando a `<base>` marca para roteamento para a propriedade de trabalho.</span><span class="sxs-lookup"><span data-stu-id="80f3f-154">If your Blazor app is deployed under a base path, then you need to specify the base URL in the page metadata using the `<base>` tag for routing to work property.</span></span> <span data-ttu-id="80f3f-155">Se a página host do aplicativo for renderizada pelo servidor usando o Razor, você poderá usar a `~/` sintaxe para especificar o endereço base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80f3f-155">If the host page for the app is server-rendered using Razor, then you can use the `~/` syntax to specify the app's base address.</span></span> <span data-ttu-id="80f3f-156">Se a página host for HTML estático, você precisará especificar a URL base explicitamente.</span><span class="sxs-lookup"><span data-stu-id="80f3f-156">If the host page is static HTML, then you need to specify the base URL explicitly.</span></span>

```html
<base href="~/" />
```

## <a name="page-layout"></a><span data-ttu-id="80f3f-157">Layout de página</span><span class="sxs-lookup"><span data-stu-id="80f3f-157">Page layout</span></span>

<span data-ttu-id="80f3f-158">O layout de página no ASP.NET Web Forms é manipulado por páginas mestras.</span><span class="sxs-lookup"><span data-stu-id="80f3f-158">Page layout in ASP.NET Web Forms is handled by Master Pages.</span></span> <span data-ttu-id="80f3f-159">As páginas mestras definem um modelo com um ou mais espaços reservados de conteúdo que podem ser fornecidos por páginas individuais.</span><span class="sxs-lookup"><span data-stu-id="80f3f-159">Master Pages define a template with one or more content placeholders that can then be supplied by individual pages.</span></span> <span data-ttu-id="80f3f-160">As páginas mestras são definidas em arquivos *. Master* e começam com a `<%@ Master %>` diretiva.</span><span class="sxs-lookup"><span data-stu-id="80f3f-160">Master Pages are defined in *.master* files and start with the `<%@ Master %>` directive.</span></span> <span data-ttu-id="80f3f-161">O conteúdo dos arquivos *. Master* é codificado como você faria com uma página *. aspx* , mas com a adição de `<asp:ContentPlaceHolder>` controles para marcar onde as páginas podem fornecer conteúdo.</span><span class="sxs-lookup"><span data-stu-id="80f3f-161">The content of the *.master* files is coded as you would an *.aspx* page, but with the addition of `<asp:ContentPlaceHolder>` controls to mark where pages can supply content.</span></span>

<span data-ttu-id="80f3f-162">*Site.master*</span><span class="sxs-lookup"><span data-stu-id="80f3f-162">*Site.master*</span></span>

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

<span data-ttu-id="80f3f-163">No Blazor , você lida com o layout da página usando componentes de layout.</span><span class="sxs-lookup"><span data-stu-id="80f3f-163">In Blazor, you handle page layout using layout components.</span></span> <span data-ttu-id="80f3f-164">Os componentes de layout herdam de `LayoutComponentBase` , que define uma única `Body` Propriedade do tipo `RenderFragment` , que pode ser usada para renderizar o conteúdo da página.</span><span class="sxs-lookup"><span data-stu-id="80f3f-164">Layout components inherit from `LayoutComponentBase`, which defines a single `Body` property of type `RenderFragment`, which can be used to render the contents of the page.</span></span>

<span data-ttu-id="80f3f-165">*MainLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="80f3f-165">*MainLayout.razor*</span></span>

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

<span data-ttu-id="80f3f-166">Quando a página com um layout é renderizada, a página é renderizada dentro do conteúdo do layout especificado no local em que o layout renderiza sua `Body` propriedade.</span><span class="sxs-lookup"><span data-stu-id="80f3f-166">When the page with a layout is rendered, the page is rendered within the contents of the specified layout at the location where the layout renders its `Body` property.</span></span>

<span data-ttu-id="80f3f-167">Para aplicar um layout a uma página, use a `@layout` diretiva:</span><span class="sxs-lookup"><span data-stu-id="80f3f-167">To apply a layout to a page, use the `@layout` directive:</span></span>

```razor
@layout MainLayout
```

<span data-ttu-id="80f3f-168">Você pode especificar o layout de todos os componentes em uma pasta e subpastas usando um arquivo *_Imports. Razor* .</span><span class="sxs-lookup"><span data-stu-id="80f3f-168">You can specify the layout for all components in a folder and subfolders using an *_Imports.razor* file.</span></span> <span data-ttu-id="80f3f-169">Você também pode especificar um layout padrão para todas as suas páginas usando o [componente do roteador](#router-component).</span><span class="sxs-lookup"><span data-stu-id="80f3f-169">You can also specify a default layout for all your pages using the [Router component](#router-component).</span></span>

<span data-ttu-id="80f3f-170">As páginas mestras podem definir vários espaços reservados de conteúdo, mas os layouts Blazor têm apenas uma única `Body` propriedade.</span><span class="sxs-lookup"><span data-stu-id="80f3f-170">Master Pages can define multiple content placeholders, but layouts in Blazor only have a single `Body` property.</span></span> <span data-ttu-id="80f3f-171">Essa limitação dos Blazor componentes de layout, felizmente, será abordada em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="80f3f-171">This limitation of Blazor layout components will hopefully be addressed in a future release.</span></span>

<span data-ttu-id="80f3f-172">As páginas mestras no ASP.NET Web Forms podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="80f3f-172">Master Pages in ASP.NET Web Forms can be nested.</span></span> <span data-ttu-id="80f3f-173">Ou seja, uma página mestra também pode usar uma página mestra.</span><span class="sxs-lookup"><span data-stu-id="80f3f-173">That is, a Master Page may also use a Master Page.</span></span> <span data-ttu-id="80f3f-174">Os componentes de layout no Blazor também podem estar aninhados.</span><span class="sxs-lookup"><span data-stu-id="80f3f-174">Layout components in Blazor may be nested too.</span></span> <span data-ttu-id="80f3f-175">Você pode aplicar um componente de layout a um componente de layout.</span><span class="sxs-lookup"><span data-stu-id="80f3f-175">You can apply a layout component to a layout component.</span></span> <span data-ttu-id="80f3f-176">O conteúdo do layout interno será renderizado dentro do layout externo.</span><span class="sxs-lookup"><span data-stu-id="80f3f-176">The contents of the inner layout will be rendered within the outer layout.</span></span>

<span data-ttu-id="80f3f-177">*ChildLayout. Razor*</span><span class="sxs-lookup"><span data-stu-id="80f3f-177">*ChildLayout.razor*</span></span>

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

<span data-ttu-id="80f3f-178">*Index. Razor*</span><span class="sxs-lookup"><span data-stu-id="80f3f-178">*Index.razor*</span></span>

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

<span data-ttu-id="80f3f-179">A saída renderizada para a página seria:</span><span class="sxs-lookup"><span data-stu-id="80f3f-179">The rendered output for the page would then be:</span></span>

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

<span data-ttu-id="80f3f-180">Os layouts no Blazor não definem normalmente os elementos HTML raiz de uma página ( `<html>` ,, `<body>` `<head>` e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="80f3f-180">Layouts in Blazor don't typically define the root HTML elements for a page (`<html>`, `<body>`, `<head>`, and so on).</span></span> <span data-ttu-id="80f3f-181">Os elementos HTML raiz são definidos na Blazor página host de um aplicativo, que é usada para renderizar o conteúdo HTML inicial para o aplicativo (consulte [Bootstrap Blazor ](project-structure.md#bootstrap-blazor)).</span><span class="sxs-lookup"><span data-stu-id="80f3f-181">The root HTML elements are instead defined in a Blazor app's host page, which is used to render the initial HTML content for the app (see [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span></span> <span data-ttu-id="80f3f-182">A página host pode renderizar vários componentes raiz para o aplicativo com marcação ao redor.</span><span class="sxs-lookup"><span data-stu-id="80f3f-182">The host page can render multiple root components for the app with surrounding markup.</span></span>

<span data-ttu-id="80f3f-183">Os componentes no Blazor , incluindo páginas, não podem renderizar `<script>` marcas.</span><span class="sxs-lookup"><span data-stu-id="80f3f-183">Components in Blazor, including pages, can't render `<script>` tags.</span></span> <span data-ttu-id="80f3f-184">Essa restrição de renderização existe porque as `<script>` marcas são carregadas uma vez e não podem ser alteradas.</span><span class="sxs-lookup"><span data-stu-id="80f3f-184">This rendering restriction exists because `<script>` tags get loaded once and then can't be changed.</span></span> <span data-ttu-id="80f3f-185">Pode ocorrer um comportamento inesperado se você tentar renderizar as marcas dinamicamente usando sintaxe Razor.</span><span class="sxs-lookup"><span data-stu-id="80f3f-185">Unexpected behavior may occur if you try to render the tags dynamically using Razor syntax.</span></span> <span data-ttu-id="80f3f-186">Em vez disso, todas as `<script>` marcas devem ser adicionadas à página host do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80f3f-186">Instead, all `<script>` tags should be added to the app's host page.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="80f3f-187">[Anterior](components.md) 
> [Avançar](state-management.md)</span><span class="sxs-lookup"><span data-stu-id="80f3f-187">[Previous](components.md)
[Next](state-management.md)</span></span>
