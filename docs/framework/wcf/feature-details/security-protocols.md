---
title: Protocolos de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], protocols
ms.assetid: 57ffcbea-807c-4e43-a41c-44b3db8ed2af
ms.openlocfilehash: 1455aeeeb759f8eb2cc09c8649a5cbd6843d950a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254006"
---
# <a name="security-protocols"></a><span data-ttu-id="d439b-102">Protocolos de segurança</span><span class="sxs-lookup"><span data-stu-id="d439b-102">Security Protocols</span></span>

<span data-ttu-id="d439b-103">Os protocolos especificação Web Services Security fornecem mecanismos de segurança de serviços da Web que abrangem todos os requisitos de segurança de mensagens empresariais existentes.</span><span class="sxs-lookup"><span data-stu-id="d439b-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="d439b-104">Esta seção descreve os detalhes de Windows Communication Foundation (WCF) (implementados no <xref:System.ServiceModel.Channels.SecurityBindingElement> ) para os seguintes protocolos de segurança de serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="d439b-104">This section describes the Windows Communication Foundation (WCF) details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="d439b-105">Especificação/documento</span><span class="sxs-lookup"><span data-stu-id="d439b-105">Specification/Document</span></span>|<span data-ttu-id="d439b-106">Link</span><span class="sxs-lookup"><span data-stu-id="d439b-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="d439b-107">WSS: segurança de mensagem SOAP 1,0</span><span class="sxs-lookup"><span data-stu-id="d439b-107">WSS: SOAP Message Security 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|  
|<span data-ttu-id="d439b-108">WSS: nome do perfil do token 1,0</span><span class="sxs-lookup"><span data-stu-id="d439b-108">WSS: Username Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|  
|<span data-ttu-id="d439b-109">WSS: perfil de token X509 1,0</span><span class="sxs-lookup"><span data-stu-id="d439b-109">WSS: X509 Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|  
|<span data-ttu-id="d439b-110">WSS: perfil de token 1,1 SAML 1,0</span><span class="sxs-lookup"><span data-stu-id="d439b-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|  
|<span data-ttu-id="d439b-111">WSS: segurança de mensagem SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="d439b-111">WSS: SOAP Message Security 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|  
|<span data-ttu-id="d439b-112">Perfil de token de nome de usuário do WSS 1,1</span><span class="sxs-lookup"><span data-stu-id="d439b-112">WSS Username Token Profile 1.1</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|  
|<span data-ttu-id="d439b-113">WSS: X. 509 o perfil de token 1,1</span><span class="sxs-lookup"><span data-stu-id="d439b-113">WSS: X.509 Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|  
|<span data-ttu-id="d439b-114">WSS: perfil de token Kerberos 1,1</span><span class="sxs-lookup"><span data-stu-id="d439b-114">WSS: Kerberos Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|  
|<span data-ttu-id="d439b-115">WSS: perfil de token 1,1 SAML 1,1</span><span class="sxs-lookup"><span data-stu-id="d439b-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|  
|<span data-ttu-id="d439b-116">WS-Secure conversa 1,3</span><span class="sxs-lookup"><span data-stu-id="d439b-116">WS-Secure Conversation 1.3</span></span>|<http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512/ws-secureconversation-1.3-os.pdf>|  
|<span data-ttu-id="d439b-117">WS-Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="d439b-117">WS-Trust 1.3</span></span>|<http://docs.oasis-open.org/ws-sx/ws-trust/200512/ws-trust-1.3-os.pdf>|  
|<span data-ttu-id="d439b-118">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d439b-118">Application Note:</span></span><br /><br /> <span data-ttu-id="d439b-119">Usando WS-Trust para handshake de TLS</span><span class="sxs-lookup"><span data-stu-id="d439b-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="d439b-120">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="d439b-120">To be published</span></span>|  
|<span data-ttu-id="d439b-121">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d439b-121">Application Note:</span></span><br /><br /> <span data-ttu-id="d439b-122">Usando WS-Trust para SPNEGO</span><span class="sxs-lookup"><span data-stu-id="d439b-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="d439b-123">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="d439b-123">To be published</span></span>|  
|<span data-ttu-id="d439b-124">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d439b-124">Application Note:</span></span><br /><br /> <span data-ttu-id="d439b-125">Serviços Web que endereçam referências e identidades de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="d439b-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="d439b-126">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="d439b-126">To be published</span></span>|  
|<span data-ttu-id="d439b-127">WS-SecurityPolicy 1,2 (2007/04)</span><span class="sxs-lookup"><span data-stu-id="d439b-127">WS-SecurityPolicy 1.2 (2007/04)</span></span>|<http://www.oasis-open.org/committees/download.php/23821/ws-securitypolicy-1.2-spec-cs.pdf>|  
  
 <span data-ttu-id="d439b-128">O WCF, versão 1, fornece 17 modos de autenticação que podem ser usados como base para a configuração de segurança de serviços Web.</span><span class="sxs-lookup"><span data-stu-id="d439b-128">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="d439b-129">Cada modo é otimizado para um conjunto comum de requisitos de implantação, como:</span><span class="sxs-lookup"><span data-stu-id="d439b-129">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="d439b-130">Credenciais usadas para autenticar o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="d439b-130">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="d439b-131">Mecanismos de proteção de segurança de mensagens ou transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-131">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="d439b-132">Padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d439b-132">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="d439b-133">Modo de autenticação</span><span class="sxs-lookup"><span data-stu-id="d439b-133">Authentication Mode</span></span>|<span data-ttu-id="d439b-134">Autenticação de cliente</span><span class="sxs-lookup"><span data-stu-id="d439b-134">Client Authentication</span></span>|<span data-ttu-id="d439b-135">Autenticação do servidor</span><span class="sxs-lookup"><span data-stu-id="d439b-135">Server Authentication</span></span>|<span data-ttu-id="d439b-136">Mode</span><span class="sxs-lookup"><span data-stu-id="d439b-136">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="d439b-137">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-137">UserNameOverTransport</span></span>|<span data-ttu-id="d439b-138">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="d439b-138">User name/password</span></span>|<span data-ttu-id="d439b-139">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-139">X509</span></span>|<span data-ttu-id="d439b-140">Transport</span><span class="sxs-lookup"><span data-stu-id="d439b-140">Transport</span></span>|  
