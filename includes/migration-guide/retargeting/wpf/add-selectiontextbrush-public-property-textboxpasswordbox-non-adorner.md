---
ms.openlocfilehash: e04134ec731c5e7bede3388621078c6518805ec2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803501"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Adicionar a propriedade pública SelectionTextBrush à seleção não baseada em adorno TextBox/PasswordBox

|   |   |
|---|---|
|Detalhes|Em aplicativos do WPF que usam a [seleção de texto não baseada em adorno](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) para <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.PasswordBox>, os desenvolvedores podem agora definir a propriedade SelectionTextBrush recém-adicionada para alterar a renderização do texto selecionado.  Por padrão, essa cor é alterada com <xref:System.Windows.SystemColors.HighlightTextBrushKey>.  Se a seleção de texto não baseada em adorno não estiver habilitada, essa propriedade não fará nada.|
|Sugestão|Depois que a seleção de texto não baseada em adorno estiver habilitada, será possível usar a propriedade <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> e <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> para alterar a aparência do texto selecionado. Isso pode ser feito usando XAML:<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Escopo|Principal|
|Versão|4.8|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|
