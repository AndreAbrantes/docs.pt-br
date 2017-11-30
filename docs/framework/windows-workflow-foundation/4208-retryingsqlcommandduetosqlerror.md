---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01db76802b96bd32e8a01cf86b1e682defe97a06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="9ce89-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="9ce89-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="9ce89-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9ce89-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ce89-104">ID</span><span class="sxs-lookup"><span data-stu-id="9ce89-104">ID</span></span>|<span data-ttu-id="9ce89-105">4208</span><span class="sxs-lookup"><span data-stu-id="9ce89-105">4208</span></span>|  
|<span data-ttu-id="9ce89-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="9ce89-106">Keywords</span></span>|<span data-ttu-id="9ce89-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="9ce89-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="9ce89-108">Nível</span><span class="sxs-lookup"><span data-stu-id="9ce89-108">Level</span></span>|<span data-ttu-id="9ce89-109">Informações</span><span class="sxs-lookup"><span data-stu-id="9ce89-109">Information</span></span>|  
|<span data-ttu-id="9ce89-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9ce89-110">Channel</span></span>|<span data-ttu-id="9ce89-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="9ce89-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ce89-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ce89-112">Description</span></span>  
 <span data-ttu-id="9ce89-113">Indica que o provedor SQL é experimentando de novo um comando SQL devido a um erro SQL.</span><span class="sxs-lookup"><span data-stu-id="9ce89-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ce89-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="9ce89-114">Message</span></span>  
 <span data-ttu-id="9ce89-115">Experimentando de novo um comando SQL por causa do erro número %1. SQL.</span><span class="sxs-lookup"><span data-stu-id="9ce89-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ce89-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9ce89-116">Details</span></span>  
  
|<span data-ttu-id="9ce89-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="9ce89-117">Data Item Name</span></span>|<span data-ttu-id="9ce89-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="9ce89-118">Data Item Type</span></span>|<span data-ttu-id="9ce89-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ce89-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ce89-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="9ce89-120">ErrorNumber</span></span>|<span data-ttu-id="9ce89-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ce89-121">xs:string</span></span>|<span data-ttu-id="9ce89-122">O número do erro SQL.</span><span class="sxs-lookup"><span data-stu-id="9ce89-122">The SQL error number.</span></span>|  
|<span data-ttu-id="9ce89-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ce89-123">AppDomain</span></span>|<span data-ttu-id="9ce89-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ce89-124">xs:string</span></span>|<span data-ttu-id="9ce89-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9ce89-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
