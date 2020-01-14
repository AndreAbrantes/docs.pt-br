---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937024"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling

O `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade, que foi introduzido no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.

#### <a name="change-description"></a>Descrição das alterações

A partir do .NET Framework 4.7.1, a opção de compatibilidade de `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` permitia aos desenvolvedores recusarem <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> e <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ações independentes. A opção restaurou o comportamento herdado, no qual o <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> será ignorado se o texto do contexto estiver presente e o desenvolvedor for solicitado a usar <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ação no controle antes da ação do <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>. Para obter mais informações, consulte [\<elemento > AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Remova a opção. Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
