---
title: Como definir a igualdade de valor para um guia C# de programação de tipo
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 8c911dc1d0aa36ab8e57fb8a77a52d9cec20743c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745387"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Como definir a igualdade de valor para um tipoC# (guia de programação)

Quando você define uma classe ou struct, decide se faz sentido criar uma definição personalizada de igualdade de valor (ou equivalência) para o tipo. Normalmente, você implementa igualdade de valor quando objetos do tipo devem ser adicionados a uma coleção de algum tipo ou quando seu objetivo principal é armazenar um conjunto de campos ou propriedades. Você pode basear sua definição de igualdade de valor em uma comparação de todos os campos e propriedades no tipo ou pode basear a definição em um subconjunto. 

Em ambos os casos, e em classes e estruturas, sua implementação deve seguir as cinco garantias de equivalência (para as regras a seguir, suponha que `x`, `y` e `z` não sejam nulos):  
  
1. `x.Equals(x)` retorna `true`. Isso é chamado de propriedade reflexiva.  
  
2. `x.Equals(y)` retorna o mesmo valor que `y.Equals(x)`. Isso é chamado de propriedade simétrica.  
  
3. se `(x.Equals(y) && y.Equals(z))` retornar `true`, então `x.Equals(z)` retornará `true`. Isso é chamado de propriedade transitiva.  
  
4. Invocações sucessivas de `x.Equals(y)` retornam o mesmo valor, contanto que os objetos referenciados por x e y não sejam modificados.  
  
5. Qualquer valor não nulo não é igual a NULL. No entanto, o CLR verifica se há NULL em todas as chamadas de método e gera um `NullReferenceException` se a referência de `this` fosse nula. Portanto, `x.Equals(y)` gera uma exceção quando `x` é nulo. Isso interrompe as regras 1 ou 2, dependendo do argumento para `Equals`.
 
 Qualquer struct que você define já tem uma implementação padrão de igualdade de valor que ele herda da substituição <xref:System.ValueType?displayProperty=nameWithType> do método <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>. Essa implementação usa a reflexão para examinar todos os campos e propriedades no tipo. Embora essa implementação produza resultados corretos, ela é relativamente lenta em comparação com uma implementação personalizada escrita especificamente para o tipo.  
  
 Os detalhes de implementação para a igualdade de valor são diferentes para classes e struct. No entanto, as classes e structs exigem as mesmas etapas básicas para implementar a igualdade:  
  
1. Substitua o método de <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> [virtual](../../language-reference/keywords/virtual.md) . Na maioria dos casos, sua implementação de `bool Equals( object obj )` deve apenas chamar o método `Equals` específico do tipo que é a implementação da interface <xref:System.IEquatable%601?displayProperty=nameWithType>. (Consulte a etapa 2.)  
  
2. Implemente a interface <xref:System.IEquatable%601?displayProperty=nameWithType> fornecendo um método `Equals` específico do tipo. Isso é o local em que a comparação de equivalência de fato é realizada. Por exemplo, você pode decidir definir a igualdade comparando apenas um ou dois campos em seu tipo. Não lance exceções de `Equals`. Para classes somente: esse método deve examinar somente os campos que são declarados na classe. Ele deve chamar `base.Equals` para examinar os campos que estão na classe base. (Não faça isso se o tipo herda diretamente de <xref:System.Object>, pois a implementação <xref:System.Object> de <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> executa uma verificação de igualdade de referência.)  
  
3. Opcional, mas recomendado: sobrecarregue os operadores [==](../../language-reference/operators/equality-operators.md#equality-operator-) e [!=](../../language-reference/operators/equality-operators.md#inequality-operator-).  
  
4. Substitua <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> para que os dois objetos que têm a igualdade de valor produzam o mesmo código hash.  
  
5. Opcional: para dar suporte às definições para “maior que” ou “menor que”, implemente a interface <xref:System.IComparable%601> para seu tipo e também sobrecarregue os operadores [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) e [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-).  
  
 O primeiro exemplo a seguir mostra uma implementação da classe. O segundo exemplo mostra uma implementação de struct.  

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como implementar a igualdade de valor em uma classe (tipo de referência).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 Em classes (tipo de referência), a implementação padrão de ambos os métodos <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> executa uma comparação de igualdade de referência, não uma verificação de igualdade de valor. Quando um implementador substitui o método virtual, o objetivo é fornecer semântica de igualdade de valor.  
  
 Os operadores `==` e `!=` podem ser usados com classes, mesmo se a classe não sobrecarregá-los. No entanto, o comportamento padrão é executar uma verificação de igualdade de referência. Em uma classe, se você sobrecarregar o método `Equals`, você deverá sobrecarregar os operadores `==` e `!=`, mas isso não é necessário.  

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como implementar a igualdade de valor em um struct (tipo de valor):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Para estruturas, a implementação padrão de <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (que é a versão substituída em <xref:System.ValueType?displayProperty=nameWithType>) executa uma verificação de igualdade de valor por meio de reflexão para comparar os valores de cada campo no tipo. Quando um implementador substitui o método `Equals` virtual em uma estrutura, a finalidade é fornecer uma maneira mais eficiente de executar a verificação de igualdade de valor e, opcionalmente, basear a comparação em algum subconjunto dos campos ou propriedades do struct.  
  
 Os operadores [==](../../language-reference/operators/equality-operators.md#equality-operator-) e [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) não podem operar em um struct a menos que o struct explicitamente os sobrecarregue.  
  
## <a name="see-also"></a>Veja também

- [Comparações de igualdade](equality-comparisons.md)
- [Guia de programação em C#](../index.md)
