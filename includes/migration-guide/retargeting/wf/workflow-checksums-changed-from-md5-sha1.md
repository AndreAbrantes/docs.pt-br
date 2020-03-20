---
ms.openlocfilehash: 0b42e320ba439a4cfc196471fc6dd4b3c15cd9d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859107"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Somas de verificação de fluxo de trabalho alteradas de MD5 para SHA1

|   |   |
|---|---|
|Detalhes|Para compatibilidade com a depuração com o Visual Studio, o runtime de fluxo de trabalho gera uma soma de verificação para uma instância de fluxo de trabalho usando um algoritmo de hash. No .NET Framework 4.6.2 e versões anteriores, o hash de soma de verificação do fluxo de trabalho usava o algoritmo MD5, o que causou problemas em sistemas habilitados para FIPS. A partir do .NET Framework 4.7, o algoritmo será o SHA1. Se o código persistir a essas somas de verificação, eles serão incompatíveis.|
|Sugestão|Se o código for incapaz de carregar instâncias de fluxo de trabalho por causa de uma falha na soma de verificação, tente configurar a opção <code>AppContext</code>&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; com true. Em código:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Ou em nossa configuração:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundária|
|Versão|4.7|
|Type|Redirecionando|
