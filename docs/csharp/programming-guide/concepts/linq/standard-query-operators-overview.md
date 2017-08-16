---
title: "Visão geral de operadores de consulta padrão (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5b03c85a298b3864a91a7052ca80cf3714ba98fe
ms.lasthandoff: 03/13/2017

---
# <a name="standard-query-operators-overview-c"></a>Visão geral de operadores de consulta padrão (C#)
Os *operadores de consulta padrão* são os métodos que formam o padrão LINQ. A maioria desses métodos opera em sequências, em que uma sequência é um objeto cujo tipo implementa a interface <xref:System.Collections.Generic.IEnumerable%601> ou a <xref:System.Linq.IQueryable%601>. Os operadores de consulta padrão fornecem recursos de consulta incluindo filtragem, projeção, agregação, classificação e muito mais.  
  
 Há dois conjuntos de operadores de consulta padrão LINQ, um que opera em objetos do tipo <xref:System.Collections.Generic.IEnumerable%601> e o outro que opera em objetos do tipo <xref:System.Linq.IQueryable%601>. Os métodos que compõem cada conjunto são membros estáticos das classes <xref:System.Linq.Enumerable> e <xref:System.Linq.Queryable>, respectivamente. Eles são definidos como *métodos de extensão* do tipo nos quais operam. Isso significa que eles podem ser chamados usando a sintaxe de método estático ou sintaxe de método de instância.  
  
 Além disso, vários métodos de operador de consulta padrão operam em tipos diferentes dos baseados em <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>. O tipo <xref:System.Linq.Enumerable> define dois métodos que operam em objetos do tipo <xref:System.Collections.IEnumerable>. Esses métodos, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> e <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, permitem que você habilite uma coleção não parametrizada ou não genérica, para ser consultada no padrão LINQ. Eles fazem isso criando uma coleção de objetos fortemente tipada. A classe <xref:System.Linq.Queryable> define dois métodos semelhantes, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> e <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, que operam em objetos do tipo <xref:System.Linq.Queryable>.  
  
 Os operadores de consulta padrão são diferentes no momento de sua execução, dependendo de se eles retornam um valor singleton ou uma sequência de valores. Esses métodos que retornam um valor singleton (por exemplo,<xref:System.Linq.Enumerable.Average%2A> e <xref:System.Linq.Enumerable.Sum%2A>) são executados imediatamente. Os métodos que retornam uma sequência adiam a execução da consulta e retornam um objeto enumerável.  
  
 No caso de métodos que operam em coleções na memória, ou seja, os métodos que estendem <xref:System.Collections.Generic.IEnumerable%601>, o objeto enumerável retornado captura o argumento que foi passado para o método. Quando esse objeto é enumerado, a lógica do operador de consulta é empregada e os resultados da consulta são retornados.  
  
 Por outro lado, os métodos que estendem <xref:System.Linq.IQueryable%601> não implementam nenhum comportamento de consulta, mas criam uma árvore de expressão que representa a consulta a ser executada. O processamento de consulta é tratado pelo objeto <xref:System.Linq.IQueryable%601> de origem.  
  
 Chamadas para métodos de consulta podem ser encadeadas em uma consulta, o que permite que consultas se tornem arbitrariamente complexas.  
  
 O exemplo de código a seguir demonstra como os operadores de consulta padrão podem ser usados para obter informações sobre uma sequência.  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Sintaxe de expressão de consulta  
 Alguns dos operadores de consulta padrão mais usados têm uma sintaxe de palavra-chave de linguagem C# e Visual Basic dedicada que possibilita que eles sejam chamados como parte de uma *expressão* *de consulta*. Para obter mais informações sobre operadores de consulta padrão que têm palavras-chave dedicadas e suas sintaxes correspondentes, consulte [Sintaxe de expressão de consulta para operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Estendendo os operadores de consulta padrão  
 Você pode aumentar o conjunto de operadores de consulta padrão criando métodos específicos de domínio apropriados para o domínio ou tecnologia de destino. Você também pode substituir os operadores de consulta padrão por suas próprias implementações que fornecem serviços adicionais, como avaliação remota, conversão de consulta e otimização. Consulte <xref:System.Linq.Enumerable.AsEnumerable%2A> para encontrar um exemplo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Os links a seguir levam você a tópicos que fornecem informações adicionais sobre os vários operadores de consulta padrão com base na funcionalidade.  
  
 [Classificando dados (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [Operações de conjunto (C#)](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtrando dados (C#)](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [Operações de quantificador (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Operações de projeção (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [Particionando dados (C#)](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Operações de junção (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [Agrupando dados (C#)](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [Operações de geração (C#)](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [Operações de Igualdade (C#)](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [Operações de elemento (C#)](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [Convertendo Tipos de Dados (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Operações de concatenação (C#)](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Operações de agregação (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable>   
 <xref:System.Linq.Queryable>   
 [Introdução a consultas LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)   
 [Sintaxe de expressão de consulta para operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)   
 [Classificação de operadores de consulta padrão pelo modo de execução (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)   
 [Métodos de Extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
