---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e909756a58d5008d917fca84af0e478fc4878d2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156804"
---
# \<system.identityModel.services>

A seção de configuração para autenticação usando o protocolo WS-Federation.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  

 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Contém as configurações que definem os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> módulos http (WSFAM) e <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).|  
  
### <a name="parent-elements"></a>Elementos pai  

 Nenhum  
  
## <a name="remarks"></a>Comentários  

 Adicione uma `<system.identityModel.services>` seção ao arquivo de configuração do aplicativo para fornecer as configurações para o Sam e o WSFAM.  
  
> [!IMPORTANT]
> Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, o Gerenciador de autorização de declarações ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) e a política usada para tomar decisões de autorização são configurados por meio de um `<identityConfiguration>` elemento que é implicitamente ou explicitamente referenciado de um `<federationConfiguration>` elemento nesta seção. Para obter mais informações, consulte os **comentários** sob o [\<federationConfiguration>](federationconfiguration.md) elemento.  
  
 A `<system.identityModel.services>` seção é representada pela <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe. A coleção de `<federationConfiguration>` elementos filho configurados na seção é representada pela <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> classe.  
  
## <a name="example"></a>Exemplo  

 O XML a seguir mostra como adicionar uma `<system.identityModel.services>` seção a um arquivo de configuração. Você deve primeiro adicionar declarações de seção para a `<system.identityModel.services>` seção e as `<system.identityModel>` seções. (Ao adicionar uma `<system.identityModel.services>` seção, você também deve adicionar uma declaração para a `<system.identityModel>` seção para garantir que uma seção padrão `<identityConfiguration>` possa ser criada pelo tempo de execução, se necessário.) Depois que as declarações de seção tiverem sido adicionadas, você poderá definir as configurações de autenticação federada no `<system.identityModel.services>` elemento.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"
        issuer="http://localhost:15839/wsFederationSTS/Issue"
        realm="http://localhost:50969/" reply="http://localhost:50969/"
        requireHttps="false"
        signOutReply="http://localhost:50969/SignedOutPage.html"
        signOutQueryString="Param1=value2&Param2=value2"
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
