---
title: Como testar a igualdade de referência (Identidade) - Guia de Programação C#
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 77ce2ef0ccf47d619134c120101ba2aa04f485e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699048"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Como testar a igualdade de referência (Identidade) (Guia de Programação C#)
Não é necessário implementar qualquer lógica personalizada para dar suporte a comparações de igualdade de referência em seus tipos. Essa funcionalidade é fornecida para todos os tipos pelo método estático <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>.  
  
 O exemplo a seguir mostra como determinar se duas variáveis têm *igualdade de referência*, que significa que elas se referem ao mesmo objeto na memória.  
  
 O exemplo também mostra por que <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> sempre retorna `false` para tipos de valor e por que você não deve usar <xref:System.Object.ReferenceEquals%2A> para determinar igualdade de cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 A implementação de `Equals` na classe base universal <xref:System.Object?displayProperty=nameWithType> também realiza uma verificação de igualdade de referência, mas é melhor não usar isso, porque, se uma classe substituir o método, os resultados poderão não ser o que você espera. O mesmo é verdadeiro para os operadores `==` e `!=`. Quando eles estiverem operando em tipos de referência, o comportamento padrão de `==` e `!=` é realizar uma verificação de igualdade de referência. No entanto, as classes derivadas podem sobrecarregar o operador para executar uma verificação de igualdade de valor. Para minimizar o potencial de erro, será melhor usar sempre <xref:System.Object.ReferenceEquals%2A> quando for necessário determinar se os dois objetos têm igualdade de referência.  
  
 Cadeias de caracteres constantes dentro do mesmo assembly sempre são internalizadas pelo runtime. Ou seja, apenas uma instância de cada cadeia de caracteres literal única é mantida. No entanto, o runtime não garante que cadeias de caracteres criadas em runtime sejam internalizadas nem garante que duas de cadeias de caracteres constantes iguais em diferentes assemblies sejam internalizadas.  
  
## <a name="see-also"></a>Confira também

- [Comparações de Igualdade](./equality-comparisons.md)
