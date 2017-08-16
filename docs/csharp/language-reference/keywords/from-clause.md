---
title: "Cláusula from (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- from_CSharpKeyword
- from
dev_langs:
- CSharp
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8634e7bd7f3c3110b42d8fc64e7ebef88b4ad8c7
ms.lasthandoff: 03/13/2017

---
# <a name="from-clause-c-reference"></a>Cláusula from (Referência de C#)
Uma expressão de consulta deve começar com uma cláusula `from`. Além disso, uma expressão de consulta pode conter subconsultas, que também começam com uma cláusula `from`. A cláusula `from` especifica o seguinte:  
  
-   A fonte de dados na qual a consulta ou subconsulta será executada.  
  
-   Uma *variável de intervalo* local que representa cada elemento na sequência de origem.  
  
 A variável de intervalo e a fonte de dados são fortemente tipadas. A fonte de dados referenciada na cláusula `from` deve ter um tipo de <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> ou um tipo derivado, como <xref:System.Linq.IQueryable%601>.  
  
 No exemplo a seguir, `numbers` é a fonte de dados e `num` é a variável de intervalo. Observe que ambas as variáveis são fortemente tipadas, mesmo com o uso da palavra-chave [var](../../../csharp/language-reference/keywords/var.md).  
  
 [!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]  
  
## <a name="the-range-variable"></a>A Variável de Intervalo  
 O compilador infere que o tipo da variável de intervalo quando a fonte de dados implementa <xref:System.Collections.Generic.IEnumerable%601>. Por exemplo, se a fonte tem um tipo de `IEnumerable<Customer>`, então, a variável de intervalo será inferida como `Customer`. O tipo deve ser especificado explicitamente somente quando a fonte for um tipo `IEnumerable` não genérico, como <xref:System.Collections.ArrayList>. Para obter mais informações, consulte [Como Consultar um ArrayList com LINQ](http://msdn.microsoft.com/library/c318b79a-fa4d-4de3-b62d-c1162beb267e).  
  
 No exemplo anterior, `num` é inferido como do tipo `int`. Como a variável de intervalo é fortemente tipada, é possível chamar métodos nela ou usá-la em outras operações. Por exemplo, em vez de gravar `select num`, grave `select num.ToString()` para fazer com que a expressão de consulta retorne uma sequência de cadeias de caracteres em vez de números inteiros. Também é possível gravar `select n + 10` para fazer com que a expressão retorne a sequência 14, 11, 13, 12, 10. Para obter mais informações, consulte [cláusula select](../../../csharp/language-reference/keywords/select-clause.md).  
  
 A variável de intervalo é como uma variável de iteração em uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md), com a exceção de uma diferença muito importante: na verdade, uma variável de intervalo nunca armazena dados da fonte. É apenas uma conveniência sintática que habilita a consulta a descrever o que ocorrerá quando ela for executada. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="compound-from-clauses"></a>Cláusulas from compostas  
 Em alguns casos, cada elemento na sequência de origem pode ser uma sequência ou conter uma sequência. Por exemplo, a fonte de dados pode ser um `IEnumerable<Student>` em que cada objeto do aluno na sequência contenha uma lista de resultados de avaliações. Para acessar a lista interna dentro de cada elemento `Student`, use cláusulas compostas `from`. A técnica é parecida com o uso de instruções [foreach](../../../csharp/language-reference/keywords/foreach-in.md) aninhadas. É possível adicionar cláusulas [where](../../../csharp/language-reference/keywords/partial-method.md) ou [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) a qualquer cláusula `from` para filtrar os resultados. O exemplo a seguir mostra uma sequência de objetos `Student`, em cada um contém uma `List` interna de inteiros que representam de resultados de avaliações. Para acessar a lista interna, use uma cláusula composta `from`. É possível inserir cláusulas entre as duas cláusulas `from`, se necessário.  
  
 [!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]  
  
## <a name="using-multiple-from-clauses-to-perform-joins"></a>Usando Várias Cláusulas from para Realizar Uniões  
 Uma cláusula composta `from` é usada para acessar coleções internas em uma fonte de dados única. No entanto, uma consulta também pode conter várias cláusulas `from` que geram consultas complementares de fontes de dados independentes. Essa técnica habilita a execução de determinados tipos de operações de união que não são possíveis por meio da [cláusula join](../../../csharp/language-reference/keywords/join-clause.md).  
  
 A exemplo a seguir mostra como duas cláusulas `from` podem ser usadas para formar uma união cruzada completa de duas fontes de dados.  
  
 [!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]  
  
 Para obter mais informações sobre as operações de união que usam várias cláusulas `from`, consulte [Como Executar Operações de União Personalizadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Palavras-chave de Consulta (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
