---
title: Autenticação no WCF
description: Saiba mais sobre vários mecanismos no WCF que fornecem autenticação, como autenticação do Windows, certificados X. 509 e nome de usuário e senha.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: e2334a8c024238f38e1c927a278a4e25e7dabd9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247532"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="f7b6f-103">Autenticação no WCF</span><span class="sxs-lookup"><span data-stu-id="f7b6f-103">Authentication in WCF</span></span>

<span data-ttu-id="f7b6f-104">Os tópicos a seguir mostram vários mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, autenticação do Windows, certificados X. 509 e nome de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="f7b6f-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7b6f-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f7b6f-105">In This Section</span></span>  

 [<span data-ttu-id="f7b6f-106">Como: usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f7b6f-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="f7b6f-107">Os recursos do ASP.NET incluem uma associação e um provedor de função, um banco de dados para armazenar pares de nome de usuário/senha para autenticação e funções de usuário para autorização.</span><span class="sxs-lookup"><span data-stu-id="f7b6f-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="f7b6f-108">Este tópico explica como os serviços WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.</span><span class="sxs-lookup"><span data-stu-id="f7b6f-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="f7b6f-109">Como: usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="f7b6f-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="f7b6f-110">Demonstra como integrar um validador de nome de usuário/senha personalizado.</span><span class="sxs-lookup"><span data-stu-id="f7b6f-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="f7b6f-111">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="f7b6f-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="f7b6f-112">Como uma proteção extra, um cliente pode autenticar o serviço especificando a *identidade* esperada do serviço.</span><span class="sxs-lookup"><span data-stu-id="f7b6f-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="f7b6f-113">Se a identidade esperada e a identidade retornada pelo serviço não corresponderem, a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="f7b6f-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="f7b6f-114">Negociação de segurança e tempo limite</span><span class="sxs-lookup"><span data-stu-id="f7b6f-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="f7b6f-115">Descreve como usar a <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Propriedade na <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.</span><span class="sxs-lookup"><span data-stu-id="f7b6f-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="f7b6f-116">Depurando erros de autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="f7b6f-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="f7b6f-117">Concentra-se em problemas comuns encontrados ao usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="f7b6f-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f7b6f-118">Referência</span><span class="sxs-lookup"><span data-stu-id="f7b6f-118">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="f7b6f-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f7b6f-119">Related Sections</span></span>  

 [<span data-ttu-id="f7b6f-120">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="f7b6f-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7b6f-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="f7b6f-121">See also</span></span>

- [<span data-ttu-id="f7b6f-122">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="f7b6f-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="f7b6f-123">[Modelo de segurança para o Windows Server app Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f7b6f-123">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
