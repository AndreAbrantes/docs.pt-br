---
ms.openlocfilehash: f4a5911787fa5f72be1dcd15c67b3f132c3f1110
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804488"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap converte com êxito ícones com quadros PNG em objetos Bitmap

|   |   |
|---|---|
|Detalhes|Começando com os aplicativos direcionados ao .NET Framework 4.6, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> converte com êxito ícones com quadros PNG em objetos Bitmap.<p/>Nos aplicativos direcionados ao .NET Framework 4.5.2 e a versões anteriores, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> gera uma exceção <xref:System.ArgumentOutOfRangeException> quando o objeto Ícone tem quadros PNG.<p/>Essa alteração afeta os aplicativos que são recompilados para serem direcionados ao .NET Framework 4.6 e que implementam um tratamento especial para a <xref:System.ArgumentOutOfRangeException>, que será gerada quando um objeto Ícone tiver quadros PNG. Ao executar no .NET Framework 4.6, a conversão é bem-sucedida, uma <xref:System.ArgumentOutOfRangeException> não é mais gerada e, portanto, o manipulador de exceção não é invocado.|
|Sugestão|Se esse comportamento for indesejável, será possível reter o comportamento anterior adicionando o seguinte elemento à seção <code>&lt;runtime&gt;</code> do arquivo app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Se o arquivo app.config já contiver o elemento <code>AppContextSwitchOverrides</code>, o novo valor deverá ser mesclado ao atributo de valor, da seguinte forma:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Escopo|Secundária|
|Versão|4.6|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|
