---
title: "Como trabalhar com dicionários usando LINQ to XML (C#) | Microsoft Docs"
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
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1570e4bb0be707d1c27e8bdfc1ef853413d70784
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>Como trabalhar com dicionários usando LINQ to XML (C#)
É conveniente converter variedades de estruturas de dados para XML, e XML de volta para outras estruturas de dados. Este tópico mostra uma implementação específica dessa abordagem geral convertendo <xref:System.Collections.Generic.Dictionary%602> para XML e vice-versa.  
  
## <a name="example"></a>Exemplo  
 Esse exemplo usa uma forma de construção funcional na qual uma consulta projeta novos objetos <xref:System.Xml.Linq.XElement> e a coleção resultante é passada como um argumento para o construtor do objeto <xref:System.Xml.Linq.XElement> raiz.  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 Esse código gera a seguinte saída:  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria um dicionário XML.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 Esse código gera a seguinte saída:  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Consulte também  
 [Projeções e transformações (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
