---
title: Tabela de decisões. Estruturas .NET a serem usadas para o Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Tabela de decisões, estruturas .NET a serem usadas para o Docker
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675813"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="d6109-104">Tabela de decisões: estruturas .NET a serem usadas para o Docker</span><span class="sxs-lookup"><span data-stu-id="d6109-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="d6109-105">A tabela de decisão a seguir resume se deve-se usar o .NET Framework ou o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6109-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="d6109-106">Lembre-se de que, para contêineres Linux, são necessários hosts do Docker baseados em Linux (VMs ou servidores) e de que, para contêineres do Windows, são necessários hosts do Docker baseados em Windows Server (VMs ou servidores).</span><span class="sxs-lookup"><span data-stu-id="d6109-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6109-107">Os computadores de desenvolvimento executarão um host Docker, seja Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="d6109-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="d6109-108">Microsserviços relacionados que você deseja executar e testar em conjunto em uma solução precisarão ser executados na mesma plataforma de contêiner.</span><span class="sxs-lookup"><span data-stu-id="d6109-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="d6109-109"><strong>Arquitetura/tipo de aplicativo</strong></span><span class="sxs-lookup"><span data-stu-id="d6109-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="d6109-110"><strong>Contêineres do Linux</strong></span><span class="sxs-lookup"><span data-stu-id="d6109-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="d6109-111"><strong>Contêineres do Windows</strong></span><span class="sxs-lookup"><span data-stu-id="d6109-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="d6109-112">Microsserviços em contêineres</span><span class="sxs-lookup"><span data-stu-id="d6109-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="d6109-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-113">.NET Core</span></span></td>
<td><span data-ttu-id="d6109-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="d6109-115">Aplicativo monolítico</span><span class="sxs-lookup"><span data-stu-id="d6109-115">Monolithic app</span></span></td>
<td><span data-ttu-id="d6109-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="d6109-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6109-117">.NET Framework</span></span></p>
<p><span data-ttu-id="d6109-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="d6109-119">Melhores desempenho e escalabilidade da categoria</span><span class="sxs-lookup"><span data-stu-id="d6109-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="d6109-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-120">.NET Core</span></span></td>
<td><span data-ttu-id="d6109-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="d6109-122">Migração do aplicativo herdado do Windows Server ("campo-marrom") para contêineres</span><span class="sxs-lookup"><span data-stu-id="d6109-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="d6109-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6109-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="d6109-124">Novo desenvolvimento baseado em contêiner ("campo-verde")</span><span class="sxs-lookup"><span data-stu-id="d6109-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="d6109-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-125">.NET Core</span></span></td>
<td><span data-ttu-id="d6109-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="d6109-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="d6109-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="d6109-129">.NET Core (recomendado)</span><span class="sxs-lookup"><span data-stu-id="d6109-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="d6109-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6109-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="d6109-131">ASP.NET 4 (MVC 5, API Web 2 e Web Forms)</span><span class="sxs-lookup"><span data-stu-id="d6109-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="d6109-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6109-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="d6109-133">Serviços SignalR</span><span class="sxs-lookup"><span data-stu-id="d6109-133">SignalR services</span></span></td>
<td><span data-ttu-id="d6109-134">.NET Core 2.1 ou versão posterior</span><span class="sxs-lookup"><span data-stu-id="d6109-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="d6109-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6109-135">.NET Framework</span></span></p>
<p><span data-ttu-id="d6109-136">.NET Core 2.1 ou versão posterior</span><span class="sxs-lookup"><span data-stu-id="d6109-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="d6109-137">WCF, WF e outras estruturas herdadas</span><span class="sxs-lookup"><span data-stu-id="d6109-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="d6109-138">WCF no .NET Core (somente a biblioteca de clientes WCF)</span><span class="sxs-lookup"><span data-stu-id="d6109-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="d6109-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6109-139">.NET Framework</span></span></p>
<p><span data-ttu-id="d6109-140">WCF no .NET Core (somente a biblioteca de clientes WCF)</span><span class="sxs-lookup"><span data-stu-id="d6109-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="d6109-141">Consumo de serviços do Azure</span><span class="sxs-lookup"><span data-stu-id="d6109-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="d6109-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-142">.NET Core</span></span></p>
<p><span data-ttu-id="d6109-143">(eventualmente todos os serviços do Azure fornecerão SDKs do cliente para o .NET Core)</span><span class="sxs-lookup"><span data-stu-id="d6109-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="d6109-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6109-144">.NET Framework</span></span></p>
<p><span data-ttu-id="d6109-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d6109-145">.NET Core</span></span></p>
<p><span data-ttu-id="d6109-146">(eventualmente todos os serviços do Azure fornecerão SDKs do cliente para o .NET Core)</span><span class="sxs-lookup"><span data-stu-id="d6109-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="d6109-147">[Anterior](net-framework-container-scenarios.md)
>[Próximo](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="d6109-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>