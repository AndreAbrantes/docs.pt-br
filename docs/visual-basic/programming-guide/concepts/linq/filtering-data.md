---
title: Filtragem de dados (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3751164b7697b63937611c77d9fda0e2873625d8
ms.lasthandoff: 03/13/2017

---
# <a name="filtering-data-visual-basic"></a>Filtragem de dados (Visual Basic)
Filtragem refere-se a operação de restringir o conjunto de resultados para conter apenas os elementos que satisfazem uma condição especificada. Ele também é conhecido como seleção.  
  
 A ilustração a seguir mostra os resultados de uma sequência de caracteres de filtragem. O predicado para a operação de filtragem Especifica que o caractere deve ser 'A'.  
  
 ![Operação de filtragem de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")  
  
 Os métodos de operador de consulta padrão que executam a seleção são listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OfType|Seleciona valores, dependendo de sua capacidade de ser convertido em um tipo especificado.|Não aplicável.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|Where|Seleciona valores com base em uma função de predicado.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>Exemplo de sintaxe de expressão de consulta  
 O exemplo a seguir usa o `Where` para filtrar em uma matriz essas cadeias de caracteres com um comprimento específico.  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq></xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Onde cláusula](../../../../visual-basic/language-reference/queries/where-clause.md)   
 [Como: Filtrar resultados de consulta](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)   
 [Como: consultar metadados de um Assembly com reflexão (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)   
 [Como: consultar arquivos com um atributo especificado ou o nome (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)   
 [Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
