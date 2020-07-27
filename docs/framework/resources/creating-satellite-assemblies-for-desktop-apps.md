---
title: Criando assemblies satélite para aplicativos de área de trabalho
description: Introdução à criação de assemblies satélite para aplicativos da área de trabalho. Um assembly satélite pode ser facilmente atualizado ou substituído para fornecer recursos localizados.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
ms.openlocfilehash: be6603f3a593d9756d55204024214660b2220af3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166216"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="23885-104">Criando assemblies satélite para aplicativos de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="23885-104">Creating Satellite Assemblies for Desktop Apps</span></span>

<span data-ttu-id="23885-105">Arquivos de recurso desempenham um papel central em aplicativos localizados.</span><span class="sxs-lookup"><span data-stu-id="23885-105">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="23885-106">Eles permitem que um aplicativo exiba cadeias de caracteres, imagens e outros dados no idioma e na cultura do usuário e forneça dados alternativos se esses recursos não estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="23885-106">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="23885-107">O .NET Framework usa um modelo de hub e spoke para localizar e recuperar os recursos localizados.</span><span class="sxs-lookup"><span data-stu-id="23885-107">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="23885-108">O hub é o principal assembly que contém o código executável não localizável e os recursos para uma única cultura, que é chamada de cultura neutra ou padrão.</span><span class="sxs-lookup"><span data-stu-id="23885-108">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="23885-109">O padrão é a cultura de fallback para o aplicativo; ela é usada quando não há recursos localizados disponíveis.</span><span class="sxs-lookup"><span data-stu-id="23885-109">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="23885-110">Você usa o atributo <xref:System.Resources.NeutralResourcesLanguageAttribute> para designar a cultura da cultura padrão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23885-110">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="23885-111">Cada spoke conecta-se a um assembly satélite que contém os recursos para uma única cultura localizada, mas não contém nenhum código.</span><span class="sxs-lookup"><span data-stu-id="23885-111">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="23885-112">Como os assemblies satélite não fazem parte do assembly principal, você pode facilmente atualizar ou substituir recursos que correspondem a uma cultura específica sem substituir o assembly principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23885-112">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>

> [!NOTE]
> <span data-ttu-id="23885-113">Os recursos da cultura padrão de um aplicativo também podem ser armazenados em um assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="23885-113">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="23885-114">Para fazer isso, você atribui ao atributo <xref:System.Resources.NeutralResourcesLanguageAttribute> um valor de <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="23885-114">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span></span>

## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="23885-115">Nome e local do assembly satélite</span><span class="sxs-lookup"><span data-stu-id="23885-115">Satellite Assembly Name and Location</span></span>

<span data-ttu-id="23885-116">Esse modelo hub e spoke requer que você coloque recursos em locais específicos, para que possam ser facilmente localizados e usados.</span><span class="sxs-lookup"><span data-stu-id="23885-116">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="23885-117">Se você não compilar e nomear os recursos conforme esperado, ou se não colocá-los nos locais corretos, o CLR não poderá localizá-los e usará os recursos da cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="23885-117">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="23885-118">O Gerenciador de Recursos do .NET Framework, representado por um objeto <xref:System.Resources.ResourceManager>, é usado para acessar automaticamente os recursos localizados.</span><span class="sxs-lookup"><span data-stu-id="23885-118">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="23885-119">O Gerenciador de Recursos requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="23885-119">The Resource Manager requires the following:</span></span>

- <span data-ttu-id="23885-120">Um assembly satélite único deve incluir todos os recursos de uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="23885-120">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="23885-121">Em outras palavras, você deve compilar vários arquivos *. txt* ou *. resx* em um único arquivo binário *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="23885-121">In other words, you should compile multiple *.txt* or *.resx* files into a single binary *.resources* file.</span></span>

