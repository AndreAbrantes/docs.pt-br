---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859092"
---
### <a name="throttle-concurrent-requests-per-session"></a>Limitação de solicitações simultâneas por sessão

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2 e versões anteriores, o ASP.NET executa solicitações com a mesma Sessionid sequencialmente e sempre emite a Sessionid por meio de um cookie por padrão. Se uma página levar muito tempo para responder, ele prejudicará significativamente o desempenho do servidor simplesmente pressionando F5 no navegador. Na correção, adicionou-se um contador que acompanha as solicitações enfileiradas e encerra as solicitações quando elas excedem um limite especificado. O valor padrão é 50. Se o limite for alcançado, um aviso será registrado no log de eventos e uma resposta HTTP 500 poderá ser registrada no log do IIS.|
|Sugestão|Para restaurar o comportamento antigo, você pode adicionar a seguinte configuração ao arquivo web.config para recusar o novo comportamento.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Type|Redirecionando|
