---
title: Comentários de documentação XML – Guia de Programação em C#
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: 07daff8b819220fad07e516281b93b24e39cba46
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711760"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Comentários de documentação XML (Guia de Programação em C#)
No Visual C#, você pode criar documentação para seu código ao incluir elementos XML nos campos de comentários especiais (indicados por barras triplas) no código-fonte logo antes do bloco de código ao qual os comentários se referem, por exemplo:  
  
```csharp  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 Quando você compilar com a opção [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) , o compilador pesquisará todas as marcas XML no código-fonte e criará um arquivo de documentação XML. Para criar a documentação final com base no arquivo gerado pelo compilador, crie uma ferramenta personalizada ou use uma ferramenta como o [DocFX](https://dotnet.github.io/docfx/) ou o [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Para consultar elementos XML (por exemplo, sua função processa elementos XML específicos que você deseja descrever em um comentário da documentação XML), você pode usar o mecanismo de citação padrão (`<` e `>`).  Para consultar identificadores genéricos em elementos de referência de código (`cref`), você pode usar os caracteres de escape (por exemplo, `cref="List&lt;T&gt;"`) ou chaves (`cref="List{T}"`).  Como um caso especial, o compilador analisa as chaves como colchetes angulares para tornar o comentário da documentação menos incômodo para o autor ao fazer referência a identificadores genéricos.  
  
> [!NOTE]
> Os comentários da documentação XML não são metadados; eles não estão incluídos no assembly compilado e, portanto, não são acessíveis através de reflexão.  
  
## <a name="in-this-section"></a>Nesta seção  
  
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)  
  
- [Processando o Arquivo XML](./processing-the-xml-file.md)  
  
- [Delimitadores para marcas de documentação](./delimiters-for-documentation-tags.md)  
  
- [Como usar os recursos de documentação XML](./how-to-use-the-xml-documentation-features.md)
  
## <a name="related-sections"></a>Seções Relacionadas  
 Para obter mais informações, consulte .  
  
- [-Doc (comentários de documentação do processo)](../../language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>Especificação da linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
