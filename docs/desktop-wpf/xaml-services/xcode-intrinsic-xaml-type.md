---
title: Tipo intrínseco x:Code (XAML)
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: ea7bc17cba19137b4e4ca2d8cddb32e6630887c9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544837"
---
# <a name="xcode-intrinsic-xaml-type"></a>Tipo intrínseco x:Code (XAML)
Permite o posicionamento do código em uma produção XAML. Esse código pode ser compilado por qualquer implementação de processador XAML que compila XAML ou deixado na produção XAML para usos posteriores, como interpretação por um tempo de execução.

## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>Comentários

O código dentro do `x:Code` elemento de diretiva XAML ainda é interpretado no namespace XML geral e nos namespaces XAML fornecidos. Portanto, geralmente é necessário colocar o código usado para dentro de `x:Code` um `CDATA` segmento.

`x:Code` Não é permitido para todos os mecanismos de implantação possíveis de uma produção XAML. Em estruturas específicas (por exemplo, WPF), o código deve ser compilado. Em outras estruturas, o `x:Code` uso pode ser geralmente não permitido.

Para estruturas que permitem conteúdo gerenciado `x:Code` , o compilador de idioma correto a ser usado para `x:Code` conteúdo é determinado pelas configurações e destinos do projeto recipiente que é usado para compilar o aplicativo.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

O código declarado no `x:Code` para WPF tem várias limitações notáveis:

- O `x:Code` elemento Diretivo deve ser um elemento filho imediato do elemento raiz da produção XAML.

- a [diretiva x:Class](xclass-directive.md) deve ser fornecida no elemento pai root.

- O código colocado em `x:Code` será tratado pela compilação para estar dentro do escopo da classe parcial que já está sendo criada para essa página XAML. Portanto, todo o código que você definir deve ser membros ou variáveis dessa classe parcial.

- Você não pode definir classes adicionais, além de aninhar uma classe dentro da classe Partial (o aninhamento é permitido, mas não é comum porque classes aninhadas não podem ser referenciadas em XAML). Os namespaces CLR que não sejam o namespace usado para a classe parcial existente não podem ser definidos ou adicionados ao.

- As referências a entidades de código fora do namespace CLR de classe parcial devem ser totalmente qualificadas. Se os membros que estão sendo declarados forem substituídos para os membros de classe parcial Overridable, isso deverá ser especificado com a palavra-chave de substituição específica do idioma. Se os membros declarados no escopo entrarem em `x:Code` conflito com membros da classe parcial criada fora do XAML, de forma que o compilador relate o conflito, o arquivo XAML não poderá ser compilado ou carregado.

## <a name="see-also"></a>Confira também

- [Diretiva x:Class](xclass-directive.md)
- [Code-behind e XAML no WPF](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
