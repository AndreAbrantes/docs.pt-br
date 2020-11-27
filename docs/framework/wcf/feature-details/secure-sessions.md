---
title: Sessões seguras
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: fd8406af0c37981b2ddc7ab8ddb0c82c63cbc0b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288535"
---
# <a name="secure-sessions"></a><span data-ttu-id="21a82-102">Sessões seguras</span><span class="sxs-lookup"><span data-stu-id="21a82-102">Secure Sessions</span></span>

<span data-ttu-id="21a82-103">Um recurso do Windows Communication Foundation (WCF) é uma sessão confiável que garante que as mensagens sejam recebidas na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="21a82-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="21a82-104">Os tópicos nesta seção discutem as implicações de segurança a serem consideradas ao criar uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="21a82-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="21a82-105">Para obter mais informações sobre sessões confiáveis, consulte [usando sessões](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="21a82-105">For more information about reliable sessions, see [Using Sessions](../using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21a82-106">Quando a representação é necessária no Windows XP, use uma sessão segura sem um símbolo de contexto de segurança com estado (SCT).</span><span class="sxs-lookup"><span data-stu-id="21a82-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="21a82-107">Quando SCTs com estado são usados com representação, um <xref:System.InvalidOperationException> é gerado.</span><span class="sxs-lookup"><span data-stu-id="21a82-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="21a82-108">Para obter mais informações, consulte [cenários sem suporte](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="21a82-108">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21a82-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="21a82-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="21a82-110">Sessões seguras e conversas seguras</span><span class="sxs-lookup"><span data-stu-id="21a82-110">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)|<span data-ttu-id="21a82-111">Conversas seguras e sessões seguras são sinônimos.</span><span class="sxs-lookup"><span data-stu-id="21a82-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="21a82-112">Este tópico explica como funciona uma conversa segura e quando e por que usar o padrão.</span><span class="sxs-lookup"><span data-stu-id="21a82-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="21a82-113">Como: criar uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="21a82-113">How to: Create a Secure Session</span></span>](how-to-create-a-secure-session.md)|<span data-ttu-id="21a82-114">Percorre as noções básicas da criação de uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="21a82-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="21a82-115">Como: criar um token de contexto de segurança para uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="21a82-115">How to: Create a Security Context Token for a Secure Session</span></span>](how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="21a82-116">Percorre as etapas de criação de um Web farm que manterá o estado e as sessões com clientes.</span><span class="sxs-lookup"><span data-stu-id="21a82-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="21a82-117">Considerações de segurança para sessões seguras</span><span class="sxs-lookup"><span data-stu-id="21a82-117">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)|<span data-ttu-id="21a82-118">Descreve considerações especiais para sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="21a82-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="21a82-119">Referência</span><span class="sxs-lookup"><span data-stu-id="21a82-119">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="21a82-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="21a82-120">Related Sections</span></span>  

 [<span data-ttu-id="21a82-121">Sessões,instanciação e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="21a82-121">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="21a82-122">Serviços de implantação e projeção</span><span class="sxs-lookup"><span data-stu-id="21a82-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="21a82-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="21a82-123">See also</span></span>

- [<span data-ttu-id="21a82-124">Como: habilitar a detecção de reprodução de mensagem</span><span class="sxs-lookup"><span data-stu-id="21a82-124">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="21a82-125">Ataques por repetição</span><span class="sxs-lookup"><span data-stu-id="21a82-125">Replay Attacks</span></span>](replay-attacks.md)
- [<span data-ttu-id="21a82-126">Como: criar um serviço que requer sessões</span><span class="sxs-lookup"><span data-stu-id="21a82-126">How to: Create a Service That Requires Sessions</span></span>](how-to-create-a-service-that-requires-sessions.md)
