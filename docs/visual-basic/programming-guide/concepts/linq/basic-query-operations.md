---
title: "Operações de consulta básica (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 87ff9173b5ff72385c8ecdc3ff13735e7be2a21d
ms.lasthandoff: 03/13/2017

---
# <a name="basic-query-operations-visual-basic"></a>Operações de consulta básica (Visual Basic)
Este tópico fornece uma breve introdução a [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressões no Visual Basic e alguns dos tipos típicos de operações que podem ser executadas em uma consulta. Para mais informações, consulte os seguintes tópicos:  
  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [Passo a passo: Escrevendo consultas em Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Especificando a Fonte de Dados (De)  
 Em um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta, a primeira etapa é especificar a fonte de dados que você deseja consultar. Portanto, o `From` cláusula em uma consulta sempre vem em primeiro lugar. Operadores de consulta selecionam e formatar o resultado com base no tipo de origem.  
  
 [!code-vb[VbLINQBasicOps n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 O `From` cláusula Especifica a fonte de dados, `customers`e um *variável de intervalo*, `cust`. A variável de intervalo é como uma variável de iteração do loop, exceto que em uma expressão de consulta, nenhuma iteração real ocorre. Quando a consulta é executada, geralmente usando um `For Each` loop, a variável de intervalo serve como uma referência para cada elemento sucessivo `customers`. Porque o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente. Para obter exemplos de consultas escritas com e sem uma digitação explícita, consulte [relacionamentos de tipo em operações de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Para obter mais informações sobre como usar o `From` cláusula no Visual Basic, consulte [cláusula From](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrando Dados (Onde)  
 Provavelmente, a operação de consulta mais comuns é aplicar um filtro na forma de uma expressão booleana. A consulta retorna apenas os elementos para o qual a expressão for verdadeira. Um `Where` cláusula é usada para executar a filtragem. O filtro especifica quais elementos na fonte de dados para incluir na sequência resultante. No exemplo a seguir, estão incluídos somente aqueles clientes que têm um endereço em Londres.  
  
 [!code-vb[VbLINQBasicOps n º&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 Você pode usar operadores lógicos como `And` e `Or` para combinar expressões de filtro em um `Where` cláusula. Por exemplo, para retornar somente os clientes que são de Londres e cujo nome é Juliana PAEs, use o seguinte código:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Para retornar os clientes de Londres ou Paris, use o seguinte código:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Para obter mais informações sobre como usar o `Where` cláusula no Visual Basic, consulte [cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Ordenando Dados (Ordenar Por)  
 Muitas vezes é conveniente classificar dados retornados em uma ordem específica. O `Order By` cláusula fará com que os elementos na sequência retornada seja classificada em um campo ou campos especificados. Por exemplo, a consulta a seguir classifica os resultados com base no `Name` propriedade. Porque `Name` é uma cadeia de caracteres, os dados retornados serão classificados em ordem alfabética, de À Z.  
  
 [!code-vb[VbLINQBasicOps n º&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 Para ordenar os resultados na ordem inversa, de Z a, use o `Order By...Descending` cláusula. O padrão é `Ascending` quando nenhuma `Ascending` nem `Descending` for especificado.  
  
 Para obter mais informações sobre como usar o `Order By` cláusula no Visual Basic, consulte [cláusula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Selecionando Dados (Selecionar)  
 O `Select` cláusula Especifica o formato e conteúdo de elementos retornados. Por exemplo, você pode especificar se os resultados consistirá em completa `Customer` objetos, apenas um `Customer` propriedade, um subconjunto de propriedades, uma combinação das propriedades de várias fontes de dados ou algum novo tipo de resultado com base em um cálculo. Quando o `Select` cláusula produz algo diferente de uma cópia do elemento de origem, a operação é chamada uma *projeção*.  
  
 Para recuperar uma coleção que consiste em completa `Customer` objetos, selecione a variável de intervalo:  
  
 [!code-vb[VbLINQBasicOps n º&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 Se um `Customer` instância é um objeto grande com muitos campos, e tudo o que você deseja recuperar é o nome, você pode selecionar `cust.Name`, conforme mostrado no exemplo a seguir. Inferência de tipo local reconhece que isso altera o tipo de resultado de uma coleção de `Customer` objetos a uma coleção de cadeias de caracteres.  
  
 [!code-vb[VbLINQBasicOps n º&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 Para selecionar vários campos da fonte de dados, você tem duas opções:  
  
-   No `Select` cláusula, especifique os campos que deseja incluir no resultado. O compilador definirá um tipo anônimo com esses campos como suas propriedades. Para obter mais informações, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Como os elementos retornados no exemplo a seguir são instâncias de um tipo anônimo, não faz referência a tipo por nome em outro lugar no seu código. O nome do tipo designado pelo compilador contém caracteres que não são válidos no código do Visual Basic normal. No exemplo a seguir, os elementos da coleção que é retornado pela consulta em `londonCusts4` são instâncias de um tipo anônimo  
  
     [!code-vb[VbLINQBasicOps n º&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     -ou-  
  
-   Definir um tipo nomeado que contém os campos específicos que você deseja incluir no resultado e criar e inicializar instâncias do tipo de `Select` cláusula. Use esta opção somente se você precisa usar resultados individuais fora da coleção na qual eles são retornados ou se você tiver para passá-las como parâmetros em chamadas de método. O tipo de `londonCusts5` no exemplo a seguir é IEnumerable (Of NamePhone).  
  
     [!code-vb[VbLINQBasicOps&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps n º&8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 Para obter mais informações sobre como usar o `Select` cláusula no Visual Basic, consulte [cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Ingressando Dados (Ingressar e Agrupar Junções)  
 Você pode combinar mais de uma fonte de dados de `From` cláusula de várias maneiras. Por exemplo, o código a seguir usa duas fontes de dados e implicitamente combina propriedades de ambos no resultado. A consulta seleciona os alunos cujos sobrenomes começam com um sinal de vogal.  
  
 [!code-vb[VbLINQBasicOps n º&9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  Você pode executar esse código com a lista de alunos criado em [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 O `Join` palavra-chave é equivalente a um `INNER JOIN` no SQL. Ele combina duas coleções baseadas nos valores de chave de correspondência entre os elementos em duas coleções. A consulta retorna todo ou parte dos elementos da coleção que têm valores de chave correspondentes. Por exemplo, o código a seguir duplica a ação da associação implícita anterior.  
  
 [!code-vb[VbLINQBasicOps n º&10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join`combina coleções em uma única coleção hierárquica, assim como um `LEFT JOIN` no SQL. Para obter mais informações, consulte [cláusula Join](../../../../visual-basic/language-reference/queries/join-clause.md) e [cláusula Join do grupo](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Agrupando Dados (Agrupar Por)  
 Você pode adicionar uma `Group By` cláusula para agrupar os elementos de acordo com um ou mais campos dos elementos de um resultado de consulta. Por exemplo, o código a seguir agrupa os alunos por ano de classe.  
  
 [!code-vb[VbLINQBasicOps n º&11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 Se você executar esse código usando a lista de alunos criado em [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), a saída do `For Each` instrução é:  
  
 Ano: júnior  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Ano: sênior  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Ano: primeiro ano  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 A variação mostrada no código a seguir ordena os anos de classe e, em seguida, os alunos os pedidos em cada ano por sobrenome.  
  
 [!code-vb[VbLINQBasicOps&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 Para obter mais informações sobre `Group By`, consulte [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
