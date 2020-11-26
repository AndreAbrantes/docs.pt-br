---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 1b63877998ea7942886c83d8795fe5ee49fdf053
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241922"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="2d8b7-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="2d8b7-102">220 - MessageSentToTransport</span></span>

## <a name="properties"></a><span data-ttu-id="2d8b7-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2d8b7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d8b7-104">ID</span><span class="sxs-lookup"><span data-stu-id="2d8b7-104">Id</span></span>|<span data-ttu-id="2d8b7-105">220</span><span class="sxs-lookup"><span data-stu-id="2d8b7-105">220</span></span>|  
|<span data-ttu-id="2d8b7-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="2d8b7-106">Keywords</span></span>|<span data-ttu-id="2d8b7-107">EndToEndMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2d8b7-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2d8b7-108">Nível</span><span class="sxs-lookup"><span data-stu-id="2d8b7-108">Level</span></span>|<span data-ttu-id="2d8b7-109">Informações do</span><span class="sxs-lookup"><span data-stu-id="2d8b7-109">Information</span></span>|  
|<span data-ttu-id="2d8b7-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2d8b7-110">Channel</span></span>|<span data-ttu-id="2d8b7-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="2d8b7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2d8b7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d8b7-112">Description</span></span>  

 <span data-ttu-id="2d8b7-113">Esse evento é emitido quando o modelo de serviço envia uma mensagem para o transporte.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d8b7-114">Esse evento não será emitido para transportes unidirecionais.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2d8b7-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="2d8b7-115">Message</span></span>  

 <span data-ttu-id="2d8b7-116">O Dispatcher enviou uma mensagem para o transporte.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="2d8b7-117">ID de correlação = = ' %1 '.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2d8b7-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2d8b7-118">Details</span></span>  
  
|<span data-ttu-id="2d8b7-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="2d8b7-119">Data Item Name</span></span>|<span data-ttu-id="2d8b7-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="2d8b7-120">Data Item Type</span></span>|<span data-ttu-id="2d8b7-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d8b7-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2d8b7-122">ID de Correlação</span><span class="sxs-lookup"><span data-stu-id="2d8b7-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="2d8b7-123">A ID da atividade usada para correlacionar um `MessageSentToTransport` evento de um serviço ou cliente ao seu correspondente `MessageReceivedFromTransport` no outro final.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="2d8b7-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="2d8b7-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="2d8b7-125">Para serviços hospedados na Web, esse campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2d8b7-126">Seu formato é definido como ' nome do site aplicativo caminho virtual&#124;serviço caminho virtual&#124;ServiceName '.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2d8b7-127">Exemplo: ' Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2d8b7-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2d8b7-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2d8b7-129">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2d8b7-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
