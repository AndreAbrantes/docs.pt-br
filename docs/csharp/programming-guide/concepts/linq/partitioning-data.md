---
title: Particionando dados (C#)
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
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2f1690dac93d5e74f1305bd457f8bc749bec5449
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="partitioning-data-c"></a>Particionando dados (C#)
Particionamento em LINQ refere-se à operação de dividir uma sequência de entrada em duas seções sem reorganizar os elementos e, depois, retornar uma das seções.  
  
 A ilustração a seguir mostra os resultados de três operações de particionamento diferentes em uma sequência de caracteres. A primeira operação retorna os três primeiros elementos na sequência. A segunda operação ignora os três primeiros elementos e retorna os elementos restantes. A terceira operação ignora os dois primeiros elementos na sequência e retorna os três elementos seguintes.  
  
 ![Operações de particionamento de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Os métodos de operador de consulta padrão que particionam sequências estão listados na seção a seguir.  
  
## <a name="operators"></a>Operadores  
  
|Nome do operador|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|Ignora elementos até uma posição especificada na sequência.|Não aplicável.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|SkipWhile|Ignora elementos com base em uma função de predicado até que um elemento não satisfaça a condição.|Não aplicável.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|Take|Aceita elementos até uma posição especificada na sequência.|Não aplicável.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|TakeWhile|Aceita elementos com base em uma função de predicado até que um elemento não satisfaça a condição.|Não aplicável.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

