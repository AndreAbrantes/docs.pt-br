---
title: Publicar um pacote NuGet
description: Práticas recomendadas para a publicação de bibliotecas .NET para NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744559"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="f1fba-103">Publicar um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="f1fba-103">Publishing a NuGet package</span></span>

<span data-ttu-id="f1fba-104">Os pacotes NuGet são publicados e consumidos dos repositórios de pacote.</span><span class="sxs-lookup"><span data-stu-id="f1fba-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="f1fba-105">Embora o NuGet.org seja o repositório mais amplamente conhecido e usado, há muitos locais para publicar pacotes NuGet:</span><span class="sxs-lookup"><span data-stu-id="f1fba-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="f1fba-106">**[NuGet.org](https://www.nuget.org/)** é o principal repositório online para pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="f1fba-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="f1fba-107">Todos os pacotes no NuGet.org estão disponíveis publicamente para todos.</span><span class="sxs-lookup"><span data-stu-id="f1fba-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="f1fba-108">Por padrão, o Visual Studio tem o NuGet.org como fonte de pacotes, e para muitos desenvolvedores o NuGet.org é o único repositório de pacotes com o qual eles vão interagir.</span><span class="sxs-lookup"><span data-stu-id="f1fba-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="f1fba-109">O NuGet.org é o melhor lugar para publicar pacotes estáveis e pacotes de pré-lançamento para os quais você deseja comentários da comunidade.</span><span class="sxs-lookup"><span data-stu-id="f1fba-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="f1fba-110">**[MyGet](https://myget.org/)** é um serviço de repositório que oferece suporte aos feeds de pacotes personalizados para projetos de software livre.</span><span class="sxs-lookup"><span data-stu-id="f1fba-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="f1fba-111">Um feed personalizado público do MyGet é um local ideal para publicar pacotes de pré-lançamento criados pelo seu serviço de CI.</span><span class="sxs-lookup"><span data-stu-id="f1fba-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="f1fba-112">O MyGet também fornece comercialmente feeds privados.</span><span class="sxs-lookup"><span data-stu-id="f1fba-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="f1fba-113">Um **[feed local](/nuget/hosting-packages/local-feeds)** permite que você trate uma pasta como um repositório de pacotes e torna os arquivos `*.nupkg` na pasta acessível pelo NuGet.</span><span class="sxs-lookup"><span data-stu-id="f1fba-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="f1fba-114">Um feed local é útil para testar um pacote do NuGet antes de publicá-lo no NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="f1fba-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="f1fba-115">O NuGet.org [não permite que um pacote seja excluído](/nuget/policies/deleting-packages) depois que ele foi carregado.</span><span class="sxs-lookup"><span data-stu-id="f1fba-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="f1fba-116">Um pacote pode ser não listado para que não seja visível publicamente na interface do usuário, mas o `*.nupkg` ainda pode ser baixado na restauração.</span><span class="sxs-lookup"><span data-stu-id="f1fba-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="f1fba-117">Além disso, o nuget.org não permite versões duplicadas do pacote.</span><span class="sxs-lookup"><span data-stu-id="f1fba-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="f1fba-118">Para corrigir um pacote NuGet com um erro, você precisa remover o pacote incorreto, aumentar o número de versão e publicar uma nova versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="f1fba-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="f1fba-119">✔️ [publicar pacotes estáveis e pacotes de pré-lançamento](/nuget/create-packages/publish-a-package) nos quais você deseja que os comentários da Comunidade NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="f1fba-119">✔️ DO [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="f1fba-120">✔️ Considere a publicação de pacotes de pré-lançamento em um feed MyGet de uma compilação de integração contínua.</span><span class="sxs-lookup"><span data-stu-id="f1fba-120">✔️ CONSIDER publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="f1fba-121">✔️ Considere o teste de pacotes em seu ambiente de desenvolvimento usando um feed local ou MyGet.</span><span class="sxs-lookup"><span data-stu-id="f1fba-121">✔️ CONSIDER testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="f1fba-122">Verifique se o pacote funciona e publique-o no NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="f1fba-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="f1fba-123">Segurança no NuGet.org</span><span class="sxs-lookup"><span data-stu-id="f1fba-123">NuGet.org security</span></span>

<span data-ttu-id="f1fba-124">É importante que os invasores não possam acessar sua conta do NuGet e carregar uma versão mal-intencionado da sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="f1fba-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="f1fba-125">O NuGet.org oferece autenticação de dois fatores e notificações por email quando um pacote é publicado.</span><span class="sxs-lookup"><span data-stu-id="f1fba-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="f1fba-126">Habilite esses recursos após fazer logon no NuGet.org, na página **Configurações de conta**.</span><span class="sxs-lookup"><span data-stu-id="f1fba-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="f1fba-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "Segurança da conta do NuGet")</span><span class="sxs-lookup"><span data-stu-id="f1fba-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="f1fba-128">✔️ usar um conta Microsoft para entrar no NuGet.</span><span class="sxs-lookup"><span data-stu-id="f1fba-128">✔️ DO use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="f1fba-129">✔️ habilitar a autenticação de dois fatores para acessar o NuGet.</span><span class="sxs-lookup"><span data-stu-id="f1fba-129">✔️ DO enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="f1fba-130">✔️ habilitar a notificação por email quando um pacote for publicado.</span><span class="sxs-lookup"><span data-stu-id="f1fba-130">✔️ DO enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f1fba-131">[Anterior](sourcelink.md)
>[Próximo](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="f1fba-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>
