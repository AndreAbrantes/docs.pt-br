---
title: Porta do .NET Framework para o .NET Core
description: Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: b5b010acbccf134afe800aa5bb98a0ae6e9ffa25
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777357"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a><span data-ttu-id="110fa-103">Visão geral da portabilidade do .NET Framework para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="110fa-103">Overview of porting from .NET Framework to .NET Core</span></span>

<span data-ttu-id="110fa-104">Você pode ter um código que atualmente é executado no .NET Framework que você está interessado em portar para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="110fa-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="110fa-105">Esse artigo fornece:</span><span class="sxs-lookup"><span data-stu-id="110fa-105">This article provides:</span></span>

* <span data-ttu-id="110fa-106">Uma visão geral do processo de portabilidade.</span><span class="sxs-lookup"><span data-stu-id="110fa-106">An overview of the porting process.</span></span>
* <span data-ttu-id="110fa-107">Uma lista de ferramentas que você pode achar útil quando está portando seu código para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="110fa-107">A list of tools that you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="110fa-108">Visão geral do processo de portabilidade</span><span class="sxs-lookup"><span data-stu-id="110fa-108">Overview of the porting process</span></span>

<span data-ttu-id="110fa-109">Recomendamos que você use o seguinte processo ao portar seu projeto para o .NET Core:</span><span class="sxs-lookup"><span data-stu-id="110fa-109">We recommend you use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="110fa-110">Redirecione todos os projetos que você deseja que a porta direcione .NET Framework 4.7.2 ou superior.</span><span class="sxs-lookup"><span data-stu-id="110fa-110">Retarget all projects you wish to port to target .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="110fa-111">Essa etapa garante que você possa usar alternativas de API para destinos específicos do .NET Framework quando o .NET Core não oferecer suporte a determinada API.</span><span class="sxs-lookup"><span data-stu-id="110fa-111">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

2. <span data-ttu-id="110fa-112">Use o [.net Portability Analyzer](../../standard/analyzers/portability-analyzer.md) para analisar seus assemblies e ver se eles são portáteis para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="110fa-112">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="110fa-113">A ferramenta Analisador de portabilidade de API analisa os assemblies compilados e gera um relatório.</span><span class="sxs-lookup"><span data-stu-id="110fa-113">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="110fa-114">Este relatório mostra um resumo de portabilidade de alto nível e uma análise de cada API que você está usando e que não está disponível no núcleo da rede.</span><span class="sxs-lookup"><span data-stu-id="110fa-114">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span>

3. <span data-ttu-id="110fa-115">Instale o [.NET API Analyzer](../../standard/analyzers/api-analyzer.md) em seus projetos para identificar as APIs que geram <xref:System.PlatformNotSupportedException> em algumas plataformas e outros problemas de compatibilidade em potencial.</span><span class="sxs-lookup"><span data-stu-id="110fa-115">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs throwing <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="110fa-116">Essa ferramenta é semelhante ao analisador de portabilidade, mas em vez de analisar se as coisas podem ser criadas no .NET Core, ele analisa se você está usando uma API de uma forma que gerará o <xref:System.PlatformNotSupportedException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="110fa-116">This tool is similar to the portability analyzer, but instead of analyzing if things can build on .NET Core, it analyzes if you're using an API in a way that will throw the <xref:System.PlatformNotSupportedException> at run time.</span></span> <span data-ttu-id="110fa-117">Embora isso não seja comum se você estiver mudando de .NET Framework 4.7.2 ou superior, é bom verificar.</span><span class="sxs-lookup"><span data-stu-id="110fa-117">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span>

4. <span data-ttu-id="110fa-118">Converta todas as suas dependências de `packages.config` para o formato [PackageReference](/nuget/consume-packages/package-references-in-project-files) com a [ferramenta de conversão no Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="110fa-118">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="110fa-119">Esta etapa envolve a conversão de suas dependências do formato herdado `packages.config`.</span><span class="sxs-lookup"><span data-stu-id="110fa-119">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="110fa-120">`packages.config` não funciona no .NET Core, portanto, essa conversão será necessária se você tiver dependências de pacote.</span><span class="sxs-lookup"><span data-stu-id="110fa-120">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span>

5. <span data-ttu-id="110fa-121">Crie novos projetos para o .NET Core e copie sobre os arquivos de origem ou tente converter o arquivo de projeto existente com uma ferramenta.</span><span class="sxs-lookup"><span data-stu-id="110fa-121">Create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="110fa-122">O .NET Core usa um formato de arquivo de [projeto](../tools/csproj.md) simplificado (e diferente) do que o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="110fa-122">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="110fa-123">Você precisará converter os arquivos de projeto nesse formato para continuar.</span><span class="sxs-lookup"><span data-stu-id="110fa-123">You'll need to convert your project files into this format to continue.</span></span>

6. <span data-ttu-id="110fa-124">Portar seu código de teste.</span><span class="sxs-lookup"><span data-stu-id="110fa-124">Port your test code.</span></span>

   <span data-ttu-id="110fa-125">Como a portabilidade para o .NET Core é uma alteração significativa na base de código, é altamente recomendável portar seus projetos de teste para que você possa executar testes à medida que você portar seu código.</span><span class="sxs-lookup"><span data-stu-id="110fa-125">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to port your test projects so that you can run tests as you port your code over.</span></span> <span data-ttu-id="110fa-126">MSTest, xUnit e NUnit funcionam no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="110fa-126">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

<span data-ttu-id="110fa-127">Além disso, você pode tentar portar soluções menores ou projetos individuais em uma operação para o formato de arquivo de projeto do .NET Core com a ferramenta [dotnet try-Convert](https://github.com/dotnet/try-convert) .</span><span class="sxs-lookup"><span data-stu-id="110fa-127">Additionally, you can attempt to port smaller solutions or individual projects in one operation to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool.</span></span> <span data-ttu-id="110fa-128">Não há garantia de que o `dotnet try-convert` funcione para todos os seus projetos e pode causar alterações sutis no comportamento que você dependou.</span><span class="sxs-lookup"><span data-stu-id="110fa-128">`dotnet try-convert` is not guaranteed to work for all your projects, and it may cause subtle changes in behavior that you depended on.</span></span> <span data-ttu-id="110fa-129">Use-o como um _ponto de partida_ que automatize as coisas básicas que podem ser automatizadas.</span><span class="sxs-lookup"><span data-stu-id="110fa-129">Use it as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="110fa-130">Não é uma solução garantida para migrar um projeto.</span><span class="sxs-lookup"><span data-stu-id="110fa-130">It isn't a guaranteed solution to migrating a project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="110fa-131">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="110fa-131">Next steps</span></span>

>[!div class="nextstepaction"]
>[<span data-ttu-id="110fa-132">Tecnologias indisponíveis no .NET Core</span><span class="sxs-lookup"><span data-stu-id="110fa-132">Unavailable technologies on .NET Core</span></span>](net-framework-tech-unavailable.md)
