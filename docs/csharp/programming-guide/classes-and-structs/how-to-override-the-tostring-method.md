---
title: Como substituir o método ToString – guia C# de programação
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 7c7196df56821c134b31982d7956a75039e9f929
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705568"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Como substituir o método ToString (guiaC# de programação)

Cada classe ou struct no C# herda implicitamente a classe <xref:System.Object>. Portanto, cada objeto no C# obtém o método <xref:System.Object.ToString%2A>, que retorna uma representação de cadeia de caracteres desse objeto. Por exemplo, todas as variáveis do tipo `int` tem um método `ToString`, que permite retornar seus conteúdos como uma cadeia de caracteres:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Ao criar uma classe ou struct personalizada, é necessário substituir o método <xref:System.Object.ToString%2A> a fim de fornecer informações sobre o tipo ao código cliente.  
  
 Para obter informações sobre como usar cadeias de caracteres de formato e outros tipos de formatação personalizada com o método `ToString`, consulte [Tipos de Formatação](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Ao decidir quais informações devem ser fornecidas por meio desse método, considere se a classe ou struct será utilizado por código não confiável. Assegure-se de que nenhuma informação que possa ser explorada por código mal-intencionado seja fornecida.  
  
Substituir o método `ToString` na classe ou struct:
  
1. Declare um método `ToString` com os seguintes modificadores e tipo retornado:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Implemente o método para que ele retorne uma cadeia de caracteres.  
  
     O exemplo a seguir retorna o nome da classe, além dos dados específicos de uma instância particular da classe.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     É possível testar o método `ToString`, conforme mostrado no exemplo de código a seguir:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.IFormattable>
- [Guia de Programação em C#](../index.md)
- [Classes e Structs](./index.md)
- [Cadeias de Caracteres](../strings/index.md)
- [string](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Formatando Tipos](../../../standard/base-types/formatting-types.md)