|<span data-ttu-id="d439b-141">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-141">CertificateOverTransport</span></span>|<span data-ttu-id="d439b-142">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-142">X509</span></span>|<span data-ttu-id="d439b-143">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-143">X509</span></span>|<span data-ttu-id="d439b-144">Transport</span><span class="sxs-lookup"><span data-stu-id="d439b-144">Transport</span></span>|  
|<span data-ttu-id="d439b-145">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-145">KerberosOverTransport</span></span>|<span data-ttu-id="d439b-146">Windows</span><span class="sxs-lookup"><span data-stu-id="d439b-146">Windows</span></span>|<span data-ttu-id="d439b-147">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-147">X509</span></span>|<span data-ttu-id="d439b-148">Transport</span><span class="sxs-lookup"><span data-stu-id="d439b-148">Transport</span></span>|  
|<span data-ttu-id="d439b-149">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-149">IssuedTokenOverTransport</span></span>|<span data-ttu-id="d439b-150">Federado</span><span class="sxs-lookup"><span data-stu-id="d439b-150">Federated</span></span>|<span data-ttu-id="d439b-151">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-151">X509</span></span>|<span data-ttu-id="d439b-152">Transport</span><span class="sxs-lookup"><span data-stu-id="d439b-152">Transport</span></span>|  
|<span data-ttu-id="d439b-153">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-153">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="d439b-154">Windows SSPI negociado</span><span class="sxs-lookup"><span data-stu-id="d439b-154">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d439b-155">Windows SSPI negociado</span><span class="sxs-lookup"><span data-stu-id="d439b-155">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d439b-156">Transport</span><span class="sxs-lookup"><span data-stu-id="d439b-156">Transport</span></span>|  
|<span data-ttu-id="d439b-157">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="d439b-157">AnonymousForCertificate</span></span>|<span data-ttu-id="d439b-158">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d439b-158">None</span></span>|<span data-ttu-id="d439b-159">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-159">X509</span></span>|<span data-ttu-id="d439b-160">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-160">Message</span></span>|  
|<span data-ttu-id="d439b-161">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="d439b-161">UserNameForCertificate</span></span>|<span data-ttu-id="d439b-162">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="d439b-162">User name/password</span></span>|<span data-ttu-id="d439b-163">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-163">X509</span></span>|<span data-ttu-id="d439b-164">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-164">Message</span></span>|  
|<span data-ttu-id="d439b-165">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="d439b-165">MutualCertificate</span></span>|<span data-ttu-id="d439b-166">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-166">X509</span></span>|<span data-ttu-id="d439b-167">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-167">X509</span></span>|<span data-ttu-id="d439b-168">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-168">Message</span></span>|  
|<span data-ttu-id="d439b-169">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="d439b-169">MutualCertificateDuplex</span></span>|<span data-ttu-id="d439b-170">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-170">X509</span></span>|<span data-ttu-id="d439b-171">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-171">X509</span></span>|<span data-ttu-id="d439b-172">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-172">Message</span></span>|  
|<span data-ttu-id="d439b-173">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="d439b-173">IssuedTokenForCertificate</span></span>|<span data-ttu-id="d439b-174">Federado</span><span class="sxs-lookup"><span data-stu-id="d439b-174">Federated</span></span>|<span data-ttu-id="d439b-175">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-175">X509</span></span>|<span data-ttu-id="d439b-176">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-176">Message</span></span>|  
|<span data-ttu-id="d439b-177">Kerberos</span><span class="sxs-lookup"><span data-stu-id="d439b-177">Kerberos</span></span>|<span data-ttu-id="d439b-178">Windows</span><span class="sxs-lookup"><span data-stu-id="d439b-178">Windows</span></span>|<span data-ttu-id="d439b-179">Windows</span><span class="sxs-lookup"><span data-stu-id="d439b-179">Windows</span></span>|<span data-ttu-id="d439b-180">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-180">Message</span></span>|  
|<span data-ttu-id="d439b-181">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="d439b-181">IssuedToken</span></span>|<span data-ttu-id="d439b-182">Federado</span><span class="sxs-lookup"><span data-stu-id="d439b-182">Federated</span></span>|<span data-ttu-id="d439b-183">Federado</span><span class="sxs-lookup"><span data-stu-id="d439b-183">Federated</span></span>|<span data-ttu-id="d439b-184">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-184">Message</span></span>|  
|<span data-ttu-id="d439b-185">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-185">SspiNegotiated</span></span>|<span data-ttu-id="d439b-186">Windows SSPI negociado</span><span class="sxs-lookup"><span data-stu-id="d439b-186">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d439b-187">Windows SSPI negociado</span><span class="sxs-lookup"><span data-stu-id="d439b-187">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d439b-188">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-188">Message</span></span>|  
|<span data-ttu-id="d439b-189">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-189">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="d439b-190">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d439b-190">None</span></span>|<span data-ttu-id="d439b-191">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="d439b-191">X509, TLS-Nego</span></span>|<span data-ttu-id="d439b-192">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-192">Message</span></span>|  
|<span data-ttu-id="d439b-193">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-193">UserNameForSslNegotiated</span></span>|<span data-ttu-id="d439b-194">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="d439b-194">User name/password</span></span>|<span data-ttu-id="d439b-195">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="d439b-195">X509, TLS-Nego</span></span>|<span data-ttu-id="d439b-196">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-196">Message</span></span>|  
|<span data-ttu-id="d439b-197">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-197">MutualSslNegotiated</span></span>|<span data-ttu-id="d439b-198">X509</span><span class="sxs-lookup"><span data-stu-id="d439b-198">X509</span></span>|<span data-ttu-id="d439b-199">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="d439b-199">X509, TLS-Nego</span></span>|<span data-ttu-id="d439b-200">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-200">Message</span></span>|  
|<span data-ttu-id="d439b-201">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-201">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="d439b-202">Federado</span><span class="sxs-lookup"><span data-stu-id="d439b-202">Federated</span></span>|<span data-ttu-id="d439b-203">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="d439b-203">X509, TLS-Nego</span></span>|<span data-ttu-id="d439b-204">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d439b-204">Message</span></span>|  
  
 <span data-ttu-id="d439b-205">Os pontos de extremidade que usam esses modos de autenticação podem expressar seus requisitos de segurança usando o WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="d439b-205">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="d439b-206">Este documento descreve a estrutura de mensagens de cabeçalho e de infraestrutura de segurança para cada modo de autenticação e fornece exemplos de políticas e mensagens.</span><span class="sxs-lookup"><span data-stu-id="d439b-206">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="d439b-207">O WCF aproveita WS-SecureConversation para fornecer suporte a sessões seguras para proteger as trocas de várias mensagens entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d439b-207">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="d439b-208">Consulte "sessões seguras" abaixo para obter detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="d439b-208">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="d439b-209">Além dos modos de autenticação, o WCF fornece configurações para controlar mecanismos de proteção comuns que se aplicam à maioria dos modos de autenticação baseados em segurança de mensagem, por exemplo: ordem de assinatura versus operações de criptografia, conjuntos de algoritmos, derivação de chave e confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="d439b-209">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="d439b-210">Os seguintes prefixos e namespaces são usados neste documento.</span><span class="sxs-lookup"><span data-stu-id="d439b-210">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="d439b-211">Prefixo</span><span class="sxs-lookup"><span data-stu-id="d439b-211">Prefix</span></span>|<span data-ttu-id="d439b-212">Namespace</span><span class="sxs-lookup"><span data-stu-id="d439b-212">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="d439b-213">s</span><span class="sxs-lookup"><span data-stu-id="d439b-213">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|  
