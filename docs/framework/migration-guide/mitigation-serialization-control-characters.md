---
title: "Mitigação: serialização de caracteres de controle com o DataContractJsonSerializer | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: 596d7ea858e40a558767fa76bb717dbbba97d4ed
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Mitigação: serialização de caracteres de controle com o DataContractJsonSerializer

A partir do .NET Framework 4.7, a maneira com a qual os caracteres de controle são serializados com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> foi alterada para estar em conformidade com o ECMAScript V6 e V8. 
 
## <a name="impact"></a>Impacto

No .NET framework 4.6.2 e nas versões anteriores, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não serializava alguns caracteres de controle especiais, como `\b`, `\f` e `\t`, de uma forma compatível com os padrões ECMAScript V6 e V8.

Para aplicativos destinados a versões do .NET Framework, a partir do .NET Framework 4.7, a serialização desses caracteres de controle é compatível com o ECMAScript V6 e V8. As seguintes APIs são afetadas:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Redução

Para aplicativos destinados a versões do .NET Framework, a partir do .NET Framework 4.7, esse comportamento é habilitado por padrão.

Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Consulte também
[Alterações de redirecionamento no .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