- <span data-ttu-id="23885-122">Deve haver um subdiretório separado no diretório do aplicativo para cada cultura localizada que armazena os recursos da cultura.</span><span class="sxs-lookup"><span data-stu-id="23885-122">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="23885-123">O nome do subdiretório deve ser igual ao nome de cultura.</span><span class="sxs-lookup"><span data-stu-id="23885-123">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="23885-124">Como alternativa, você pode armazenar seus assemblies satélites no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="23885-124">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="23885-125">Nesse caso, o componente de informações de cultura do nome forte do assembly deve indicar sua cultura.</span><span class="sxs-lookup"><span data-stu-id="23885-125">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="23885-126">(Consulte a seção [Instalação dos assemblies de satélite no cache de assembly global](#SN), mais adiante neste tópico.)</span><span class="sxs-lookup"><span data-stu-id="23885-126">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>

  > [!NOTE]
  > <span data-ttu-id="23885-127">Se o aplicativo incluir recursos para subculturas, coloque cada subcultura em um subdiretório separado no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23885-127">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="23885-128">Não coloque subculturas em subdiretórios no diretório principal da sua cultura.</span><span class="sxs-lookup"><span data-stu-id="23885-128">Do not place subcultures in subdirectories under their main culture's directory.</span></span>

- <span data-ttu-id="23885-129">O assembly satélite deve ter o mesmo nome que o aplicativo e usar a extensão de nome de arquivo ".resources.dll".</span><span class="sxs-lookup"><span data-stu-id="23885-129">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="23885-130">Por exemplo, se um aplicativo for nomeado *Example.exe*, o nome de cada assembly satélite deverá ser *Example.resources.dll*.</span><span class="sxs-lookup"><span data-stu-id="23885-130">For example, if an application is named *Example.exe*, the name of each satellite assembly should be *Example.resources.dll*.</span></span> <span data-ttu-id="23885-131">Observe que o nome do assembly satélite não indica a cultura dos seus arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="23885-131">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="23885-132">No entanto, o assembly satélite aparece em um diretório que especifica a cultura.</span><span class="sxs-lookup"><span data-stu-id="23885-132">However, the satellite assembly appears in a directory that does specify the culture.</span></span>

- <span data-ttu-id="23885-133">Informações sobre a cultura do assembly satélite devem ser incluídas nos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="23885-133">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="23885-134">Para armazenar o nome da cultura nos metadados do assembly satélite, você deve especificar a opção `/culture` quando usar o [Assembly Linker](../tools/al-exe-assembly-linker.md) para incorporar recursos no assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="23885-134">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>

<span data-ttu-id="23885-135">A ilustração a seguir mostra a estrutura e os requisitos de localização de um diretório de exemplo para os aplicativos que você não está instalando no [cache de assembly global](../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="23885-135">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../app-domains/gac.md).</span></span> <span data-ttu-id="23885-136">Os itens com as extensões .txt e .resources não serão fornecidos com o aplicativo final.</span><span class="sxs-lookup"><span data-stu-id="23885-136">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="23885-137">Esses são os arquivos de recurso intermediários usados para criar os assemblies satélite finais de recursos.</span><span class="sxs-lookup"><span data-stu-id="23885-137">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="23885-138">Neste exemplo, você poderia substituir arquivos .resx por arquivos .txt.</span><span class="sxs-lookup"><span data-stu-id="23885-138">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="23885-139">Para obter mais informações, consulte [Empacotamento e implantação de recursos](packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="23885-139">For more information, see [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

<span data-ttu-id="23885-140">A imagem a seguir mostra o diretório do assembly satélite:</span><span class="sxs-lookup"><span data-stu-id="23885-140">The following image shows the satellite assembly directory:</span></span>

![Um diretório do assembly satélite com subdiretórios de culturas localizadas.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="23885-142">Compilação de assemblies satélite</span><span class="sxs-lookup"><span data-stu-id="23885-142">Compiling Satellite Assemblies</span></span>

<span data-ttu-id="23885-143">Você usa o [gerador de arquivo de recurso (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) para compilar arquivos de texto ou arquivos XML (*. resx*) que contêm recursos para arquivos *. Resources* binários.</span><span class="sxs-lookup"><span data-stu-id="23885-143">You use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to compile text files or XML (*.resx*) files that contain resources to binary *.resources* files.</span></span> <span data-ttu-id="23885-144">Em seguida, você usa o [vinculador de assembly (Al.exe)](../tools/al-exe-assembly-linker.md) para compilar arquivos *. Resources* em assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="23885-144">You then use [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile *.resources* files into satellite assemblies.</span></span> <span data-ttu-id="23885-145">*Al.exe* cria um assembly a partir dos arquivos *. Resources* que você especificar.</span><span class="sxs-lookup"><span data-stu-id="23885-145">*Al.exe* creates an assembly from the *.resources* files that you specify.</span></span> <span data-ttu-id="23885-146">Assemblies satélites podem conter somente recursos; eles não podem conter nenhum código executável.</span><span class="sxs-lookup"><span data-stu-id="23885-146">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>

<span data-ttu-id="23885-147">O comando a seguir *Al.exe* cria um assembly satélite para o aplicativo `Example` a partir das cadeias de caracteres do arquivo de recursos do alemão *. de. Resources*.</span><span class="sxs-lookup"><span data-stu-id="23885-147">The following *Al.exe* command creates a satellite assembly for the application `Example` from the German resources file *strings.de.resources*.</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

<span data-ttu-id="23885-148">O comando a seguir *Al.exe* também cria um assembly satélite para o aplicativo `Example` a partir das *cadeias de caracteres de arquivo. de. Resources*.</span><span class="sxs-lookup"><span data-stu-id="23885-148">The following *Al.exe* command also creates a satellite assembly for the application `Example` from the file *strings.de.resources*.</span></span> <span data-ttu-id="23885-149">A opção **/Template** faz com que o assembly satélite herde todos os metadados do assembly, exceto para suas informações de cultura do assembly pai (*Example.dll*).</span><span class="sxs-lookup"><span data-stu-id="23885-149">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (*Example.dll*).</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
<span data-ttu-id="23885-150">A tabela a seguir descreve as opções de *Al.exe* usadas nesses comandos mais detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="23885-150">The following table describes the *Al.exe* options used in these commands in more detail:</span></span>
  
|<span data-ttu-id="23885-151">Opção</span><span class="sxs-lookup"><span data-stu-id="23885-151">Option</span></span>|<span data-ttu-id="23885-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="23885-152">Description</span></span>|
|------------|-----------------|
|`-target:lib`|<span data-ttu-id="23885-153">Especifica que o seu assembly satélite é compilado em um arquivo de biblioteca (. dll).</span><span class="sxs-lookup"><span data-stu-id="23885-153">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="23885-154">Como um assembly satélite não contém código executável e não é um assembly principal do aplicativo, você deve salvar assemblies satélites como DLLs.</span><span class="sxs-lookup"><span data-stu-id="23885-154">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|
|`-embed:strings.de.resources`|<span data-ttu-id="23885-155">Especifica o nome do arquivo de recurso a ser inserido quando *Al.exe* compila o assembly.</span><span class="sxs-lookup"><span data-stu-id="23885-155">Specifies the name of the resource file to embed when *Al.exe* compiles the assembly.</span></span> <span data-ttu-id="23885-156">Você pode incorporar vários arquivos .resources em um assembly satélite, mas se estiver seguindo o modelo hub e spoke, compile um assembly satélite para cada cultura.</span><span class="sxs-lookup"><span data-stu-id="23885-156">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="23885-157">No entanto, você pode criar arquivos .resources separados para cadeias de caracteres e objetos.</span><span class="sxs-lookup"><span data-stu-id="23885-157">However, you can create separate .resources files for strings and objects.</span></span>|
|`-culture:de`|<span data-ttu-id="23885-158">Especifica a cultura do recurso para compilar.</span><span class="sxs-lookup"><span data-stu-id="23885-158">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="23885-159">O Common Language Runtime usa essas informações ao procurar os recursos de uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="23885-159">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="23885-160">Se você omitir essa opção, *Al.exe* ainda compilará o recurso, mas o tempo de execução não poderá encontrá-lo quando um usuário solicitar.</span><span class="sxs-lookup"><span data-stu-id="23885-160">If you omit this option, *Al.exe* will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|
|`-out:Example.resources.dll`|<span data-ttu-id="23885-161">Especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="23885-161">Specifies the name of the output file.</span></span> <span data-ttu-id="23885-162">O nome deve seguir o padrão de nomeação *baseName*.resources.\* extensão\*, onde *baseName* é o nome do assembly principal, e *extension* é uma extensão de nome de arquivo válido (como .dll).</span><span class="sxs-lookup"><span data-stu-id="23885-162">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="23885-163">Observe que o runtime não é capaz de determinar a cultura de um assembly satélite com base em seu nome de arquivo de saída; você deve usar a opção **/culture** para especificá-lo.</span><span class="sxs-lookup"><span data-stu-id="23885-163">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|
|`-template:Example.dll`|<span data-ttu-id="23885-164">Especifica o assembly do qual todos os metadados de assembly devem ser herdados, exceto o campo de cultura.</span><span class="sxs-lookup"><span data-stu-id="23885-164">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="23885-165">Esta opção afetará assemblies satélites somente se você especificar um assembly com um [nome forte](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="23885-165">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../standard/assembly/strong-named.md).</span></span>|
  
 <span data-ttu-id="23885-166">Para obter uma lista completa das opções disponíveis com *Al.exe*, consulte [vinculador de assembly (Al.exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="23885-166">For a complete list of options available with *Al.exe*, see [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>
  
## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="23885-167">Assemblies satélites: um exemplo</span><span class="sxs-lookup"><span data-stu-id="23885-167">Satellite Assemblies: An Example</span></span>

<span data-ttu-id="23885-168">Este é um exemplo simples "Olá, Mundo", que exibe uma caixa de mensagem com uma saudação localizada.</span><span class="sxs-lookup"><span data-stu-id="23885-168">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="23885-169">O exemplo inclui recursos para as culturas inglesas (Estados Unidos), francesas (França) e russas (Rússia), e sua cultura de fallback é o inglês.</span><span class="sxs-lookup"><span data-stu-id="23885-169">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="23885-170">Para criar o exemplo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="23885-170">To create the example, do the following:</span></span>
  
1. <span data-ttu-id="23885-171">Crie um arquivo de recurso chamado *greeting. resx* ou *Greeting.txt* para conter o recurso para a cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="23885-171">Create a resource file named *Greeting.resx* or *Greeting.txt* to contain the resource for the default culture.</span></span> <span data-ttu-id="23885-172">Armazene uma única cadeia de caracteres denominada `HelloString`, cujo valor é "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="23885-172">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="23885-173">neste arquivo.</span><span class="sxs-lookup"><span data-stu-id="23885-173">in this file.</span></span>

2. <span data-ttu-id="23885-174">Para indicar que inglês (en) é a cultura padrão do aplicativo, adicione o seguinte atributo <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> ao arquivo AssemblyInfo do aplicativo ou ao arquivo de código-fonte principal que será compilado no assembly principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23885-174">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>

    [!code-csharp[Conceptual.Resources.Locating#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. <span data-ttu-id="23885-175">Adicione suporte a culturas adicionais (en-US, fr-FR e ru-RU) ao aplicativo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="23885-175">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>  
  
    - <span data-ttu-id="23885-176">Para dar suporte à cultura en-US ou inglês (Estados Unidos), crie um arquivo de recurso chamado *greeting. en-US. resx* ou *Greeting.en-US.txt*e armazene-o em uma única cadeia de caracteres chamada `HelloString` cujo valor é "Hi World!".</span><span class="sxs-lookup"><span data-stu-id="23885-176">To support the en-US or English (United States) culture, create a resource file named *Greeting.en-US.resx* or *Greeting.en-US.txt*, and store in it a single string named `HelloString` whose value is "Hi world!".</span></span>
  
    - <span data-ttu-id="23885-177">Para dar suporte à cultura fr-FR ou francês (França), crie um arquivo de recurso chamado *greeting.fr-fr. resx* ou *Greeting.fr-FR.txt*e armazene-o em uma única cadeia de caracteres chamada `HelloString` cujo valor é "saudação do Monde!".</span><span class="sxs-lookup"><span data-stu-id="23885-177">To support the fr-FR or French (France) culture, create a resource file named *Greeting.fr-FR.resx* or *Greeting.fr-FR.txt*, and store in it a single string named `HelloString` whose value is "Salut tout le monde!".</span></span>
  
    - <span data-ttu-id="23885-178">Para dar suporte à cultura RU-RU ou russo (Rússia), crie um arquivo de recurso chamado *greeting.ru-ru. resx* ou *Greeting.ru-RU.txt*e armazene-o em uma única cadeia de caracteres chamada `HelloString` cujo valor é "Всем привет!".</span><span class="sxs-lookup"><span data-stu-id="23885-178">To support the ru-RU or Russian (Russia) culture, create a resource file named *Greeting.ru-RU.resx* or *Greeting.ru-RU.txt*, and store in it a single string named `HelloString` whose value is "Всем привет!".</span></span>
  
4. <span data-ttu-id="23885-179">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) para compilar cada arquivo de recurso XML ou texto em um arquivo binário *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="23885-179">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary *.resources* file.</span></span> <span data-ttu-id="23885-180">A saída é um conjunto de arquivos que têm o mesmo nome de arquivo raiz que os arquivos *. resx* ou *. txt* , mas uma extensão *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="23885-180">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="23885-181">Se você criar o exemplo com o Visual Studio, o processo de compilação será manipulado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="23885-181">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="23885-182">Se você não estiver usando o Visual Studio, execute os seguintes comandos para compilar os arquivos *. resx* em arquivos *. Resources* :</span><span class="sxs-lookup"><span data-stu-id="23885-182">If you aren't using Visual Studio, run the following commands to compile the *.resx* files into *.resources* files:</span></span>  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    <span data-ttu-id="23885-183">Se os recursos estiverem em arquivos de texto em vez de em arquivos XML, substitua a extensão *. resx* por *. txt*.</span><span class="sxs-lookup"><span data-stu-id="23885-183">If your resources are in text files instead of XML files, replace the *.resx* extension with *.txt*.</span></span>

5. <span data-ttu-id="23885-184">Compile o código-fonte abaixo com os recursos para a cultura padrão no assembly principal do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="23885-184">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="23885-185">Se você estiver usando a linha de comando em vez do Visual Studio para criar o exemplo, deverá modificar a chamada para o construtor de classe <xref:System.Resources.ResourceManager> para o seguinte: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="23885-185">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span></span>

    [!code-csharp[Conceptual.Resources.Locating#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    <span data-ttu-id="23885-186">Se o aplicativo for chamado de exemplo e você estiver compilando a partir da linha de comando, o comando para o compilador C# é:</span><span class="sxs-lookup"><span data-stu-id="23885-186">If the application is named Example and you are compiling from the command-line, the command for the C# compiler is:</span></span>

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    <span data-ttu-id="23885-187">O comando do compilador Visual Basic correspondente é:</span><span class="sxs-lookup"><span data-stu-id="23885-187">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. <span data-ttu-id="23885-188">Crie um subdiretório no diretório do aplicativo principal para cada cultura localizada com suporte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23885-188">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="23885-189">Você deve criar um *en-US*, um *fr-fr*e um subdiretório *ru-ru* .</span><span class="sxs-lookup"><span data-stu-id="23885-189">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="23885-190">O Visual Studio cria esses subdiretórios automaticamente como parte do processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="23885-190">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>

7. <span data-ttu-id="23885-191">Insira os arquivos *. Resources* específicos da cultura em assemblies satélites e salve-os no diretório apropriado.</span><span class="sxs-lookup"><span data-stu-id="23885-191">Embed the individual culture-specific *.resources* files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="23885-192">O comando para fazer isso para cada arquivo *. Resources* é:</span><span class="sxs-lookup"><span data-stu-id="23885-192">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

     <span data-ttu-id="23885-193">onde *cultura* é o nome da cultura cujos recursos o assembly satélite contém.</span><span class="sxs-lookup"><span data-stu-id="23885-193">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="23885-194">O Visual Studio trata esse processo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="23885-194">Visual Studio handles this process automatically.</span></span>

<span data-ttu-id="23885-195">Você pode executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="23885-195">You can then run the example.</span></span> <span data-ttu-id="23885-196">Isso tornará aleatoriamente uma das culturas com suporte a cultura atual e exibirá uma saudação localizada.</span><span class="sxs-lookup"><span data-stu-id="23885-196">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="23885-197">Instalação de assemblies satélite no Cache de Assembly Global (GAC)</span><span class="sxs-lookup"><span data-stu-id="23885-197">Installing Satellite Assemblies in the Global Assembly Cache</span></span>

<span data-ttu-id="23885-198">Em vez de instalar assemblies em um subdiretório do aplicativo local, você pode instalá-los no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="23885-198">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="23885-199">Isso é particularmente útil se você tiver bibliotecas de classes e assemblies de recursos de biblioteca de classe usados por vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="23885-199">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>
  
<span data-ttu-id="23885-200">A instalação de assemblies no cache de assembly global exige que eles tenham nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="23885-200">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="23885-201">Assemblies com nomes fortes são assinados com um par de chaves públicas/privadas válido.</span><span class="sxs-lookup"><span data-stu-id="23885-201">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="23885-202">Elas contêm informações de versão que o runtime usa para determinar qual assembly usar para atender a uma solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="23885-202">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="23885-203">Para obter mais informações sobre nomes fortes e controle de versão, consulte [Controle de versão do assembly](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="23885-203">For more information about strong names and versioning, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span> <span data-ttu-id="23885-204">Para obter mais informações sobre nomes fortes, consulte [Assemblies com nome forte](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="23885-204">For more information about strong names, see [Strong-Named Assemblies](../../standard/assembly/strong-named.md).</span></span>

<span data-ttu-id="23885-205">Quando você estiver desenvolvendo um aplicativo, é improvável que tenha acesso ao par de chaves públicas/privadas final.</span><span class="sxs-lookup"><span data-stu-id="23885-205">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="23885-206">Para instalar um assembly satélite no cache de assembly global e garantir que ele funcione conforme o esperado, você pode usar uma técnica chamada assinatura atrasada.</span><span class="sxs-lookup"><span data-stu-id="23885-206">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="23885-207">Quando você atrasar a assinatura de um assembly, no momento da compilação, reserve espaço no arquivo para a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="23885-207">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="23885-208">A assinatura real é atrasada até mais tarde, quando o par de chaves públicas/privadas final ficar disponível.</span><span class="sxs-lookup"><span data-stu-id="23885-208">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="23885-209">Para obter mais informações sobre o processo de assinatura com atraso, consulte [Assinatura com atraso de um assembly](../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="23885-209">For more information about delayed signing, see [Delay Signing an Assembly](../../standard/assembly/delay-sign.md).</span></span>

### <a name="obtaining-the-public-key"></a><span data-ttu-id="23885-210">Obtenção da chave pública</span><span class="sxs-lookup"><span data-stu-id="23885-210">Obtaining the Public Key</span></span>

<span data-ttu-id="23885-211">Para atrasar a assinatura de um assembly, você deve ter acesso à chave pública.</span><span class="sxs-lookup"><span data-stu-id="23885-211">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="23885-212">Você pode obter a chave pública real da organização para sua empresa que fará a eventual assinatura, ou criar uma chave pública usando a [Ferramenta de Nome Forte (Sn.exe)](../tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="23885-212">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md).</span></span>

<span data-ttu-id="23885-213">O comando a seguir *Sn.exe* cria um par de chaves pública/privada de teste.</span><span class="sxs-lookup"><span data-stu-id="23885-213">The following *Sn.exe* command creates a test public/private key pair.</span></span> <span data-ttu-id="23885-214">A opção **– k** especifica que *Sn.exe* deve criar um novo par de chaves e salvá-lo em um arquivo chamado *TestKeyPair. SNK*.</span><span class="sxs-lookup"><span data-stu-id="23885-214">The **–k** option specifies that *Sn.exe* should create a new key pair and save it in a file named *TestKeyPair.snk*.</span></span>
  
```console
sn –k TestKeyPair.snk
```

<span data-ttu-id="23885-215">Você pode extrair a chave pública do arquivo que contém o par de chaves de teste.</span><span class="sxs-lookup"><span data-stu-id="23885-215">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="23885-216">O comando a seguir extrai a chave pública de *TestKeyPair. SNK* e a salva em *PublicKey. SNK*:</span><span class="sxs-lookup"><span data-stu-id="23885-216">The following command extracts the public key from *TestKeyPair.snk* and saves it in *PublicKey.snk*:</span></span>

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a><span data-ttu-id="23885-217">Atrasando a assinatura de um assembly</span><span class="sxs-lookup"><span data-stu-id="23885-217">Delay Signing an Assembly</span></span>

<span data-ttu-id="23885-218">Depois de obter ou criar a chave pública, use o [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) para compilar o assembly e especificar a assinatura com atraso.</span><span class="sxs-lookup"><span data-stu-id="23885-218">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>

<span data-ttu-id="23885-219">O comando a seguir *Al.exe* cria um assembly satélite de nome forte para o aplicativo StringLibrary do arquivo *Strings. ja. Resources* :</span><span class="sxs-lookup"><span data-stu-id="23885-219">The following *Al.exe* command creates a strong-named satellite assembly for the application StringLibrary from the *strings.ja.resources* file:</span></span>

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

<span data-ttu-id="23885-220">A opção **-delay+** especifica que o Assembly Linker deve atrasar a assinatura do assembly.</span><span class="sxs-lookup"><span data-stu-id="23885-220">The **-delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="23885-221">A opção **-keyfile** especifica o nome do arquivo de chave que contém a chave pública a ser usada para atrasar a assinatura do assembly.</span><span class="sxs-lookup"><span data-stu-id="23885-221">The **-keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>

### <a name="re-signing-an-assembly"></a><span data-ttu-id="23885-222">Nova assinatura de um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="23885-222">Re-signing an Assembly</span></span>

<span data-ttu-id="23885-223">Antes de implantar seu aplicativo, você deve reassinar o assembly satélite com atraso com o par de chaves real.</span><span class="sxs-lookup"><span data-stu-id="23885-223">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="23885-224">Você pode fazer isso usando *Sn.exe*.</span><span class="sxs-lookup"><span data-stu-id="23885-224">You can do this by using *Sn.exe*.</span></span>

<span data-ttu-id="23885-225">Os seguintes *Sn.exem* os sinais de comando *StringLibrary.resources.dll* com o par de chaves armazenado no arquivo *RealKeyPair. SNK*.</span><span class="sxs-lookup"><span data-stu-id="23885-225">The following *Sn.exe* command signs *StringLibrary.resources.dll* with the key pair stored in the file *RealKeyPair.snk*.</span></span> <span data-ttu-id="23885-226">A opção **– R** especifica que um assembly assinado anteriormente ou assinado com atraso deve ser assinado novamente.</span><span class="sxs-lookup"><span data-stu-id="23885-226">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="23885-227">Instalação de assemblies satélite no Cache de Assembly Global (GAC)</span><span class="sxs-lookup"><span data-stu-id="23885-227">Installing a Satellite Assembly in the Global Assembly Cache</span></span>

<span data-ttu-id="23885-228">Quando o runtime procura recursos no processo de fallback de recursos, ele examina o [cache de assembly global](../app-domains/gac.md) primeiro.</span><span class="sxs-lookup"><span data-stu-id="23885-228">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../app-domains/gac.md) first.</span></span> <span data-ttu-id="23885-229">(Para obter mais informações, consulte a seção "processo de fallback de recursos" do tópico [empacotando e implantando recursos](packaging-and-deploying-resources-in-desktop-apps.md) .) Assim que um assembly satélite é assinado com um nome forte, ele pode ser instalado no cache de assembly global usando o [ferramenta de cache de assembly global (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="23885-229">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span>

<span data-ttu-id="23885-230">O comando a seguir *Gacutil.exe* instala *StringLibrary.resources.dll*\* no cache de assembly global:</span><span class="sxs-lookup"><span data-stu-id="23885-230">The following *Gacutil.exe* command installs *StringLibrary.resources.dll*\* in the global assembly cache:</span></span>

```console
gacutil -i:StringLibrary.resources.dll
```

<span data-ttu-id="23885-231">A opção **/i** especifica que *Gacutil.exe* deve instalar o assembly especificado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="23885-231">The **/i** option specifies that *Gacutil.exe* should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="23885-232">Após o satélite assembly ser instalado no cache, os recursos que ele contém ficam disponíveis para todos os aplicativos que são projetados para usar o assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="23885-232">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>

### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="23885-233">Recursos no Cache de Assembly Global: um exemplo</span><span class="sxs-lookup"><span data-stu-id="23885-233">Resources in the Global Assembly Cache: An Example</span></span>

<span data-ttu-id="23885-234">O exemplo a seguir usa um método em uma biblioteca de classes .NET Framework para extrair e retornar uma saudação localizada de um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="23885-234">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="23885-235">A biblioteca e seus recursos são registrados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="23885-235">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="23885-236">O exemplo do inclui recursos para as culturas inglesa (Estados Unidos), francesa (França), russa (Rússia) e inglesas.</span><span class="sxs-lookup"><span data-stu-id="23885-236">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="23885-237">Inglês é a cultura padrão; seus recursos são armazenados no assembly principal.</span><span class="sxs-lookup"><span data-stu-id="23885-237">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="23885-238">O exemplo inicialmente atrasa a assinatura da biblioteca e seus assemblies satélites com uma chave pública. Em seguida, assina-os novamente com um par de chaves públicas/privadas.</span><span class="sxs-lookup"><span data-stu-id="23885-238">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="23885-239">Para criar o exemplo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="23885-239">To create the example, do the following:</span></span>

1. <span data-ttu-id="23885-240">Se você não estiver usando o Visual Studio, use o seguinte comando de [ferramenta de nome forte (Sn.exe)](../tools/sn-exe-strong-name-tool.md) para criar um par de chaves pública/privada chamado *ResKey. SNK*:</span><span class="sxs-lookup"><span data-stu-id="23885-240">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named *ResKey.snk*:</span></span>

    ```console
    sn –k ResKey.snk
    ```

    <span data-ttu-id="23885-241">Se você estiver usando o Visual Studio, use a guia **Assinatura** da caixa de diálogo **Propriedades** do projeto para gerar o arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="23885-241">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>

2. <span data-ttu-id="23885-242">Use o seguinte comando de [ferramenta de nome forte (Sn.exe)](../tools/sn-exe-strong-name-tool.md) para criar um arquivo de chave pública chamado *PublicKey. SNK*:</span><span class="sxs-lookup"><span data-stu-id="23885-242">Use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public key file named *PublicKey.snk*:</span></span>

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. <span data-ttu-id="23885-243">Crie um arquivo de recurso chamado *Strings. resx* para conter o recurso para a cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="23885-243">Create a resource file named *Strings.resx* to contain the resource for the default culture.</span></span> <span data-ttu-id="23885-244">Armazene uma única cadeia de caracteres denominada `Greeting` cujo valor é "How do you do?"</span><span class="sxs-lookup"><span data-stu-id="23885-244">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="23885-245">nesse arquivo.</span><span class="sxs-lookup"><span data-stu-id="23885-245">in that file.</span></span>

4. <span data-ttu-id="23885-246">Para indicar que “en” é a cultura padrão do aplicativo, adicione o seguinte atributo <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> ao arquivo AssemblyInfo do aplicativo ou ao arquivo de código-fonte principal que será compilado no assembly principal do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="23885-246">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. <span data-ttu-id="23885-247">Adicione suporte a culturas adicionais (en-US, fr-FR e ru-RU) ao aplicativo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="23885-247">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>

    - <span data-ttu-id="23885-248">Para dar suporte à cultura "en-US" ou inglês (Estados Unidos), crie um arquivo de recurso chamado *Strings. en-US. resx* ou *Strings.en-US.txt*e armazene-o em uma única cadeia de caracteres chamada `Greeting` cujo valor é "Hello!".</span><span class="sxs-lookup"><span data-stu-id="23885-248">To support the "en-US" or English (United States) culture, create a resource file named *Strings.en-US.resx* or *Strings.en-US.txt*, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>

    - <span data-ttu-id="23885-249">Para dar suporte à cultura "fr-FR" ou francês (França), crie um arquivo de recurso chamado *Strings.fr-fr. resx* ou *Strings.fr-FR.txt* e armazene-o em uma única cadeia de caracteres chamada `Greeting` cujo valor é "Bno atual!".</span><span class="sxs-lookup"><span data-stu-id="23885-249">To support the "fr-FR" or French (France) culture, create a resource file named *Strings.fr-FR.resx* or *Strings.fr-FR.txt* and store in it a single string named `Greeting` whose value is "Bon jour!".</span></span>

    - <span data-ttu-id="23885-250">Para dar suporte à cultura "ru-RU" ou russo (Rússia), crie um arquivo de recurso chamado *Strings.ru-ru. resx* ou *Strings.ru-RU.txt* e armazene-o em uma única cadeia de caracteres chamada `Greeting` cujo valor é "привет!".</span><span class="sxs-lookup"><span data-stu-id="23885-250">To support the "ru-RU" or Russian (Russia) culture, create a resource file named *Strings.ru-RU.resx* or *Strings.ru-RU.txt* and store in it a single string named `Greeting` whose value is "Привет!".</span></span>

6. <span data-ttu-id="23885-251">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) para compilar cada texto ou um arquivo de recursos XML em um arquivo binário .resources.</span><span class="sxs-lookup"><span data-stu-id="23885-251">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="23885-252">A saída é um conjunto de arquivos que têm o mesmo nome de arquivo raiz que os arquivos *. resx* ou *. txt* , mas uma extensão *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="23885-252">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="23885-253">Se você criar o exemplo com o Visual Studio, o processo de compilação será manipulado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="23885-253">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="23885-254">Se você não estiver usando o Visual Studio, execute o seguinte comando para compilar os arquivos *. resx* em arquivos *. Resources* :</span><span class="sxs-lookup"><span data-stu-id="23885-254">If you aren't using Visual Studio, run the following command to compile the *.resx* files into *.resources* files:</span></span>

    ```console
    resgen filename
    ```

    <span data-ttu-id="23885-255">Em que *filename* é o caminho opcional, o nome do arquivo e a extensão do arquivo *. resx* ou de texto.</span><span class="sxs-lookup"><span data-stu-id="23885-255">Where *filename* is the optional path, file name, and extension of the *.resx* or text file.</span></span>

7. <span data-ttu-id="23885-256">Compile o seguinte código-fonte para *StringLibrary. vb* ou *StringLibrary.cs* junto com os recursos para a cultura padrão em um assembly de biblioteca assinado com atraso chamado *StringLibrary.dll*:</span><span class="sxs-lookup"><span data-stu-id="23885-256">Compile the following source code for *StringLibrary.vb* or *StringLibrary.cs* along with the resources for the default culture into a delay signed library assembly named *StringLibrary.dll*:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="23885-257">Se você estiver usando a linha de comando em vez do Visual Studio para criar o exemplo, deverá modificar a chamada para o <xref:System.Resources.ResourceManager> Construtor de classe para `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);` .</span><span class="sxs-lookup"><span data-stu-id="23885-257">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    <span data-ttu-id="23885-258">O comando para o compilador do C# é:</span><span class="sxs-lookup"><span data-stu-id="23885-258">The command for the C# compiler is:</span></span>

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    <span data-ttu-id="23885-259">O comando do compilador Visual Basic correspondente é:</span><span class="sxs-lookup"><span data-stu-id="23885-259">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. <span data-ttu-id="23885-260">Crie um subdiretório no diretório do aplicativo principal para cada cultura localizada com suporte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23885-260">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="23885-261">Você deve criar um *en-US*, um *fr-fr*e um subdiretório *ru-ru* .</span><span class="sxs-lookup"><span data-stu-id="23885-261">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="23885-262">O Visual Studio cria esses subdiretórios automaticamente como parte do processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="23885-262">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="23885-263">Como todos os assemblies satélite têm o mesmo nome de arquivo, os subdiretórios são usados para armazenar assemblies satélite de cultura específica individuais até que eles sejam assinados com um par de chaves públicas/privadas.</span><span class="sxs-lookup"><span data-stu-id="23885-263">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>

9. <span data-ttu-id="23885-264">Insira os arquivos *. Resources* específicos da cultura em atraso nos assemblies satélite assinados e salve-os no diretório apropriado.</span><span class="sxs-lookup"><span data-stu-id="23885-264">Embed the individual culture-specific *.resources* files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="23885-265">O comando para fazer isso para cada arquivo *. Resources* é:</span><span class="sxs-lookup"><span data-stu-id="23885-265">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    <span data-ttu-id="23885-266">onde *culture* é o nome de uma cultura.</span><span class="sxs-lookup"><span data-stu-id="23885-266">where *culture* is the name of a culture.</span></span> <span data-ttu-id="23885-267">Neste exemplo, os nomes de cultura são ru-RU, en-US e fr-FR.</span><span class="sxs-lookup"><span data-stu-id="23885-267">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>

10. <span data-ttu-id="23885-268">Assine novamente *StringLibrary.dll* usando a ferramenta de [nome forte (Sn.exe)](../tools/sn-exe-strong-name-tool.md) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="23885-268">Re-sign *StringLibrary.dll* by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows:</span></span>

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. <span data-ttu-id="23885-269">Assine novamente os assemblies satélite individuais.</span><span class="sxs-lookup"><span data-stu-id="23885-269">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="23885-270">Para fazer isso, use a [Ferramenta de Nome Forte (Sn.exe)](../tools/sn-exe-strong-name-tool.md) da seguinte forma para cada assembly satélite:</span><span class="sxs-lookup"><span data-stu-id="23885-270">To do this, use the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. <span data-ttu-id="23885-271">Registre *StringLibrary.dll* e cada um de seus assemblies satélites no cache de assembly global usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="23885-271">Register *StringLibrary.dll* and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>

    ```console
    gacutil -i filename
    ```

    <span data-ttu-id="23885-272">onde *filename* é o nome do arquivo para registrar.</span><span class="sxs-lookup"><span data-stu-id="23885-272">where *filename* is the name of the file to register.</span></span>

13. <span data-ttu-id="23885-273">Se você estiver usando o Visual Studio, crie um novo projeto de **aplicativo de console** chamado `Example` , adicione uma referência a *StringLibrary.dll* e o seguinte código-fonte a ele e compile.</span><span class="sxs-lookup"><span data-stu-id="23885-273">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to *StringLibrary.dll* and the following source code to it, and compile.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    <span data-ttu-id="23885-274">Para compilar da linha de comando, use o seguinte comando para o compilador do C#:</span><span class="sxs-lookup"><span data-stu-id="23885-274">To compile from the command line, use the following command for the C# compiler:</span></span>

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    <span data-ttu-id="23885-275">A linha de comando para o compilador do Visual Basic é:</span><span class="sxs-lookup"><span data-stu-id="23885-275">The command line for the Visual Basic compiler is:</span></span>

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. <span data-ttu-id="23885-276">Execute *Example.exe*.</span><span class="sxs-lookup"><span data-stu-id="23885-276">Run *Example.exe*.</span></span>

## <a name="see-also"></a><span data-ttu-id="23885-277">Confira também</span><span class="sxs-lookup"><span data-stu-id="23885-277">See also</span></span>

- [<span data-ttu-id="23885-278">Empacotando e implantando recursos</span><span class="sxs-lookup"><span data-stu-id="23885-278">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="23885-279">Assinar um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="23885-279">Delay Signing an Assembly</span></span>](../../standard/assembly/delay-sign.md)
- [<span data-ttu-id="23885-280">Al.exe (vinculador de assembly)</span><span class="sxs-lookup"><span data-stu-id="23885-280">Al.exe (Assembly Linker)</span></span>](../tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="23885-281">Sn.exe (ferramenta de nome forte)</span><span class="sxs-lookup"><span data-stu-id="23885-281">Sn.exe (Strong Name Tool)</span></span>](../tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="23885-282">Gacutil.exe (Ferramenta de Cache de Assembly Global)</span><span class="sxs-lookup"><span data-stu-id="23885-282">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="23885-283">Recursos em aplicativos da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="23885-283">Resources in Desktop Apps</span></span>](index.md)