|<span data-ttu-id="d439b-214">sp</span><span class="sxs-lookup"><span data-stu-id="d439b-214">sp</span></span>|`http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702`|  
|<span data-ttu-id="d439b-215">um</span><span class="sxs-lookup"><span data-stu-id="d439b-215">a</span></span>|`http://www.w3.org/2005/08/addressing`|  
|<span data-ttu-id="d439b-216">wsse</span><span class="sxs-lookup"><span data-stu-id="d439b-216">wsse</span></span>|<span data-ttu-id="d439b-217">TBD – OASIS WSS 1,0 URI</span><span class="sxs-lookup"><span data-stu-id="d439b-217">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="d439b-218">wsse11</span><span class="sxs-lookup"><span data-stu-id="d439b-218">wsse11</span></span>|<span data-ttu-id="d439b-219">TBD – OASIS WSS 1,1 URI</span><span class="sxs-lookup"><span data-stu-id="d439b-219">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="d439b-220">wsu</span><span class="sxs-lookup"><span data-stu-id="d439b-220">wsu</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd`|  
|<span data-ttu-id="d439b-221">AD</span><span class="sxs-lookup"><span data-stu-id="d439b-221">ds</span></span>|<span data-ttu-id="d439b-222">TBD – URI de XMLDSig do W3C</span><span class="sxs-lookup"><span data-stu-id="d439b-222">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="d439b-223">WST</span><span class="sxs-lookup"><span data-stu-id="d439b-223">wst</span></span>|<span data-ttu-id="d439b-224">TBD – WS-Trust URI 2005/02</span><span class="sxs-lookup"><span data-stu-id="d439b-224">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="d439b-225">wssc</span><span class="sxs-lookup"><span data-stu-id="d439b-225">wssc</span></span>|<span data-ttu-id="d439b-226">TBD – WS-SecureConversation URI 2005/02</span><span class="sxs-lookup"><span data-stu-id="d439b-226">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="d439b-227">wsaw</span><span class="sxs-lookup"><span data-stu-id="d439b-227">wsaw</span></span>|`http://www.w3.org/2006/05/addressing/wsdl`|  
|<span data-ttu-id="d439b-228">WSP</span><span class="sxs-lookup"><span data-stu-id="d439b-228">wsp</span></span>|`http://schemas.xmlsoap.org/ws/2004/09/policy`|  
|<span data-ttu-id="d439b-229">mssp</span><span class="sxs-lookup"><span data-stu-id="d439b-229">mssp</span></span>|`http://schemas.microsoft.com/ws/2005/07/securitypolicy`|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="d439b-230">1. perfis de token</span><span class="sxs-lookup"><span data-stu-id="d439b-230">1. Token Profiles</span></span>  

 <span data-ttu-id="d439b-231">As especificações de especificação Web Services Security representam credenciais como tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="d439b-231">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="d439b-232">O WCF dá suporte aos seguintes tipos de token:</span><span class="sxs-lookup"><span data-stu-id="d439b-232">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="d439b-233">UsernameToken 1,1</span><span class="sxs-lookup"><span data-stu-id="d439b-233">1.1 UsernameToken</span></span>  

 <span data-ttu-id="d439b-234">O WCF segue os perfis UsernameToken10 e UsernameToken11 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="d439b-234">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="d439b-235">O atributo R1101 Passwordtype no elemento UsernameToken\Password deve ser omitido ou ter um valor #PasswordText (padrão).</span><span class="sxs-lookup"><span data-stu-id="d439b-235">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="d439b-236">Uma delas pode implementar o #PasswordDigest usando a extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="d439b-236">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="d439b-237">Foi observado que #PasswordDigest muitas vezes estava confundido como um mecanismo seguro de proteção de senha.</span><span class="sxs-lookup"><span data-stu-id="d439b-237">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="d439b-238">Mas #PasswordDigest não pode servir como um substituto para a criptografia do UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="d439b-238">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="d439b-239">O objetivo principal do #PasswordDigest é a proteção contra ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="d439b-239">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="d439b-240">Nos modos de autenticação do WCF, a reprodução de ameaças de ataque é atenuada usando assinaturas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d439b-240">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="d439b-241">O WCF B1102 nunca emite um nonce e cria subelementos do UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="d439b-241">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="d439b-242">Esses subelementos destinam-se a ajudar a detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="d439b-242">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="d439b-243">Em vez disso, o WCF usa assinaturas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d439b-243">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="d439b-244">O perfil de UsernameToken de segurança de mensagem SOAP do WSS 1,1 (UsernameToken11) introduziu a derivação de chave do recurso de senha.</span><span class="sxs-lookup"><span data-stu-id="d439b-244">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="d439b-245">A senha do UsernameToken B1103 não deve ser usada para a derivação de chave e, portanto, para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="d439b-245">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="d439b-246">Lógica: as senhas geralmente são consideradas muito fracas para serem usadas para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="d439b-246">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="d439b-247">1,2 token X509</span><span class="sxs-lookup"><span data-stu-id="d439b-247">1.2 X509 Token</span></span>  

 <span data-ttu-id="d439b-248">O WCF dá suporte a certificados X509v3 como um tipo de credencial e segue o X509TokenProfile 1.0 e o X509TokenProfile 1.1 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="d439b-248">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="d439b-249">R1201 o atributo ValueType no elemento BinarySecurityToken deve ter valor #X509v3 quando ele contiver um certificado X509v3.</span><span class="sxs-lookup"><span data-stu-id="d439b-249">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="d439b-250">O perfil de token X509 do WSS 1,0 e 1,1 definem também #X509PKIPathv1 e #PKCS7 como tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="d439b-250">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="d439b-251">O WCF não oferece suporte a esses tipos.</span><span class="sxs-lookup"><span data-stu-id="d439b-251">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="d439b-252">R1202 se uma extensão SubjectKeyIdentifier (esqui) estiver presente em um certificado X509, wsse: KeyIdentifier deve ser usado para referências externas ao token, com o atributo ValueType como #X509SubjectKeyIdentifier e seu conteúdo, o valor codificado na base64 da extensão de esqui do certificado.</span><span class="sxs-lookup"><span data-stu-id="d439b-252">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="d439b-253">As referências de esqui são amplamente implementadas e comprovadas como um tipo de referência externa altamente interoperável.</span><span class="sxs-lookup"><span data-stu-id="d439b-253">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="d439b-254">R1203 uma referência externa ao token de segurança X509 não deve usar DS: X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="d439b-254">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="d439b-255">R1204 se o X509TokenProfile 1.1 estiver em uso, uma referência externa ao token de segurança X509 deverá usar a impressão digital introduzida pelo WS-Security 1,1.</span><span class="sxs-lookup"><span data-stu-id="d439b-255">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="d439b-256">O WCF dá suporte a X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="d439b-256">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="d439b-257">No entanto, há problemas de interoperabilidade com o X509IssuerSerial: o WCF usa uma cadeia de caracteres para comparar dois valores de X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="d439b-257">However there are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="d439b-258">Portanto, se um reordenar componentes do nome da entidade e enviar a um serviço WCF uma referência a um certificado, ele poderá não ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="d439b-258">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="d439b-259">Token Kerberos 1,3</span><span class="sxs-lookup"><span data-stu-id="d439b-259">1.3 Kerberos Token</span></span>  

 <span data-ttu-id="d439b-260">O WCF dá suporte ao KerberosTokenProfile 1.1 para fins de autenticação do Windows com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="d439b-260">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="d439b-261">R1301 um token Kerberos deve transportar o valor de um AP_REQ de Kerberos v4 encapsulado de GSS, conforme definido em GSS_API e a especificação de Kerberos, e deve ter o atributo ValueType com o valor #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="d439b-261">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="d439b-262">O WCF usa a GSS-REQ do Kerberos encapsulado no protocolo de autenticação, e não um ponto de acesso simples.</span><span class="sxs-lookup"><span data-stu-id="d439b-262">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="d439b-263">Essa é uma prática recomendada de segurança.</span><span class="sxs-lookup"><span data-stu-id="d439b-263">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="d439b-264">Token do SAML v 1.1 1,4</span><span class="sxs-lookup"><span data-stu-id="d439b-264">1.4 SAML v1.1 Token</span></span>  

 <span data-ttu-id="d439b-265">O WCF dá suporte a perfis de token SAML 1,0 e 1,1 para tokens SAML v 1.1.</span><span class="sxs-lookup"><span data-stu-id="d439b-265">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="d439b-266">É possível implementar outras versões de formatos de token SAML.</span><span class="sxs-lookup"><span data-stu-id="d439b-266">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="d439b-267">Token de contexto de segurança 1,5</span><span class="sxs-lookup"><span data-stu-id="d439b-267">1.5 Security Context Token</span></span>  

 <span data-ttu-id="d439b-268">O WCF dá suporte ao SCT (token de contexto de segurança) introduzido no WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="d439b-268">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="d439b-269">O SCT é usado para representar um contexto de segurança estabelecido no SecureConversation, bem como os protocolos de negociação binárias TLS e SSPI, descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="d439b-269">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="d439b-270">2. parâmetros de segurança de mensagem comum</span><span class="sxs-lookup"><span data-stu-id="d439b-270">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="d439b-271">2,1 carimbo de data/hora</span><span class="sxs-lookup"><span data-stu-id="d439b-271">2.1 TimeStamp</span></span>  

 <span data-ttu-id="d439b-272">A presença do carimbo de data/hora é controlada usando a <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> propriedade da <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="d439b-272">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="d439b-273">O WCF sempre serializa wsse: TimeStamp com wsse: created e wsse: expira campos.</span><span class="sxs-lookup"><span data-stu-id="d439b-273">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="d439b-274">O carimbo de data/hora wsse: sempre é assinado quando a assinatura é usada.</span><span class="sxs-lookup"><span data-stu-id="d439b-274">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="d439b-275">2,2 ordem de proteção</span><span class="sxs-lookup"><span data-stu-id="d439b-275">2.2 Protection Order</span></span>  

 <span data-ttu-id="d439b-276">O WCF dá suporte à ordem de proteção de mensagem "assinar antes de criptografar" e "criptografar antes de assinar" (política de segurança 1,2).</span><span class="sxs-lookup"><span data-stu-id="d439b-276">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.2).</span></span> <span data-ttu-id="d439b-277">A opção "assinar antes de criptografar" é recomendada por motivos, incluindo: mensagens protegidas com criptografar antes de assinar os ataques de substituição de assinatura, a menos que o mecanismo de SignatureConfirmation 1,1 seja usado, e uma assinatura sobre conteúdo criptografado torna WS-Security a auditoria mais difícil.</span><span class="sxs-lookup"><span data-stu-id="d439b-277">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="d439b-278">Proteção de assinatura 2,3</span><span class="sxs-lookup"><span data-stu-id="d439b-278">2.3 Signature Protection</span></span>  

 <span data-ttu-id="d439b-279">Quando o sinal de criptografia antes é usado, é recomendável proteger a assinatura para evitar ataques de força bruta para adivinhar o conteúdo criptografado ou a chave de assinatura (especialmente quando um token personalizado é usado com o material de chave fraco).</span><span class="sxs-lookup"><span data-stu-id="d439b-279">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="d439b-280">Pacote de algoritmos 2,4</span><span class="sxs-lookup"><span data-stu-id="d439b-280">2.4 Algorithm Suite</span></span>  

 <span data-ttu-id="d439b-281">O WCF dá suporte a todos os conjuntos de algoritmos listados na política de segurança 1,2.</span><span class="sxs-lookup"><span data-stu-id="d439b-281">WCF supports all algorithm suites listed in Security Policy 1.2.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="d439b-282">Derivação de chave 2,5</span><span class="sxs-lookup"><span data-stu-id="d439b-282">2.5 Key Derivation</span></span>  

 <span data-ttu-id="d439b-283">O WCF usa "derivação de chave para chaves simétricas", conforme descrito em WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="d439b-283">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="d439b-284">2,6 confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="d439b-284">2.6 Signature Confirmation</span></span>  

 <span data-ttu-id="d439b-285">A confirmação de assinatura pode ser usada como proteção contra ataques de Man intermediários para proteger o conjunto de assinaturas.</span><span class="sxs-lookup"><span data-stu-id="d439b-285">Signature confirmation can be used as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="d439b-286">Layout do cabeçalho de segurança 2,7</span><span class="sxs-lookup"><span data-stu-id="d439b-286">2.7 Security Header Layout</span></span>  

 <span data-ttu-id="d439b-287">Cada modo de autenticação descreve um determinado layout para o cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="d439b-287">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="d439b-288">Os elementos dentro do cabeçalho de segurança são semiordenados.</span><span class="sxs-lookup"><span data-stu-id="d439b-288">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="d439b-289">Para definir a ordem dos elementos filho do cabeçalho de segurança, WS-Security política define os seguintes modos de layout de cabeçalho de segurança:</span><span class="sxs-lookup"><span data-stu-id="d439b-289">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d439b-290">Rigoroso</span><span class="sxs-lookup"><span data-stu-id="d439b-290">Strict</span></span>|<span data-ttu-id="d439b-291">Os itens são adicionados ao cabeçalho de segurança seguindo as regras de layout numeradas descritas na seção política de segurança 7.7.1 de acordo com um princípio geral de "declarar antes de usar".</span><span class="sxs-lookup"><span data-stu-id="d439b-291">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="d439b-292">Incerto</span><span class="sxs-lookup"><span data-stu-id="d439b-292">Lax</span></span>|<span data-ttu-id="d439b-293">Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que esteja de acordo com o WSS: segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="d439b-293">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="d439b-294">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="d439b-294">LaxTimestampFirst</span></span>|<span data-ttu-id="d439b-295">O mesmo que LAX, exceto que o primeiro item no cabeçalho de segurança deve ser um wsse: timestamp</span><span class="sxs-lookup"><span data-stu-id="d439b-295">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="d439b-296">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="d439b-296">LaxTimestampLast</span></span>|<span data-ttu-id="d439b-297">O mesmo que LAX, exceto que o último item no cabeçalho de segurança deve ser um wsse: timestamp</span><span class="sxs-lookup"><span data-stu-id="d439b-297">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="d439b-298">O WCF dá suporte a todos os quatro modos de layout de cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="d439b-298">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="d439b-299">A estrutura de cabeçalho de segurança e os exemplos de mensagem para os modos de autenticação abaixo seguem o modo "estrito".</span><span class="sxs-lookup"><span data-stu-id="d439b-299">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="3-common-message-security-parameters"></a><span data-ttu-id="d439b-300">3. parâmetros de segurança de mensagem comum</span><span class="sxs-lookup"><span data-stu-id="d439b-300">3. Common Message Security Parameters</span></span>  

 <span data-ttu-id="d439b-301">Esta seção fornece as políticas de exemplo para cada modo de autenticação, juntamente com exemplos que mostram a estrutura de cabeçalho de segurança em mensagens trocadas por cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="d439b-301">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="31-transport-protection"></a><span data-ttu-id="d439b-302">Proteção de transporte 3,1</span><span class="sxs-lookup"><span data-stu-id="d439b-302">3.1 Transport Protection</span></span>  

 <span data-ttu-id="d439b-303">O WCF fornece cinco modos de autenticação que usam o transporte seguro para proteger mensagens; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport e SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="d439b-303">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="d439b-304">Esses modos de autenticação são construídos usando a associação de transporte descrita em SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="d439b-304">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="d439b-305">Para o modo de autenticação UserNameOverTransport, o UsernameToken é um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="d439b-305">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="d439b-306">Para os outros modos de autenticação, o token aparece como um token de endosso assinado.</span><span class="sxs-lookup"><span data-stu-id="d439b-306">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="d439b-307">O Apêndice C. 1.2 e o C. 1.3 de SecurityPolicy descrevem o layout do cabeçalho de segurança em detalhes.</span><span class="sxs-lookup"><span data-stu-id="d439b-307">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="d439b-308">Os cabeçalhos de segurança de exemplo a seguir mostram o layout estrito para um determinado modo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="d439b-308">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="d439b-309">O valor da propriedade "chaves derivadas" para os tokens em todos os casos é "false".</span><span class="sxs-lookup"><span data-stu-id="d439b-309">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="d439b-310">Os valores das várias propriedades da Associação de transporte são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="d439b-310">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="d439b-311">Carimbo de data/hora: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-311">Timestamp: true</span></span>  
  
 <span data-ttu-id="d439b-312">Layout do cabeçalho de segurança: estrito</span><span class="sxs-lookup"><span data-stu-id="d439b-312">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="d439b-313">Conjunto de algoritmos: Basic256</span><span class="sxs-lookup"><span data-stu-id="d439b-313">Algorithm Suite: Basic256</span></span>  
  
