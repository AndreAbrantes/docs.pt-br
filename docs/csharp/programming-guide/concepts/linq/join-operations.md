---
title: JoinOperações (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76867999"
---
# <a name="join-operations-c"></a>Operações de junção (C#)

Uma *junção* de duas fontes de dados é a associação de objetos em uma fonte de dados, com objetos que compartilham um atributo comum em outra fonte de dados.  
  
 A junção é uma operação importante em consultas que têm como destino fontes de dados cujas relações entre si não podem ser seguidas diretamente. Na programação orientada a objeto, isso pode significar uma correlação entre objetos que não são modelados, como a direção retroativa de uma relação unidirecional. Um exemplo de uma relação unidirecional é uma classe Cliente que tem uma propriedade do tipo Cidade, mas a classe Cidade ainda não tem uma propriedade que é uma coleção de objetos Cliente. Se você tem uma lista de objetos Cidade e você quer encontrar todos os clientes em cada cidade, você pode usar uma operação de junção para encontrá-los.  
  
 Os métodos de junção fornecidos na estrutura do LINQ são <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A>. Esses métodos executam junção por igualdade ou junções que correspondem duas fontes de dados com base na igualdade de suas chaves. (Para comparação, o Transact-SQL suporta unir operadores que não os "iguais", por exemplo, o operador 'menos que'.) Em termos de banco <xref:System.Linq.Enumerable.Join%2A> de dados relacionais, implementa uma adesão interna, um tipo de adesão em que apenas os objetos que têm uma correspondência no outro conjunto de dados são devolvidos. O método <xref:System.Linq.Enumerable.GroupJoin%2A> não tem equivalente direto em termos de banco de dados relacional, mas ele implementa um superconjunto de junções internas e junções externas esquerdas. Uma junção externa esquerda é uma junção que retorna cada elemento da primeira (esquerda) fonte de dados, mesmo que ele não tenha elementos correlacionados na outra fonte de dados.  
  
 A ilustração a seguir mostra uma visão conceitual de dois conjuntos e os elementos dentro desses conjuntos que estão incluídos em uma junção interna ou externa à esquerda.  
  
 ![Dois círculos sobrepostos mostrando interna/externa.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Une duas sequências com base nas funções de seletor de chave e extrai pares de valores.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Une duas sequências baseadas em funções de seletor de chave e agrupa as correspondências resultantes para cada elemento.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta
  
### Join  
  
O exemplo a `join … in … on … equals …` seguir usa a cláusula para juntar duas seqüências com base no valor específico:
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

O exemplo a `join … in … on … equals … into …` seguir usa a cláusula para juntar duas seqüências com base no valor específico e agrupa as correspondências resultantes para cada elemento:
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Linq>
- [Visão geral de operadores de consulta padrão (C#)](./standard-query-operators-overview.md)
- [Tipos Anônimos](../../classes-and-structs/anonymous-types.md)
- [Formular junções e consultas entre produtos](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [aderir cláusula](../../../language-reference/keywords/join-clause.md)
- [Joinusando chaves compostas](../../../linq/join-by-using-composite-keys.md)
- [Como juntar conteúdo de arquivos diferentes (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Ordenar os resultados de uma cláusula join](../../../linq/order-the-results-of-a-join-clause.md)
- [Executar operações de junção personalizadas](../../../linq/perform-custom-join-operations.md)
- [Executar junções agrupadas](../../../linq/perform-grouped-joins.md)
- [Executar junções internas](../../../linq/perform-inner-joins.md)
- [Executar junções externas esquerdas](../../../linq/perform-left-outer-joins.md)
- [Como preencher coleções de objetos de várias fontes (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
