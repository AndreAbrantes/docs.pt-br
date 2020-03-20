---
title: Segurança de mensagem com um nome de usuário cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 3dd21268d4ea7dc59c74889ac94dc86678e91865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184634"
---
# <a name="message-security-with-a-user-name-client"></a>Segurança de mensagem com um nome de usuário cliente
A ilustração a seguir mostra um serviço da Windows Communication Foundation (WCF) e um cliente protegido usando segurança de nível de mensagem. O serviço é autenticado com um certificado X.509. O cliente autentica usando um nome de usuário e senha.  
  
 Para obter um aplicativo de exemplo, consulte [Nome do usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md).  
  
 ![Segurança de mensagem usando autenticação de nome de usuário](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Mensagem|  
|Interoperabilidade|Windows Communication Foundation (WCF) apenas|  
|Autenticação (Servidor)|Negociação inicial requer autenticação do servidor|  
|Autenticação (Cliente)|Nome de usuário/senha|  
|Integridade|Sim, usando o contexto de segurança compartilhada|  
|Confidencialidade|Sim, usando o contexto de segurança compartilhada|  
|Transporte|HTTP|  
|Associação|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Serviço  
 O seguinte código e configuração devem ser executados independentemente. Realize um dos seguintes procedimentos:  
  
- Crie um serviço autônomo usando o código sem configuração.  
  
- Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto final.  
  
### <a name="code"></a>Código  
 O código a seguir mostra como criar um ponto final de serviço que usa a segurança da mensagem.  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a>Configuração  
 A seguinte configuração pode ser usada em vez do código:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
  
### <a name="code"></a>Código  
 O código a seguir cria o cliente. A vinculação é para a segurança do modo de `UserName`mensagem, e o tipo de credencial do cliente está definido como . O nome de usuário e a senha só podem ser especificados usando código (não é configurável). O código para devolver o nome de usuário e a senha não é mostrado aqui porque deve ser feito no nível do aplicativo. Por exemplo, use uma caixa de diálogo Formulários do Windows para consultar os dados do usuário.  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a>Configuração  
 O código a seguir configura o cliente. A vinculação é para a segurança do modo de `UserName`mensagem, e o tipo de credencial do cliente está definido como . O nome de usuário e a senha só podem ser especificados usando código (não é configurável).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Visão geral da segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [Identidade e autenticação de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<>de identidade](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- [Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