#### <a name="311-usernameovertransport"></a><span data-ttu-id="d439b-314">3.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-314">3.1.1 UsernameOverTransport</span></span>  

 <span data-ttu-id="d439b-315">Com esse modo de autenticação, o cliente é autenticado com um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="d439b-315">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d439b-316">O serviço é autenticado usando um certificado X. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-316">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d439b-317">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-317">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="d439b-318">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-318">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="d439b-319">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d439b-319">Security Header Layout</span></span>  
  
 <span data-ttu-id="d439b-320">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-320">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:UsernameToken u:Id="uuid-b96fbb3a-e646-4403-9473-2e5ffc733ff8-1"> ... </o:UsernameToken></o:Security>  
```  
  
 <span data-ttu-id="d439b-321">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-321">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="312-certificateovertransport"></a><span data-ttu-id="d439b-322">3.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-322">3.1.2 CertificateOverTransport</span></span>  

 <span data-ttu-id="d439b-323">Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="d439b-323">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d439b-324">O serviço é autenticado usando um certificado X. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-324">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d439b-325">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-325">The binding used is a transport binding.</span></span> <span data-ttu-id="d439b-326">CertificateOverTransport assina apenas os cabeçalhos SOAP, não o corpo SOAP.</span><span class="sxs-lookup"><span data-stu-id="d439b-326">CertificateOverTransport only signs the SOAP headers, not the SOAP body.</span></span> <span data-ttu-id="d439b-327">Esse é o modo de autenticação usado pelo modo de segurança TransportWithMessageCredentials.</span><span class="sxs-lookup"><span data-stu-id="d439b-327">This is the authentication mode used by the TransportWithMessageCredentials security mode.</span></span> <span data-ttu-id="d439b-328">Somente os cabeçalhos SOAP são assinados porque a autenticação é feita usando as credenciais da mensagem.</span><span class="sxs-lookup"><span data-stu-id="d439b-328">Only the SOAP headers are signed because authentication is done by using message credentials.</span></span>  
  
 <span data-ttu-id="d439b-329">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-329">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="CertificateOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="d439b-330">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d439b-330">Security Header Layout</span></span>  
  
 <span data-ttu-id="d439b-331">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-331">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="d439b-332">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-332">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="313-issuedtokenovertransport"></a><span data-ttu-id="d439b-333">3.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-333">3.1.3 IssuedTokenOverTransport</span></span>  

 <span data-ttu-id="d439b-334">Com esse modo de autenticação, o cliente não se autentica no serviço, como tal, mas apresenta um token emitido por um STS (serviço de token de segurança) e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d439b-334">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="d439b-335">O token emitido é exibido na camada SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="d439b-335">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d439b-336">O serviço é autenticado usando um certificado X. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-336">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d439b-337">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-337">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="d439b-338">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-338">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenOverTransport_policy">
 <wsp:ExactlyOne>
  <wsp:All>
   <sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:TransportToken>
      <wsp:Policy>
       <sp:HttpsToken />
      </wsp:Policy>
     </sp:TransportToken>
     <sp:AlgorithmSuite>
      <wsp:Policy>
       <sp:Basic256 />
      </wsp:Policy>
     </sp:AlgorithmSuite>
     <sp:Layout>
      <wsp:Policy>
       <sp:Strict/>
      </wsp:Policy>
     </sp:Layout>
     <sp:IncludeTimestamp/>
    </wsp:Policy>
   </sp:TransportBinding>
   <sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient">
      <Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
       <Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address>
       <Metadata xmlns="http://www.w3.org/2005/08/addressing">
        <Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
         <wsx:MetadataSection xmlns="">
          <wsx:MetadataReference>
           <Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address>
           <Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity">
            <Dns> ...  </Dns>
           </Identity>
          </wsx:MetadataReference>
         </wsx:MetadataSection>
        </Metadata>
       </Metadata>
      </Issuer>
      <sp:RequestSecurityTokenTemplate>
       <trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType>
      </sp:RequestSecurityTokenTemplate>
      <wsp:Policy>
       <sp:RequireInternalReference/>
      </wsp:Policy>
     </sp:IssuedToken>
     <sp:SignedParts>
      <sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/>
     </sp:SignedParts>
    </wsp:Policy>
   </sp:EndorsingSupportingTokens>
   <sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/>
     <sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/>
    </wsp:Policy>
   </sp:Wss11>
   <sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportIssuedTokens/>
     <sp:RequireClientEntropy/>
     <sp:RequireServerEntropy/>
    </wsp:Policy>
   </sp:Trust13>
   <wsaw:UsingAddressing/>
  </wsp:All>
 </wsp:ExactlyOne>
</wsp:Policy>
```  
  
 <span data-ttu-id="d439b-339">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d439b-339">Security Header Layout</span></span>  
  
 <span data-ttu-id="d439b-340">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-340">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67692bb6-85b7-4299-8587-3ce60086b0d2-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-341">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-341">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="314-kerberosovertransport"></a><span data-ttu-id="d439b-342">3.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-342">3.1.4 KerberosOverTransport</span></span>  

 <span data-ttu-id="d439b-343">Com esse modo de autenticação, o cliente é autenticado para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="d439b-343">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="d439b-344">O token Kerberos é exibido na camada SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d439b-344">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d439b-345">O serviço é autenticado usando um certificado X. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-345">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d439b-346">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-346">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="d439b-347">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-347">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="KerberosOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="d439b-348">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d439b-348">Security Header Layout</span></span>  
  
 <span data-ttu-id="d439b-349">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-349">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="d439b-350">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-350">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="315-sspinegotiatedovertransport"></a><span data-ttu-id="d439b-351">3.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="d439b-351">3.1.5 SspiNegotiatedOverTransport</span></span>  

 <span data-ttu-id="d439b-352">Com esse modo, um protocolo de negociação é usado para executar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="d439b-352">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="d439b-353">O Kerberos é usado se possível, caso contrário, NTLM.</span><span class="sxs-lookup"><span data-stu-id="d439b-353">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="d439b-354">O SCT resultante aparece na camada SOAP como um token de suporte de endosso que sempre é enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="d439b-354">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="d439b-355">O serviço também é autenticado na camada de transporte por um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-355">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="d439b-356">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d439b-356">The binding used is a transport binding.</span></span> <span data-ttu-id="d439b-357">"SPNEGO" (negociação) descreve como o WCF usa o protocolo de negociação binária SSPI com WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="d439b-357">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="d439b-358">Os exemplos de cabeçalho de segurança nesta seção são após o SCT ter sido estabelecido por meio do handshake SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="d439b-358">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="d439b-359">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-359">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiatedOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="d439b-360">Exemplos de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d439b-360">Security Header Examples</span></span>  

 <span data-ttu-id="d439b-361">Depois que o token de contexto de segurança é estabelecido por meio de handshake SPNEGO usando a negociação binária WS-Trust, as mensagens de aplicativo têm cabeçalhos de segurança com a seguinte estrutura.</span><span class="sxs-lookup"><span data-stu-id="d439b-361">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="d439b-362">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-362">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-9a29d087-5dae-4d40-bf86-5746d9d30eca-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="d439b-363">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-363">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
