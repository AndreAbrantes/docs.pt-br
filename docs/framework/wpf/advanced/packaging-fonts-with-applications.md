---
title: Empacotando fontes com aplicativos
description: Saiba como empacotar fontes com um aplicativo Windows Presentation Foundation, incluindo a adição de fontes como conteúdo e itens de recursos e limites de uso de fontes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: 725f05c22eda199d86e5ec5dbb6bdd899ee66a5d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166353"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="28505-103">Empacotando fontes com aplicativos</span><span class="sxs-lookup"><span data-stu-id="28505-103">Packaging Fonts with Applications</span></span>
<span data-ttu-id="28505-104">Este tópico fornece uma visão geral de como empacotar fontes com seu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-104">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28505-105">Assim como a maioria dos tipos de software, as fontes são licenciadas, ao invés de vendidas.</span><span class="sxs-lookup"><span data-stu-id="28505-105">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="28505-106">As licenças que regem o uso de fontes variam de fornecedor para fornecedor, mas, em geral, a maioria das licenças, incluindo aquelas que abrangem as fontes fornecidas pela Microsoft com aplicativos e janelas, não permitem que as fontes sejam inseridas em aplicativos ou redistribuídas de outra forma.</span><span class="sxs-lookup"><span data-stu-id="28505-106">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="28505-107">Portanto, como desenvolvedor, é sua responsabilidade assegurar que você tenha os direitos de licença necessários de qualquer fonte que você inserir em um aplicativo ou redistribuir.</span><span class="sxs-lookup"><span data-stu-id="28505-107">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="28505-108">Introdução a empacotamento de fontes</span><span class="sxs-lookup"><span data-stu-id="28505-108">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="28505-109">Você pode empacotar facilmente as fontes como recursos em seus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos para exibir o texto da interface do usuário e outros tipos de conteúdo baseado em texto.</span><span class="sxs-lookup"><span data-stu-id="28505-109">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="28505-110">As fontes podem ser separadas ou inseridas nos arquivos de assembly do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-110">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="28505-111">Você também pode criar uma biblioteca de fontes somente recursos, que seu aplicativo pode fazer referência.</span><span class="sxs-lookup"><span data-stu-id="28505-111">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="28505-112">As fontes de® OpenType e TrueType contêm um sinalizador de tipo, fsType, que indica os direitos de licenciamento de incorporação de fontes para a fonte.</span><span class="sxs-lookup"><span data-stu-id="28505-112">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="28505-113">No entanto, esse sinalizador de tipo somente referencia fontes embutidas armazenadas em um documento. Ele não referencia fontes incorporadas em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-113">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="28505-114">Você pode recuperar os direitos de incorporação de fontes para uma fonte criando um <xref:System.Windows.Media.GlyphTypeface> objeto e referenciando sua <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="28505-114">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="28505-115">Consulte a seção "sistema operacional/2 e métricas do Windows" da [especificação OpenType](https://www.microsoft.com/typography/otspec/os2.htm) para obter mais informações sobre o sinalizador fsType.</span><span class="sxs-lookup"><span data-stu-id="28505-115">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="28505-116">O site da [Microsoft Typography](https://docs.microsoft.com/typography/) inclui informações de contato que podem ajudá-lo a localizar um fornecedor de fontes específico ou encontrar um fornecedor de fontes para trabalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="28505-116">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="28505-117">Adicionando fontes como itens de conteúdo</span><span class="sxs-lookup"><span data-stu-id="28505-117">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="28505-118">Você pode adicionar fontes ao seu aplicativo como itens de conteúdo de projeto que são separados dos arquivos de assembly do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-118">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="28505-119">Isso significa que os itens de conteúdo não são inseridos como recursos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="28505-119">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="28505-120">O seguinte exemplo de arquivo de projeto mostra como definir itens de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="28505-120">The following project file example shows how to define content items.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 <span data-ttu-id="28505-121">Para garantir que o aplicativo possa usar as fontes em tempo de execução, as fontes devem ser acessíveis no diretório de implantação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-121">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="28505-122">O `<CopyToOutputDirectory>` elemento no arquivo de projeto do aplicativo permite que você copie automaticamente as fontes para o diretório de implantação do aplicativo durante o processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="28505-122">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="28505-123">O seguinte exemplo de arquivo de projeto mostra como copiar fontes para o diretório de implantação.</span><span class="sxs-lookup"><span data-stu-id="28505-123">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 <span data-ttu-id="28505-124">O exemplo de código a seguir mostra como referenciar a fonte do aplicativo como um item de conteúdo. O item de conteúdo referenciado deve estar no mesmo diretório que os arquivos de assembly do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-124">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="28505-125">Adicionando fontes como itens de recurso</span><span class="sxs-lookup"><span data-stu-id="28505-125">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="28505-126">Você pode adicionar fontes ao seu aplicativo como itens de recurso de projeto que são inseridos nos arquivos de assembly do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-126">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="28505-127">Usar um subdiretório separado para recursos ajuda a organizar arquivos de projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-127">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="28505-128">O seguinte exemplo de arquivo de projeto mostra como definir fontes como itens de recursos em um subdiretório separado.</span><span class="sxs-lookup"><span data-stu-id="28505-128">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="28505-129">Ao adicionar fontes como recursos ao seu aplicativo, verifique se você está definindo o `<Resource>` elemento e não o `<EmbeddedResource>` elemento no arquivo de projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-129">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="28505-130">`<EmbeddedResource>`Não há suporte para o elemento da ação de compilação.</span><span class="sxs-lookup"><span data-stu-id="28505-130">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="28505-131">O exemplo de marcação a seguir mostra como referenciar os recursos de fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-131">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="28505-132">Referenciando itens de recurso de fonte do código</span><span class="sxs-lookup"><span data-stu-id="28505-132">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="28505-133">Para referenciar itens de recurso de fonte do código, você deve fornecer uma referência de recurso de fonte de duas partes: o URI (Uniform Resource Identifier) base. e a referência do local da fonte.</span><span class="sxs-lookup"><span data-stu-id="28505-133">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="28505-134">Esses valores são usados como os parâmetros para o <xref:System.Windows.Media.FontFamily.%23ctor%2A> método.</span><span class="sxs-lookup"><span data-stu-id="28505-134">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="28505-135">O exemplo de código a seguir mostra como referenciar os recursos de fonte do aplicativo no subdiretório do projeto chamado `resources` .</span><span class="sxs-lookup"><span data-stu-id="28505-135">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="28505-136">O URI (Uniform Resource Identifier) base pode incluir o subdiretório do aplicativo onde reside o recurso de fonte.</span><span class="sxs-lookup"><span data-stu-id="28505-136">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="28505-137">Nesse caso, a referência de local de fonte não precisaria especificar um diretório, mas teria que incluir um "" à esquerda `./` , que indica que o recurso de fonte está no mesmo diretório especificado pelo URI (Uniform Resource Identifier) base.</span><span class="sxs-lookup"><span data-stu-id="28505-137">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="28505-138">O exemplo de código a seguir mostra uma maneira alternativa de referenciar o item de recurso de fonte. Ele é equivalente ao exemplo de código anterior.</span><span class="sxs-lookup"><span data-stu-id="28505-138">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="28505-139">Referenciando fontes do mesmo subdiretório do aplicativo</span><span class="sxs-lookup"><span data-stu-id="28505-139">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="28505-140">Você pode colocar ambos os arquivos de conteúdo e recursos de aplicativo dentro do mesmo subdiretório definido pelo usuário do seu projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-140">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="28505-141">O seguinte exemplo de arquivo de projeto mostra uma página de conteúdo e recursos de fonte definidos no mesmo subdiretório.</span><span class="sxs-lookup"><span data-stu-id="28505-141">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="28505-142">Como o conteúdo do aplicativo e a fonte estão no mesmo subdiretório, a referência da fonte é relativa ao conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-142">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="28505-143">Os exemplos a seguir mostram como referenciar o recurso de fonte do aplicativo quando a fonte está no mesmo diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-143">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="28505-144">Enumerando fontes em um aplicativo</span><span class="sxs-lookup"><span data-stu-id="28505-144">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="28505-145">Para enumerar fontes como itens de recurso em seu aplicativo, use <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> o <xref:System.Windows.Media.Fonts.GetTypefaces%2A> método ou.</span><span class="sxs-lookup"><span data-stu-id="28505-145">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="28505-146">O exemplo a seguir mostra como usar o <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> método para retornar a coleção de <xref:System.Windows.Media.FontFamily> objetos do local da fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-146">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="28505-147">Nesse caso, o aplicativo contém um subdiretório chamado "recursos".</span><span class="sxs-lookup"><span data-stu-id="28505-147">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="28505-148">O exemplo a seguir mostra como usar o <xref:System.Windows.Media.Fonts.GetTypefaces%2A> método para retornar a coleção de <xref:System.Windows.Media.Typeface> objetos do local da fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-148">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="28505-149">Nesse caso, o aplicativo contém um subdiretório chamado "recursos".</span><span class="sxs-lookup"><span data-stu-id="28505-149">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="28505-150">Criando uma biblioteca de recursos de fonte</span><span class="sxs-lookup"><span data-stu-id="28505-150">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="28505-151">Você pode criar uma biblioteca somente recursos que contém apenas fontes. Nenhum código faz parte desse tipo de projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="28505-151">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="28505-152">Criar uma biblioteca somente recursos é uma técnica comum para desacoplar recursos do código do aplicativo que os utiliza.</span><span class="sxs-lookup"><span data-stu-id="28505-152">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="28505-153">Isso também permite que o assembly de biblioteca seja incluído em vários projetos de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-153">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="28505-154">O seguinte exemplo de arquivo de projeto mostra as partes principais de um projeto de biblioteca somente recursos.</span><span class="sxs-lookup"><span data-stu-id="28505-154">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="28505-155">Referenciando uma fonte em uma biblioteca de recursos</span><span class="sxs-lookup"><span data-stu-id="28505-155">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="28505-156">Para referenciar uma fonte em uma biblioteca de recursos de seu aplicativo, você deve prefixar a referência da fonte com o nome do assembly de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="28505-156">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="28505-157">Nesse caso, o assembly de recursos de fonte é "FontLibrary".</span><span class="sxs-lookup"><span data-stu-id="28505-157">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="28505-158">Para separar o nome do assembly de referência dentro do assembly, use um caractere ';'.</span><span class="sxs-lookup"><span data-stu-id="28505-158">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="28505-159">Adicionar a palavra-chave "Component" seguida da referência ao nome da fonte completa a referência completa ao recurso da biblioteca de fontes.</span><span class="sxs-lookup"><span data-stu-id="28505-159">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="28505-160">O exemplo de código a seguir mostra como referenciar uma fonte em um assembly de biblioteca de recursos.</span><span class="sxs-lookup"><span data-stu-id="28505-160">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="28505-161">Este SDK contém um conjunto de fontes OpenType de exemplo que você pode usar com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="28505-161">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="28505-162">As fontes são definidas em uma biblioteca somente recursos.</span><span class="sxs-lookup"><span data-stu-id="28505-162">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="28505-163">Para obter mais informações, consulte [pacote de fontes OpenType de exemplo](sample-opentype-font-pack.md).</span><span class="sxs-lookup"><span data-stu-id="28505-163">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="28505-164">Limitações no uso de fontes</span><span class="sxs-lookup"><span data-stu-id="28505-164">Limitations on Font Usage</span></span>  
 <span data-ttu-id="28505-165">A lista a seguir descreve várias limitações sobre o empacotamento e o uso de fontes em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos:</span><span class="sxs-lookup"><span data-stu-id="28505-165">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="28505-166">**Bits de permissão de incorporação de fontes:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os aplicativos não verificam ou impõem bits de permissão de incorporação de fonte.</span><span class="sxs-lookup"><span data-stu-id="28505-166">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="28505-167">Consulte a seção [Introduction_to_Packing fontes](#introduction_to_packaging_fonts) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="28505-167">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="28505-168">**Local das fontes de origem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os aplicativos não permitem uma referência de fonte a um URI (Uniform Resource Identifier) http ou FTP.</span><span class="sxs-lookup"><span data-stu-id="28505-168">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="28505-169">**URI absoluto usando a notação** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de pacote: os aplicativos não permitem que você crie um <xref:System.Windows.Media.FontFamily> objeto programaticamente usando "Pack:" como parte da referência absoluta do URI (Uniform Resource Identifier) para uma fonte.</span><span class="sxs-lookup"><span data-stu-id="28505-169">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="28505-170">Por exemplo, `"pack://application:,,,/resources/#Pericles Light"` é uma referência de fonte inválida.</span><span class="sxs-lookup"><span data-stu-id="28505-170">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="28505-171">**Incorporação de fonte automática:** no tempo de design, não há suporte para pesquisar o uso de um aplicativo de fontes e incorporar automaticamente as fontes nos recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28505-171">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="28505-172">**Subconjuntos de fontes:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os aplicativos não dão suporte à criação de subconjuntos de fontes para documentos não fixos.</span><span class="sxs-lookup"><span data-stu-id="28505-172">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="28505-173">Em casos em que há uma referência incorreta, o aplicativo volta a usar uma fonte disponível.</span><span class="sxs-lookup"><span data-stu-id="28505-173">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28505-174">Confira também</span><span class="sxs-lookup"><span data-stu-id="28505-174">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="28505-175">Microsoft Typography: links, notícias e contatos</span><span class="sxs-lookup"><span data-stu-id="28505-175">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="28505-176">Especificação OpenType</span><span class="sxs-lookup"><span data-stu-id="28505-176">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="28505-177">Recursos de fonte OpenType</span><span class="sxs-lookup"><span data-stu-id="28505-177">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="28505-178">Pacote de fontes OpenType de amostra</span><span class="sxs-lookup"><span data-stu-id="28505-178">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
