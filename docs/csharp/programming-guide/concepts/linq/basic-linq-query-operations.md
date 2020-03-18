---
title: Operações de consulta LINQ básica (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 91c038303c1ad7c2530964d3102aae49090c4c2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635932"
---
# <a name="basic-linq-query-operations-c"></a>Operações de consulta LINQ básica (C#)
Este tópico fornece uma breve introdução às expressões de consulta LINQ e alguns dos tipos típicos de operações que você executa em uma consulta. Informações mais detalhadas estão nos tópicos a seguir:  
  
 [Expressões de Consulta LINQ](../../../linq/index.md)  
  
 [Visão geral de operadores de consulta padrão (C#)](./standard-query-operators-overview.md)  
  
 [Passo a passo: escrevendo consultas em C#](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> Se já estiver familiarizado com uma linguagem de consulta como SQL ou XQuery, você poderá ignorar a maior parte deste tópico. Leia sobre`from` a "cláusula" na próxima seção para saber sobre a ordem das cláusulas nas expressões de consulta LINQ.  
  
## <a name="obtaining-a-data-source"></a>Obtendo uma Fonte de Dados  
 Em uma consulta LINQ, o primeiro passo é especificar a fonte de dados. No C#, como na maioria das linguagens de programação, uma variável deve ser declarada antes que possa ser usada. Em uma consulta LINQ, `from` a cláusula vem primeiro para`customers`introduzir a fonte de dados ( ) e a *variável de intervalo* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 A variável de intervalo é como a variável de iteração em um loop `foreach`, mas nenhuma iteração real ocorre em uma expressão de consulta. Quando a consulta é executada, a variável de intervalo servirá como uma referência para cada elemento sucessivo em `customers`. Uma vez que o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente. Variáveis de intervalo adicionais podem ser introduzidas por uma cláusula `let`. Para obter mais informações, consulte [Cláusula let](../../../language-reference/keywords/let-clause.md).  
  
> [!NOTE]
> Para fontes de dados não genéricas, como <xref:System.Collections.ArrayList>, a variável de intervalo deve ser tipada explicitamente. Para obter mais informações, consulte [Como consultar uma ArrayList com LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) e [a partir de cláusula](../../../language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtragem  
 Provavelmente, a operação de consulta mais comum é aplicar um filtro no formulário de uma expressão booliana. O filtro faz com que a consulta retorne apenas os elementos para os quais a expressão é verdadeira. O resultado é produzido usando a cláusula `where`. O filtro em vigor especifica os elementos a serem excluídos da sequência de origem. No exemplo a seguir, somente os `customers` que têm um endereço em Londres são retornados.  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 Você pode usar os operadores lógicos `AND` e `OR` de C# para aplicar quantas expressões de filtro forem necessárias na cláusula `where`. Por exemplo, para retornar somente clientes de "Londres" `AND` cujo nome seja "Devon", você escreveria o seguinte código:  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 Para retornar clientes de Londres ou Paris, você escreveria o seguinte código:  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 Para obter mais informações, consulte [onde a cláusula](../../../language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Ordering  
 Muitas vezes é conveniente classificar os dados retornados. A cláusula `orderby` fará com que os elementos na sequência retornada sejam classificados de acordo com o comparador padrão para o tipo que está sendo classificado. Por exemplo, a consulta a seguir pode ser estendida para classificar os resultados com base na propriedade `Name`. Como `Name` é uma cadeia de caracteres, o comparador padrão executa uma classificação em ordem alfabética de A a Z.  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 Para ordenar os resultados na ordem inversa, de Z para a, use a cláusula `orderby…descending`.  
  
 Para obter mais informações, consulte [Cláusula orderby](../../../language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Agrupamento  
 A cláusula `group` permite agrupar seus resultados com base em uma chave que você especificar. Por exemplo, você pode especificar que os resultados sejam agrupados segundo o `City`, de modo que todos os clientes de Londres ou Paris fiquem em grupos individuais. Nesse caso, `cust.City` é a chave.  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 Quando você terminar uma consulta com um cláusula `group`, seus resultados assumirão a forma de uma lista de listas. Cada elemento na lista é um objeto que tem um membro `Key` e uma lista dos elementos que estão agrupados sob essa chave. Quando itera em uma consulta que produz uma sequência de grupos, você deve usar um loop `foreach` aninhado. O loop externo itera em cada grupo e o loop interno itera nos membros de cada grupo.  
  
 Se precisar consultar os resultados de uma operação de grupo, você poderá usar a palavra-chave `into` para criar um identificador que pode ser consultado ainda mais. A consulta a seguir retorna apenas os grupos que contêm mais de dois clientes:  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 Para obter mais informações, consulte [Cláusula group](../../../language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Adição  
 Operações de junção criam associações entre sequências que não são modeladas explicitamente nas fontes de dados. Por exemplo, você pode executar uma junção para localizar todos os clientes e distribuidores que têm o mesmo local. No LINQ, a `join` cláusula sempre funciona contra coleções de objetos em vez de tabelas de banco de dados diretamente.  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 No LINQ, você não `join` precisa usar tantas vezes quanto no SQL, porque as chaves estrangeiras no LINQ são representadas no modelo de objeto como propriedades que possuem uma coleção de itens. Por exemplo, um objeto `Customer` que contém uma coleção de objetos `Order`. Em vez de executar uma junção, você pode acessar os pedidos usando notação de ponto:  
  
```csharp
from order in Customer.Orders...  
```  
  
 Para obter mais informações, consulte [a cláusula de adesão](../../../language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Selecionando (Projeções)  
 A cláusula `select` produz os resultados da consulta e especifica a "forma" ou o tipo de cada elemento retornado. Por exemplo, você pode especificar se os resultados consistirão em objetos `Customer` completos, apenas um membro, um subconjunto de membros ou algum tipo de resultado completamente diferente com base em um cálculo ou na criação de um novo objeto. Quando a cláusula `select` produz algo diferente de uma cópia do elemento de origem, a operação é chamada de *projeção*. O uso de projeções para transformar dados é uma poderosa capacidade de expressões de consulta LINQ. Para obter mais informações, consulte [Transformações de dados com LINQ (C#)](./data-transformations-with-linq.md) e [Cláusula select](../../../language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Confira também

- [Expressões de Consulta LINQ](../../../linq/index.md)
- [Passo a passo: escrevendo consultas em C#](./walkthrough-writing-queries-linq.md)
- [Palavras-chave de consulta (LINQ)](../../../language-reference/keywords/query-keywords.md)
- [Tipos Anônimos](../../classes-and-structs/anonymous-types.md)