### <a name="32-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="d439b-364">3,2 usando certificados X. 509 para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="d439b-364">3.2 Using X.509 Certificates for Service Authentication</span></span>  

 <span data-ttu-id="d439b-365">Esta seção descreve os seguintes modos de autenticação: MutualCertificate WSS 1.0, Mutual CertificateDuplex, MutualCertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate e IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="d439b-365">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="321-mutualcertificate-wss10"></a><span data-ttu-id="d439b-366">3.2.1 MutualCertificate WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="d439b-366">3.2.1 MutualCertificate WSS1.0</span></span>  

 <span data-ttu-id="d439b-367">Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como o token do iniciador.</span><span class="sxs-lookup"><span data-stu-id="d439b-367">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="d439b-368">O serviço também é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-368">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d439b-369">Os cabeçalhos SOAP e o corpo SOAP são assinados.</span><span class="sxs-lookup"><span data-stu-id="d439b-369">Both the SOAP headers and the SOAP body are signed.</span></span> <span data-ttu-id="d439b-370">Uma chave simétrica é criada e criptografada com o certificado de transporte do destinatário.</span><span class="sxs-lookup"><span data-stu-id="d439b-370">A symmetric key is created and is encrypted with the transport certificate for the recipient.</span></span>  
  
 <span data-ttu-id="d439b-371">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="d439b-371">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="d439b-372">Token do iniciador: o certificado X. 509 do cliente, com o modo de inclusão definido como. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d439b-372">Initiator Token: the client’s X.509 certificate, with inclusion mode set to .../IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="d439b-373">Token do destinatário: o certificado X. 509 do servidor, com o modo de inclusão, está definido. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d439b-373">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set .../IncludeToken/Never</span></span>  
  
 <span data-ttu-id="d439b-374">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="d439b-374">Token Protection: False</span></span>  
  
 <span data-ttu-id="d439b-375">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-375">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d439b-376">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d439b-376">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d439b-377">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-377">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d439b-378">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-378">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-379">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-379">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-380">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-380">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-39cb393e-9da8-4d5d-b273-540ef614569b-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-381">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-381">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"> <u:Timestamp u:Id="uuid-3d742930-70d3-4d7e-aa0a-8721128dc115-8"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_5" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-382">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-382">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-383">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-383">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-384">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-384">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-73da3e21-abff-4294-a910-e75303d280cc-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-385">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-385">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-02f276b6-804f-480d-99e9-2e90fc76ab27-3"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="322-mutualcertificateduplex"></a><span data-ttu-id="d439b-386">3.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="d439b-386">3.2.2 MutualCertificateDuplex</span></span>  

 <span data-ttu-id="d439b-387">Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como o token do iniciador.</span><span class="sxs-lookup"><span data-stu-id="d439b-387">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="d439b-388">O serviço também é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-388">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="d439b-389">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="d439b-389">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="d439b-390">Token do iniciador: certificado X509 do cliente, modo de inclusão definido como. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d439b-390">Initiator Token: Client’s X509 Certificate, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="d439b-391">Token do destinatário: certificado X509 do servidor, modo de inclusão definido como. ../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="d439b-391">Recipient Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="d439b-392">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="d439b-392">Token Protection: False</span></span>  
  
 <span data-ttu-id="d439b-393">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-393">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d439b-394">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d439b-394">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d439b-395">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-395">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d439b-396">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-396">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-397">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-397">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-398">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-398">Request and Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4dec3da4-b572-4654-ba4d-4a2f84a87510-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-399">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-399">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-400">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-400">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-401">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-401">Request and Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b0e23feb-cd2d-4dc1-bad9-284bc45f3be3-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="323-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="d439b-402">3.2.3 usando Simétricobinding com autenticação de serviço X. 509</span><span class="sxs-lookup"><span data-stu-id="d439b-402">3.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  

 <span data-ttu-id="d439b-403">"WSS10" forneceu suporte limitado para cenários com tokens X509.</span><span class="sxs-lookup"><span data-stu-id="d439b-403">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="d439b-404">Por exemplo, não havia como fornecer proteção de assinatura e criptografia para mensagens usando apenas o token X509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="d439b-404">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="d439b-405">"WSS11" introduziu o uso de EncryptedKey como um token simétrico.</span><span class="sxs-lookup"><span data-stu-id="d439b-405">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="d439b-406">Agora, uma chave temporária criptografada para o certificado X. 509 do serviço pode ser usada para a proteção de mensagens de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="d439b-406">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="d439b-407">Os modos de autenticação descritos na seção 3,4 abaixo usam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="d439b-407">The authentication modes described in the section 3.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="d439b-408">WS-SecurityPolicy descreve esse padrão usando o Simétricobinding com o token X509 do serviço como o token de proteção.</span><span class="sxs-lookup"><span data-stu-id="d439b-408">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="d439b-409">Modos de autenticação AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 e IssuedTokenForCertificate usam uma instância semelhante de SP: Symmetricbinding com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="d439b-409">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="d439b-410">Token de proteção: certificado X509 do servidor, modo de inclusão definido como. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d439b-410">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="d439b-411">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="d439b-411">Token Protection: False</span></span>  
  
 <span data-ttu-id="d439b-412">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-412">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d439b-413">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d439b-413">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d439b-414">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-414">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d439b-415">Os modos de autenticação acima diferem apenas pelos tokens de suporte que eles usam.</span><span class="sxs-lookup"><span data-stu-id="d439b-415">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="d439b-416">AnonymousForCertificate não tem nenhum token de suporte, o MutualCertificate WSS 1,1 tem o certificado X509 do cliente como um token de suporte de endosso, UserNameForCertificate tem um token de nome de usuário como um token de suporte assinado e IssuedTokenForCertificate tem o token emitido como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d439b-416">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
