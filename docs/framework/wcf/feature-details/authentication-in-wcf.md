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
# <a name="authentication-in-wcf"></a>Autenticação no WCF

Os tópicos a seguir mostram vários mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, autenticação do Windows, certificados X. 509 e nome de usuário e senhas.  
  
## <a name="in-this-section"></a>Nesta seção  

 [Como: usar o provedor de associação do ASP.NET](how-to-use-the-aspnet-membership-provider.md)  
 Os recursos do ASP.NET incluem uma associação e um provedor de função, um banco de dados para armazenar pares de nome de usuário/senha para autenticação e funções de usuário para autorização. Este tópico explica como os serviços WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.  
  
 [Como: usar um validador personalizado de nome de usuário e senha](how-to-use-a-custom-user-name-and-password-validator.md)  
 Demonstra como integrar um validador de nome de usuário/senha personalizado.  
  
 [Identidade e autenticação de serviço](service-identity-and-authentication.md)  
 Como uma proteção extra, um cliente pode autenticar o serviço especificando a *identidade* esperada do serviço. Se a identidade esperada e a identidade retornada pelo serviço não corresponderem, a autenticação falhará.  
  
 [Negociação de segurança e tempo limite](security-negotiation-and-timeouts.md)  
 Descreve como usar a <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Propriedade na <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.  
  
 [Depurando erros de autenticação do Windows](debugging-windows-authentication-errors.md)  
 Concentra-se em problemas comuns encontrados ao usar a autenticação do Windows.  
  
## <a name="reference"></a>Referência  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Seções relacionadas  

 [Cenários comuns de segurança](common-security-scenarios.md)  
  
## <a name="see-also"></a>Veja também

- [Visão geral de segurança](security-overview.md)
- [Modelo de segurança para o Windows Server app Fabric](/previous-versions/appfabric/ee677202(v=azure.10))
