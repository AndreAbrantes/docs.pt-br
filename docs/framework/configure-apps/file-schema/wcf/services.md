---
title: "&lt;serviços&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a2e0d810068db6409bc7b0fd1443a41c3d3ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="5b32e-102">&lt;serviços&gt;</span><span class="sxs-lookup"><span data-stu-id="5b32e-102">&lt;services&gt;</span></span>
<span data-ttu-id="5b32e-103">Os serviços são definidos no `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5b32e-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="5b32e-104">Cada serviço tem seu próprio `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="5b32e-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="5b32e-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5b32e-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b32e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b32e-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b32e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5b32e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5b32e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5b32e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b32e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5b32e-109">Attributes</span></span>  
 <span data-ttu-id="5b32e-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5b32e-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b32e-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5b32e-111">Child Elements</span></span>  
  
|<span data-ttu-id="5b32e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b32e-112">Element</span></span>|<span data-ttu-id="5b32e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b32e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b32e-114">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="5b32e-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="5b32e-115">Defina o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="5b32e-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b32e-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5b32e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5b32e-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b32e-117">Element</span></span>|<span data-ttu-id="5b32e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b32e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b32e-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5b32e-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="5b32e-120">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5b32e-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b32e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b32e-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
