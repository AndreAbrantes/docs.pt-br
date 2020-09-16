---
title: Federação e tokens emitidos
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: dffba51c1bf1aaffbed8725aafc96fd747cb31c6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559246"
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="3323c-102">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="3323c-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="3323c-103">Com o Windows Communication Foundation (WCF), você pode criar clientes que se comunicam de forma segura com os serviços que implementam as especificações de WS-Federation e WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="3323c-103">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="3323c-104">As especificações usam XML, SOAP e WSDL (Web Services Description Language) para fornecer mecanismos que habilitam a autenticação e a autorização entre territórios de confiança diferentes.</span><span class="sxs-lookup"><span data-stu-id="3323c-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3323c-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3323c-105">In This Section</span></span>  
 [<span data-ttu-id="3323c-106">Federação</span><span class="sxs-lookup"><span data-stu-id="3323c-106">Federation</span></span>](federation.md)  
 <span data-ttu-id="3323c-107">Fornece uma visão geral da Federação.</span><span class="sxs-lookup"><span data-stu-id="3323c-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="3323c-108">Federação e confiabilidade</span><span class="sxs-lookup"><span data-stu-id="3323c-108">Federation and Trust</span></span>](federation-and-trust.md)  
 <span data-ttu-id="3323c-109">Lista os problemas de design a serem considerados ao criar serviços ou clientes federados.</span><span class="sxs-lookup"><span data-stu-id="3323c-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="3323c-110">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="3323c-110">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)  
 <span data-ttu-id="3323c-111">Descreve as noções básicas de criação de um cliente federado com o WCF.</span><span class="sxs-lookup"><span data-stu-id="3323c-111">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="3323c-112">Como: configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="3323c-112">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="3323c-113">Descreve as etapas de criação de um serviço federado.</span><span class="sxs-lookup"><span data-stu-id="3323c-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="3323c-114">Como: criar uma WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3323c-114">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="3323c-115">Descreve como configurar clientes e serviços que usam o `WSFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="3323c-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="3323c-116">Como: criar um serviço de token de segurança</span><span class="sxs-lookup"><span data-stu-id="3323c-116">How to: Create a Security Token Service</span></span>](how-to-create-a-security-token-service.md)  
 <span data-ttu-id="3323c-117">Descreve as etapas de criação de um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="3323c-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="3323c-118">Declarações e tokens de SAML (Security Assertions Markup Language)</span><span class="sxs-lookup"><span data-stu-id="3323c-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](saml-tokens-and-claims.md)  
 <span data-ttu-id="3323c-119">Descreve os tokens SAML (Security Asserties Markup Language), que são extensíveis e permitem que você crie tipos de declaração avançados.</span><span class="sxs-lookup"><span data-stu-id="3323c-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="3323c-120">Como: configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="3323c-120">How to: Configure a Local Issuer</span></span>](how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="3323c-121">Descreve como criar um emissor local de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="3323c-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="3323c-122">Como: desabilitar sessões seguras em uma WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3323c-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="3323c-123">Descreve como desabilitar sessões seguras em um `WSFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="3323c-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="3323c-124">A desabilitação de sessões seguras é necessária ao criar um Web farm que requer uma sessão para cada cliente.</span><span class="sxs-lookup"><span data-stu-id="3323c-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3323c-125">Referência</span><span class="sxs-lookup"><span data-stu-id="3323c-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="3323c-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="3323c-126">See also</span></span>

- [<span data-ttu-id="3323c-127">Autorização</span><span class="sxs-lookup"><span data-stu-id="3323c-127">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="3323c-128">Tokens personalizados</span><span class="sxs-lookup"><span data-stu-id="3323c-128">Custom Tokens</span></span>](../extending/custom-tokens.md)
- <span data-ttu-id="3323c-129">[Modelo de segurança para o Windows Server app Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3323c-129">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
