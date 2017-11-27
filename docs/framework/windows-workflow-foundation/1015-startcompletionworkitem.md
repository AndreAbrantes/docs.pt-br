---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7457b65f81e9e26b9de6055df474a83ce4264846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="cd581-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="cd581-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="cd581-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="cd581-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd581-104">ID</span><span class="sxs-lookup"><span data-stu-id="cd581-104">ID</span></span>|<span data-ttu-id="cd581-105">1015</span><span class="sxs-lookup"><span data-stu-id="cd581-105">1015</span></span>|  
|<span data-ttu-id="cd581-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="cd581-106">Keywords</span></span>|<span data-ttu-id="cd581-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cd581-107">WFRuntime</span></span>|  
|<span data-ttu-id="cd581-108">Nível</span><span class="sxs-lookup"><span data-stu-id="cd581-108">Level</span></span>|<span data-ttu-id="cd581-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="cd581-109">Verbose</span></span>|  
|<span data-ttu-id="cd581-110">Canal</span><span class="sxs-lookup"><span data-stu-id="cd581-110">Channel</span></span>|<span data-ttu-id="cd581-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="cd581-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cd581-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd581-112">Description</span></span>  
 <span data-ttu-id="cd581-113">Indica que um CompletionWorkItem está sendo a execução.</span><span class="sxs-lookup"><span data-stu-id="cd581-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cd581-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="cd581-114">Message</span></span>  
 <span data-ttu-id="cd581-115">Iniciar a execução de um CompletionWorkItem para atividades pai “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="cd581-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="cd581-116">Atividade counting “%4 ", DisplayName: “%5", InstanceId: “%6".</span><span class="sxs-lookup"><span data-stu-id="cd581-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cd581-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="cd581-117">Details</span></span>  
  
|<span data-ttu-id="cd581-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="cd581-118">Data Item Name</span></span>|<span data-ttu-id="cd581-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="cd581-119">Data Item Type</span></span>|<span data-ttu-id="cd581-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd581-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cd581-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="cd581-121">ParentActivity</span></span>|<span data-ttu-id="cd581-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="cd581-122">xs:string</span></span>|<span data-ttu-id="cd581-123">O nome do tipo de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="cd581-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="cd581-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="cd581-124">ParentDisplayName</span></span>|<span data-ttu-id="cd581-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="cd581-125">xs:string</span></span>|<span data-ttu-id="cd581-126">O nome para exibição de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="cd581-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="cd581-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="cd581-127">ParentInstanceId</span></span>|<span data-ttu-id="cd581-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="cd581-128">xs:string</span></span>|<span data-ttu-id="cd581-129">A identificação de instância de atividade pai.</span><span class="sxs-lookup"><span data-stu-id="cd581-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="cd581-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="cd581-130">CompletedActivity</span></span>|<span data-ttu-id="cd581-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="cd581-131">xs:string</span></span>|<span data-ttu-id="cd581-132">O nome do tipo de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="cd581-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="cd581-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="cd581-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="cd581-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="cd581-134">xs:string</span></span>|<span data-ttu-id="cd581-135">O nome para exibição de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="cd581-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="cd581-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="cd581-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="cd581-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="cd581-137">xs:string</span></span>|<span data-ttu-id="cd581-138">A identificação de instância de atividade concluída.</span><span class="sxs-lookup"><span data-stu-id="cd581-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="cd581-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cd581-139">AppDomain</span></span>|<span data-ttu-id="cd581-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="cd581-140">xs:string</span></span>|<span data-ttu-id="cd581-141">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cd581-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