#### <a name="324-anonymousforcertificate"></a><span data-ttu-id="d439b-417">3.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="d439b-417">3.2.4 AnonymousForCertificate</span></span>  

 <span data-ttu-id="d439b-418">Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-418">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d439b-419">A associação usada é uma instância da Associação simétrica, conforme descrito em 3.4.2.</span><span class="sxs-lookup"><span data-stu-id="d439b-419">The binding used is an instance of symmetric binding as described in 3.4.2.</span></span>  
  
 <span data-ttu-id="d439b-420">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-420">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-421">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-422">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-422">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-423">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-423">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b06cb481-3176-4c56-af35-c38252bb6c78-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-424">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-424">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-425">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-425">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-426">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-426">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-427">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-427">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-15b48260-23da-424d-8dc4-8f4e150fb8cf-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="ALF+QNGmWn2k3LpWEDIzSBgTkvo=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="325-usernameforcertificate"></a><span data-ttu-id="d439b-428">3.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="d439b-428">3.2.5 UserNameForCertificate</span></span>  

 <span data-ttu-id="d439b-429">Com esse modo de autenticação, o cliente é autenticado no serviço usando um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="d439b-429">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="d439b-430">O serviço é autenticado no cliente usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-430">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="d439b-431">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="d439b-431">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d439b-432">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-432">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-433">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-433">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-434">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-434">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-435">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-435">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-681226f7-126a-4806-b732-fcca097cd7a8-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-436">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-436">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-437">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-437">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-438">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-438">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-439">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-439">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8a7ad353-f071-49dc-90dd-5ad2e9abd40a-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="326-mutualcertificate-wss-11"></a><span data-ttu-id="d439b-440">3.2.6 MutualCertificate (WSS 1,1)</span><span class="sxs-lookup"><span data-stu-id="d439b-440">3.2.6 MutualCertificate (WSS 1.1)</span></span>  

 <span data-ttu-id="d439b-441">Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d439b-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d439b-442">O serviço também é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d439b-443">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="d439b-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d439b-444">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-444">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-445">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-445">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-446">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-446">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><o:BinarySecurityToken> ...</o:BinarySecurityToken><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-447">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-447">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8c73fa91-f95b-40ff-b088-48118e6fadcf-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_3" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-448">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-448">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-449">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-449">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-450">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-450">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature Id="_2" xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-451">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-451">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67dacc31-4a50-4866-b673-ccc03e156337-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="mYyksUQKkK27Fd6hmgOiqFwvudk=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><k:SignatureConfirmation u:Id="_3" Value="SreOZ4Rr2BcXjFQFvgN55ERypI/1/86hdWThE5lav0eYIxF1OCzQgZF+y7cQ82t+g3CRnLbE3c52DqMpY/HXlrdMct3m3rnpDH+fqdhNY4fE+M2v4zUMFR7uxDKWcEm9zZpmUvJCDfJRfKRaKjy5cTbccRKqSxw7HAqOYnqibA4=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="327-issuedtokenforcertificate"></a><span data-ttu-id="d439b-452">3.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="d439b-452">3.2.7 IssuedTokenForCertificate</span></span>  

 <span data-ttu-id="d439b-453">Com esse modo de autenticação, o cliente não se autentica no serviço, como tal, mas apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d439b-453">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d439b-454">O token emitido é exibido na camada SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d439b-454">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d439b-455">O serviço é autenticado no cliente usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-455">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="d439b-456">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="d439b-456">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d439b-457">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-457">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-458">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-458">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-459">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-459">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1d2c03e6-0b69-4483-903a-6ef9b9d286ed-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-460">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-460">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-461">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-461">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-462">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-462">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="d439b-463">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-463">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-de1c51aa-2ecc-4e70-b6bd-9dca58331fa7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-464">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-464">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
