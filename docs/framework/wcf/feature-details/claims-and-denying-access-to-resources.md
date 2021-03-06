---
title: Declarações e acesso negado para recursos
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 2c903d5b5aa520b9c79fb8b36912324feaf9a432
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264915"
---
# <a name="claims-and-denying-access-to-resources"></a>Declarações e acesso negado para recursos

O Windows Communication Foundation (WCF) dá suporte a um mecanismo de autorização baseado em declarações. Além de permitir o acesso a recursos com base na presença de declarações, os sistemas geralmente negam o acesso a recursos com base na presença de declarações. Esses sistemas devem examinar as <xref:System.IdentityModel.Policy.AuthorizationContext> declarações para que resultam no acesso negado antes de procurar declarações que resultam no acesso permitido.  
  
 Por exemplo, um sistema pode negar acesso a um recurso a qualquer pessoa que tenha uma declaração com um tipo de `Age` , um direito de <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> e um valor de recurso `Under 21` somente quando essa identidade também tiver uma declaração de tipo `Name` , à direita e <xref:System.IdentityModel.Claims.Rights.Identity%2A> um valor de recurso de `Mallory` . Em outras palavras, o sistema nega acesso a qualquer pessoa com menos de 21 anos de idade e concede acesso quando o nome é Mallory. Para implementar corretamente essa semântica, é importante procurar a `Age` declaração primeiro e determinar se a idade está abaixo de 21 anos de idade. Caso contrário, se Mallory for inferior a 21, o recurso poderá receber acesso exclusivamente com base na `Name` declaração.  
  
## <a name="see-also"></a>Veja também

- [Gerenciamento de declarações e autorizações com o modelo de identidade](managing-claims-and-authorization-with-the-identity-model.md)
- [Declarações e tokens](claims-and-tokens.md)
