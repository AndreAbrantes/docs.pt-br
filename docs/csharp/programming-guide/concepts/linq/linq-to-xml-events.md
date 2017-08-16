---
title: Eventos LINQ to XML (C#) | Microsoft Docs
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
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
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
ms.openlocfilehash: f19439004a9551f5e13588201ca3aaf201620681
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-events-c"></a>Eventos LINQ to XML (C#)
Eventos [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permitem que você seja notificado quando uma árvore XML é modificada.  
  
 É possível adicionar eventos a uma instância de qualquer <xref:System.Xml.Linq.XObject>. O manipulador de eventos, então, receberá eventos para alterações nesse <xref:System.Xml.Linq.XObject> e em qualquer um dos seus descendentes. Por exemplo, você pode adicionar um manipulador de eventos à raiz da árvore, e trata todas as alterações na árvore do manipulador de eventos.  
  
 Para obter exemplos de eventos [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], consulte <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Tipos e eventos  
 Você usa os seguintes tipos ao trabalhar com eventos:  
  
|Tipo|Descrição|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Especifica o tipo de evento quando um evento é gerado para um <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Fornece dados para os eventos <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed>.|  
  
 Os seguintes eventos são gerados quando você altera uma árvore XML:  
  
|Evento|Descrição|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Ocorre logo antes que este <xref:System.Xml.Linq.XObject> ou qualquer um de seus descendentes seja alterado.|  
|<xref:System.Xml.Linq.XObject.Changed>|Ocorre quando um <xref:System.Xml.Linq.XObject> ou qualquer um de seus descendentes é alterado.|  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Os eventos são úteis quando você deseja manter algumas informações aggregate em uma árvore XML. Por exemplo, você pode querer mantém um total de fatura que é a soma das linhas de item de fatura. Este exemplo usa eventos para manter o total de todos os elementos filho no elemento complexo `Items`.  
  
### <a name="code"></a>Código  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a>Comentários  
 Esse código gera a seguinte saída:  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Programação LINQ to XML avançada (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