## <a name="33-kerberos"></a><span data-ttu-id="d439b-465">3,3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="d439b-465">3.3 Kerberos</span></span>  

 <span data-ttu-id="d439b-466">Com esse modo de autenticação, o cliente é autenticado para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="d439b-466">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="d439b-467">Esse mesmo tíquete também fornece autenticação de servidor.</span><span class="sxs-lookup"><span data-stu-id="d439b-467">That same ticket also provides server authentication.</span></span> <span data-ttu-id="d439b-468">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="d439b-468">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d439b-469">Token de proteção: tíquete Kerberos, modo de inclusão é definido como. ../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="d439b-469">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="d439b-470">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="d439b-470">Token Protection: False</span></span>  
  
 <span data-ttu-id="d439b-471">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-471">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d439b-472">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d439b-472">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d439b-473">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-473">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d439b-474">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-474">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-475">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-475">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-476">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-476">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e8f6dc3b-407d-4387-bd33-97aedfd8bf13-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-477">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-477">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7b03568e-66ae-49da-82ee-5d12d372876e-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-478">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-478">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-479">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-479">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-480">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-480">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d29247f0-f220-4e81-9a8d-a15f5ac31072-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-481">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-481">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9025b930-4f15-42fe-8e78-35d3a3480177-2"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="34-issuedtoken"></a><span data-ttu-id="d439b-482">3,4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="d439b-482">3.4 IssuedToken</span></span>  

 <span data-ttu-id="d439b-483">Com esse modo de autenticação, o cliente não se autentica no serviço, como tal, em vez disso, o cliente apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d439b-483">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d439b-484">O serviço não é autenticado para o cliente, como tal, em vez disso, o STS criptografa a chave compartilhada como parte do token emitido, de modo que somente o serviço possa descriptografar a chave.</span><span class="sxs-lookup"><span data-stu-id="d439b-484">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="d439b-485">A associação usada é como uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="d439b-485">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d439b-486">Token de proteção: token emitido, o modo de inclusão é definido como. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d439b-486">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="d439b-487">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="d439b-487">Token Protection: False</span></span>  
  
 <span data-ttu-id="d439b-488">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-488">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d439b-489">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d439b-489">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d439b-490">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-490">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d439b-491">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-491">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-492">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-492">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-493">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-493">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-61ce3989-bc38-4d67-8262-6232c9d49a26-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-494">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-494">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 <span data-ttu-id="d439b-495">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-495">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-496">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-496">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-497">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-497">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1dc8bdef-4202-4e08-8a5e-ab94da579dec-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-498">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-498">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> </c:DerivedKeyToken> ... <c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="35-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="d439b-499">3,5 usando SslNegotiated para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="d439b-499">3.5 Using SslNegotiated for Service Authentication</span></span>  

 <span data-ttu-id="d439b-500">Esta seção descreve um grupo de modos de autenticação que usam uma associação simétrica com o token de proteção sendo um token de contexto de segurança por WS-SecureConversation (WS-SC), cujo valor de chave é negociado executando o protocolo TLS em mensagens de RST/RSTR de WS-Trust (WS-T).</span><span class="sxs-lookup"><span data-stu-id="d439b-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="d439b-501">Os detalhes da implementação de handshake de TLS usando WS-Trust são descritos em TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="d439b-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="d439b-502">Aqui, nos exemplos de mensagem, vamos supor que o SCT com um contexto de segurança associado já foi estabelecido por meio de um handshake.</span><span class="sxs-lookup"><span data-stu-id="d439b-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="d439b-503">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="d439b-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d439b-504">Token de proteção: SslContextToken, o modo de inclusão é definido como. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d439b-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="d439b-505">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="d439b-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="d439b-506">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d439b-507">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d439b-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d439b-508">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-508">Encrypt Signature: True</span></span>  
  
