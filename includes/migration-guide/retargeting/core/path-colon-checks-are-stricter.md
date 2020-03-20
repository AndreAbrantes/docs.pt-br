---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859342"
---
### <a name="path-colon-checks-are-stricter"></a>Verificações de dois-pontos em caminhos estão mais rigorosas

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2, uma série de alterações foram feitas para dar suporte aos caminhos incompatíveis anteriormente (em termos de comprimento e formato). As verificações de sintaxe do separador de unidades (dois-pontos) correto foram aperfeiçoadas, o que teve como efeito colateral o bloqueio de alguns caminhos de URI em algumas APIs de Caminho selecionadas em que eles costumavam ser aceitos.|
|Sugestão|Ao passar um URI para as APIs afetadas, modifique a cadeia de caracteres para um caminho correto antes.<ul><li>Remova o esquema das URLs manualmente (por exemplo, remova <code>file://</code> das URLs).</li><li>Passe o URI para a classe <xref:System.Uri> e use <xref:System.Uri.LocalPath>.</li></ul>Como alternativa, é possível recusar a normalização do novo caminho definindo a opção AppContext <code>Switch.System.IO.UseLegacyPathHandling</code> como true.|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
