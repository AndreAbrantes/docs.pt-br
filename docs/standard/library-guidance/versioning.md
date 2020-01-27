---
title: Bibliotecas de controle de versão e .NET
description: Recomendações de melhores práticas para controle de versão de bibliotecas do .NET.
ms.date: 12/10/2018
ms.openlocfilehash: a274410714791e2790da0e3deb2a595390ee9389
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745021"
---
# <a name="versioning"></a><span data-ttu-id="ae849-103">{1&gt;Controle de versão&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ae849-103">Versioning</span></span>

<span data-ttu-id="ae849-104">Uma biblioteca de software raramente está completa na versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="ae849-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="ae849-105">Boas bibliotecas evoluem com o tempo, adicionando recursos, corrigindo bugs e melhorando o desempenho.</span><span class="sxs-lookup"><span data-stu-id="ae849-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="ae849-106">É importante que você possa liberar novas versões de uma biblioteca do .NET, fornecendo valor adicional a cada versão, sem interromper os usuários existentes.</span><span class="sxs-lookup"><span data-stu-id="ae849-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="ae849-107">Alterações da falha</span><span class="sxs-lookup"><span data-stu-id="ae849-107">Breaking changes</span></span>

<span data-ttu-id="ae849-108">Para obter informações sobre como lidar com alterações da falha entre as versões, veja [Alterações da falha](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ae849-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="ae849-109">Números de versão</span><span class="sxs-lookup"><span data-stu-id="ae849-109">Version numbers</span></span>

<span data-ttu-id="ae849-110">Uma biblioteca .NET tem várias maneiras de especificar uma versão.</span><span class="sxs-lookup"><span data-stu-id="ae849-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="ae849-111">Essas versões são as mais importantes:</span><span class="sxs-lookup"><span data-stu-id="ae849-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="ae849-112">Versão do pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="ae849-112">NuGet package version</span></span>

<span data-ttu-id="ae849-113">A [Versão do pacote NuGet](/nuget/reference/package-versioning) é exibida em NuGet.org, o gerenciador de pacotes do NuGet do Visual Studio e adicionada ao código-fonte quando o pacote é usado.</span><span class="sxs-lookup"><span data-stu-id="ae849-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="ae849-114">A versão do pacote NuGet é o número de versão que os usuários normalmente verão e ao qual eles farão referência ao falarem sobre a versão de uma biblioteca que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="ae849-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="ae849-115">A versão do pacote NuGet é usada pelo NuGet e não tem nenhum efeito sobre o comportamento de runtime.</span><span class="sxs-lookup"><span data-stu-id="ae849-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="ae849-116">O identificador de pacote do NuGet combinado com a versão do pacote NuGet é usado para identificar um pacote no NuGet.</span><span class="sxs-lookup"><span data-stu-id="ae849-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="ae849-117">Por exemplo, `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="ae849-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="ae849-118">Um pacote com um sufixo é um pacote de pré-lançamento e tem um comportamento especial que o torna ideal para teste.</span><span class="sxs-lookup"><span data-stu-id="ae849-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="ae849-119">Para obter mais informações, veja [Pacotes pré-lançamento](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="ae849-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="ae849-120">Como a versão do pacote NuGet é a versão mais visível para os desenvolvedores, é uma boa ideia atualizá-la usando [SemVer (Controle de Versão de Semântica)](https://semver.org/).</span><span class="sxs-lookup"><span data-stu-id="ae849-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="ae849-121">SemVer indica a importância das alterações entre as versões e ajuda os desenvolvedores a tomarem uma decisão bem informada ao escolherem qual versão usar.</span><span class="sxs-lookup"><span data-stu-id="ae849-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="ae849-122">Por exemplo, ir de `1.0` para `2.0` indica que potencialmente há alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="ae849-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="ae849-123">✔️ Considere usar [SemVer 2.0.0](https://semver.org/) para versão do seu pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ae849-123">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="ae849-124">✔️ usar a versão do pacote NuGet na documentação pública, pois é o número de versão que os usuários normalmente verão.</span><span class="sxs-lookup"><span data-stu-id="ae849-124">✔️ DO use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="ae849-125">✔️ inclui um sufixo de pré-lançamento ao liberar um pacote não estável.</span><span class="sxs-lookup"><span data-stu-id="ae849-125">✔️ DO include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="ae849-126">Os usuários devem aceitar receberem pacotes de pré-lançamento, assim, eles entenderão que o pacote não está concluído.</span><span class="sxs-lookup"><span data-stu-id="ae849-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="ae849-127">Versão do assembly</span><span class="sxs-lookup"><span data-stu-id="ae849-127">Assembly version</span></span>

<span data-ttu-id="ae849-128">A versão do assembly é o que o CLR usa no runtime para selecionar qual versão de um assembly carregar.</span><span class="sxs-lookup"><span data-stu-id="ae849-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="ae849-129">Selecionar um assembly usando o controle de versão só se aplica aos assemblies com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="ae849-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="ae849-130">O Windows .NET Framework CLR exige uma correspondência exata para carregar um assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="ae849-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="ae849-131">Por exemplo, `Libary1, Version=1.0.0.0` foi compilado com uma referência ao `Newtonsoft.Json, Version=11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="ae849-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="ae849-132">O .NET Framework só carregará a versão exata `11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="ae849-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="ae849-133">Para carregar uma versão diferente no runtime, um redirecionamento de associação deve ser adicionado ao arquivo de configuração do aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="ae849-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="ae849-134">Nomenclatura forte combinada com a versão do assembly habilita [carregamento de versão do assembly estrita](../assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="ae849-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="ae849-135">Embora dar um nome forte a uma biblioteca tenha uma série de benefícios, isso tenderá a resultar em exceções de runtime de que um assembly não pode ser encontrado e [exigirá que redirecionamentos de associação](../../framework/configure-apps/redirect-assembly-versions.md) em `app.config`/`web.config` sejam corrigidos.</span><span class="sxs-lookup"><span data-stu-id="ae849-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="ae849-136">O carregamento do assembly do .NET Core foi relaxado e o .NET Core CLR carregará automaticamente os assemblies no runtime com uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="ae849-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="ae849-137">✔️ Considere apenas a inclusão de uma versão principal no AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="ae849-137">✔️ CONSIDER only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="ae849-138">Por exemplo, Biblioteca 1.0 e Biblioteca 1.0.1 têm ambas uma AssemblyVersion de `1.0.0.0`, enquanto a Biblioteca 2.0 tem uma AssemblyVersion de `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="ae849-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="ae849-139">Quando a versão do assembly é alterada com menos frequência, ela reduz os redirecionamentos de associação.</span><span class="sxs-lookup"><span data-stu-id="ae849-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="ae849-140">✔️ Considere manter o número de versão principal do AssemblyVersion e a versão do pacote NuGet em sincronia.</span><span class="sxs-lookup"><span data-stu-id="ae849-140">✔️ CONSIDER keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="ae849-141">A versão do AssemblyVersion é incluída em algumas mensagens informativas exibidas ao usuário, por exemplo, o nome do assembly e os nomes de tipo qualificados do assembly em mensagens de exceção.</span><span class="sxs-lookup"><span data-stu-id="ae849-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="ae849-142">Manter uma relação entre as versões fornece mais informações para desenvolvedores sobre qual versão eles estão usando.</span><span class="sxs-lookup"><span data-stu-id="ae849-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="ae849-143">❌ não tem um AssemblyVersion fixo.</span><span class="sxs-lookup"><span data-stu-id="ae849-143">❌ DO NOT have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="ae849-144">Embora um AssemblyVersion inalterável evite a necessidade de redirecionamentos de associação, isso significa que apenas uma única versão do assembly pode ser instalada no GAC (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="ae849-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="ae849-145">Além disso, os aplicativos que fazem referência ao assembly no GAC serão interrompidos se outro aplicativo atualizar o assembly do GAC com alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="ae849-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="ae849-146">Versão do arquivo do assembly</span><span class="sxs-lookup"><span data-stu-id="ae849-146">Assembly file version</span></span>

<span data-ttu-id="ae849-147">A versão de arquivo do assembly é usada para exibir uma versão de arquivo no Windows e não tem nenhum efeito sobre o comportamento de runtime.</span><span class="sxs-lookup"><span data-stu-id="ae849-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="ae849-148">Configurar esta versão é opcional.</span><span class="sxs-lookup"><span data-stu-id="ae849-148">Setting this version is optional.</span></span> <span data-ttu-id="ae849-149">Ele ficará visível na caixa de diálogo Propriedades do Arquivo no Windows Explorer:</span><span class="sxs-lookup"><span data-stu-id="ae849-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="ae849-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span><span class="sxs-lookup"><span data-stu-id="ae849-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="ae849-151">✔️ Considere incluir um número de Build de integração contínua como a revisão AssemblyFileVersion.</span><span class="sxs-lookup"><span data-stu-id="ae849-151">✔️ CONSIDER including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="ae849-152">Por exemplo, você está criando a versão 1.0.0 do seu projeto e o número de build de integração contínua é 99, portanto, sua AssemblyFileVersion é 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="ae849-152">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="ae849-153">✔️ Use o formato `Major.Minor.Build.Revision` para a versão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ae849-153">✔️ DO use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="ae849-154">Embora a versão de arquivo nunca seja usada pelo .NET, o [Windows espera que a versão de arquivo](/windows/desktop/menurc/versioninfo-resource) esteja no formato `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="ae849-154">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="ae849-155">Um aviso é acionado se a versão não segue esse formato.</span><span class="sxs-lookup"><span data-stu-id="ae849-155">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="ae849-156">Versão informativa do assembly</span><span class="sxs-lookup"><span data-stu-id="ae849-156">Assembly informational version</span></span>

<span data-ttu-id="ae849-157">A versão informativa do assembly é usada para registrar informações adicionais de versão e não tem nenhum efeito sobre o comportamento de runtime.</span><span class="sxs-lookup"><span data-stu-id="ae849-157">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="ae849-158">Configurar esta versão é opcional.</span><span class="sxs-lookup"><span data-stu-id="ae849-158">Setting this version is optional.</span></span> <span data-ttu-id="ae849-159">Se você estiver usando o Source Link, essa versão será definida no build com a versão do pacote NuGet, além de uma versão de controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ae849-159">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="ae849-160">Por exemplo, `1.0.0-beta1+204ff0a` inclui o hash de confirmação do código-fonte do qual o assembly foi criado.</span><span class="sxs-lookup"><span data-stu-id="ae849-160">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="ae849-161">Para obter mais informações, confira [Source Link](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="ae849-161">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="ae849-162">As versões mais antigas do Visual Studio acionam um aviso de build caso essa versão não siga o formato `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="ae849-162">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="ae849-163">O aviso pode ser ignorado com segurança.</span><span class="sxs-lookup"><span data-stu-id="ae849-163">The warning can be safely ignored.</span></span>

<span data-ttu-id="ae849-164">❌ Evite definir a versão informativa do assembly por conta própria.</span><span class="sxs-lookup"><span data-stu-id="ae849-164">❌ AVOID setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="ae849-165">Permita a SourceLink gerar automaticamente a versão que contém metadados de controle do código-fonte e NuGet.</span><span class="sxs-lookup"><span data-stu-id="ae849-165">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ae849-166">[Anterior](publish-nuget-package.md)
>[Próximo](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="ae849-166">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
