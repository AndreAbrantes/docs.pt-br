---
title: Como implementar e chamar um método de extensão personalizado – C# guia de programação
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7e2092a37c1f042a087e03f4a272139b585156c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705594"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Como implementar e chamar um método de extensão personalizado (C# guia de programação)
Este tópico mostra como implementar seus próprios métodos de extensão para qualquer tipo do .NET. O código de cliente pode usar seus métodos de extensão, adicionando uma referência à DLL que os contém e adicionando uma diretiva [using](../../language-reference/keywords/using-directive.md) que especifica o namespace no qual os métodos de extensão são definidos.  
  
## <a name="to-define-and-call-the-extension-method"></a>Para definir e chamar o método de extensão  
  
1. Defina uma [classe](./static-classes-and-static-class-members.md) estática para conter o método de extensão.  
  
     A classe deve estar visível para o código de cliente. Para obter mais informações sobre regras de acessibilidade, consulte [Modificadores de acesso](./access-modifiers.md).  
  
2. Implemente o método de extensão como um método estático com, pelo menos, a mesma visibilidade da classe que a contém.  
  
3. O primeiro parâmetro do método especifica o tipo no qual o método opera. Ele deve ser precedido pelo modificador [this](../../language-reference/keywords/this.md).  
  
4. No código de chamada, adicione uma diretiva `using` para especificar o [namespace](../../language-reference/keywords/namespace.md) que contém a classe do método de extensão.  
  
5. Chame os métodos como se fossem métodos de instância no tipo.  
  
     Observe que o primeiro parâmetro não é especificado pelo código de chamada porque ele representa o tipo no qual o operador está sendo aplicado e o compilador já conhece o tipo do objeto. Você só precisa fornecer argumentos para os parâmetros de 2 até o `n`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir implementa um método de extensão chamado `WordCount` na classe `CustomExtensions.StringExtension`. O método funciona na classe <xref:System.String>, que é especificada como o primeiro parâmetro do método. O namespace `CustomExtensions` é importado para o namespace do aplicativo e o método é chamado dentro do método `Main`.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Os métodos de extensão não apresentam nenhuma vulnerabilidade de segurança específica. Eles nunca podem ser usados para representar os métodos existentes em um tipo, porque todos os conflitos de nome são resolvidos em favor da instância ou do método estático, definidos pelo próprio tipo. Os métodos de extensão não podem acessar nenhum dado particular na classe estendida.  
  
## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Métodos de Extensão](./extension-methods.md)
- [LINQ (Consulta Integrada à Linguagem)](../../linq/linq-in-csharp.md)
- [Classes static e membros de classes static](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)
- [public](../../language-reference/keywords/public.md)
- [this](../../language-reference/keywords/this.md)
- [namespace](../../language-reference/keywords/namespace.md)
