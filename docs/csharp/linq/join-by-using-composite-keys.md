---
title: Unir usando chaves compostas
description: Como unir usando chaves compostas.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f504c9dabcd7ca2d198d58c6d81e1fde1052e3be
ms.lasthandoff: 03/13/2017

---
# <a name="join-by-using-composite-keys"></a>Unir usando chaves compostas

Este exemplo mostra como realizar operações de junção nas quais você deseja usar mais de uma chave para definir uma correspondência. Isso é realizado por meio de uma chave composta. Uma chave composta é criada como um tipo anônimo ou como um tipo nomeado com os valores que você deseja comparar. Se a variável de consulta será transmitida além dos limites do método, use um tipo nomeado que substitui <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> pela chave. Os nomes das propriedades e a ordem em que elas ocorrem, devem ser idênticas em cada chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar uma chave composta para unir dados de três tabelas:  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 A inferência de tipos em chaves compostas depende dos nomes das propriedades nas chaves e da ordem em que elas ocorrem. Se as propriedades nas sequências de origem não têm os mesmos nomes, você deve atribuir novos nomes nas chaves. Por exemplo, se a tabela `Orders` e a tabela `OrderDetails` usaram nomes diferentes para suas colunas, você poderia criar chaves compostas ao atribuir nomes idênticos nos tipos anônimos:  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 As chaves compostas também podem ser usadas em uma cláusula `group`.  

## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)   
 [Cláusula join](../language-reference/keywords/join-clause.md)   
 [Cláusula group](../language-reference/keywords/group-clause.md)