#### <a name="351-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="d439b-509">política 3.5.1 para autenticação do serviço SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-509">3.5.1 Policy for SslNegotiated service authentication</span></span>  

 <span data-ttu-id="d439b-510">A política para todos os modos de autenticação nesta seção é semelhante e difere somente por tokens de suporte ou de endosso específicos assinados usados.</span><span class="sxs-lookup"><span data-stu-id="d439b-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
#### <a name="352-anonymousforsslnegotiated"></a><span data-ttu-id="d439b-511">3.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-511">3.5.2 AnonymousForSslNegotiated</span></span>  

 <span data-ttu-id="d439b-512">Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d439b-513">A associação usada é uma instância de associação simétrica, conforme descrito em 3.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="d439b-513">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="d439b-514">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-514">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-515">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-515">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-516">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-516">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f4b86ce2-4ba6-4c55-bac1-2e920fc6d5db-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-517">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-517">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-518">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-518">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-519">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-519">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-520">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-520">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c84b24b9-39e0-4cc3-99e2-cec088f1b9eb-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-521">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-521">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="353-usernameforsslnegotiated"></a><span data-ttu-id="d439b-522">3.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-522">3.5.3 UserNameForSslNegotiated</span></span>  

 <span data-ttu-id="d439b-523">Com esse modo de autenticação, o cliente é autenticado usando um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="d439b-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="d439b-524">O serviço é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d439b-525">A associação usada é uma instância da Associação simétrica, conforme descrito em 3.5.1.</span><span class="sxs-lookup"><span data-stu-id="d439b-525">The binding used is an instance of symmetric binding as described in 3.5.1.</span></span>  
  
 <span data-ttu-id="d439b-526">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-526">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-527">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-527">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-528">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-528">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3d1a12c3-e690-474a-a223-a346fc0329a9-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-529">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-529">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-530">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-530">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-531">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-531">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-532">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-532">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-56e931e8-20c2-457f-a83e-8fcd6b92c258-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-533">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-533">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="354-issuedtokenforsslnegotiated"></a><span data-ttu-id="d439b-534">3.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-534">3.5.4 IssuedTokenForSslNegotiated</span></span>  

 <span data-ttu-id="d439b-535">Com esse modo de autenticação, o cliente não se autentica no serviço, como tal, mas apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d439b-535">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d439b-536">O token emitido é exibido na camada SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d439b-536">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d439b-537">O serviço é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-537">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d439b-538">A associação usada é uma instância de associação simétrica, conforme descrito em 3.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="d439b-538">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="d439b-539">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-539">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-540">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-540">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-541">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-541">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b19fb2e7-8f0c-45c1-b62c-45d6ff6d57e7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-542">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-542">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-543">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-543">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-544">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-544">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-545">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-545">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d75104d5-313e-440f-b112-db8aff57a5fe-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-546">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-546">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="355-mutualsslnegotiated"></a><span data-ttu-id="d439b-547">3.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-547">3.5.5 MutualSslNegotiated</span></span>  

 <span data-ttu-id="d439b-548">Com esse modo de autenticação, o cliente e o serviço se autenticam usando certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="d439b-548">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="d439b-549">A associação usada é uma instância de associação simétrica, conforme descrito em 3.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="d439b-549">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="d439b-550">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-550">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-551">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-551">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-552">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-552">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d1e6037e-8a64-494f-9447-07d3125b81b5-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-553">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-553">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-554">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-554">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-555">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-555">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-556">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-556">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c2a6ab10-889a-4ee1-871d-05410c90fc10-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-557">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-557">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="36-sspinegotiated"></a><span data-ttu-id="d439b-558">3,6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="d439b-558">3.6 SspiNegotiated</span></span>  

 <span data-ttu-id="d439b-559">Com esse modo de autenticação, um protocolo de negociação é usado para executar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="d439b-559">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="d439b-560">O Kerberos é usado se possível, caso contrário, NTLM.</span><span class="sxs-lookup"><span data-stu-id="d439b-560">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="d439b-561">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="d439b-561">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d439b-562">Token de proteção: SpnegoContextToken, o modo de inclusão é definido como. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d439b-562">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="d439b-563">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="d439b-563">Token Protection: False</span></span>  
  
 <span data-ttu-id="d439b-564">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-564">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d439b-565">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d439b-565">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d439b-566">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="d439b-566">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d439b-567">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-567">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-568">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-568">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-569">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-569">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9a954fcb-4df2-4610-9800-f542f2b5130a-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-570">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-570">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 <span data-ttu-id="d439b-571">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-571">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-572">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-572">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-573">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-573">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f1673773-f9a7-4b43-b13b-405e7dd4a6e3-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="d439b-574">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-574">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="37-secureconversation"></a><span data-ttu-id="d439b-575">3,7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="d439b-575">3.7 SecureConversation</span></span>  

 <span data-ttu-id="d439b-576">A associação usada é uma associação simétrica com o token de proteção sendo um SCT por WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="d439b-576">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="d439b-577">O SCT é negociado usando WS-Trust (WS-Trust) ou WS-SecureConversation (WS-SC) de acordo com uma associação aninhada, que, por sua vez, é uma ligação simétrica que usa um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="d439b-577">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="d439b-578">O protocolo de negociação usará o Kerberos para executar a autenticação de cliente e servidor, se possível.</span><span class="sxs-lookup"><span data-stu-id="d439b-578">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="d439b-579">Se o Kerberos não puder ser usado, ele retornará ao NTLM.</span><span class="sxs-lookup"><span data-stu-id="d439b-579">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="d439b-580">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-580">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d439b-581">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d439b-581">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="d439b-582">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-582">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f01c6159-f159-454d-bd97-bbcc9b8e25d3-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-583">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-583">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-584">Política</span><span class="sxs-lookup"><span data-stu-id="d439b-584">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d439b-585">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d439b-585">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="d439b-586">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d439b-586">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d57e6342-1c68-4095-a0c1-41979088a944-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="d439b-587">Resposta</span><span class="sxs-lookup"><span data-stu-id="d439b-587">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```
