---
title: Como recuperar o valor raso de um elemento (C#)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347444"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Como recuperar o valor raso de um elemento (C#)
Este tópico mostra como obter o valor raso de um elemento. O valor raso é o valor do elemento específico somente, diferentemente de valor maior, que inclui os valores de todos os elementos descendentes concatenados em uma única cadeia de caracteres.  
  
 Quando você recupera um valor de elemento usando conversão ou propriedade de <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> , você recupera o valor maior. Para recuperar o valor raso, você pode usar o método de extensão de `ShallowValue`, conforme mostrado no exemplo a seguir. Recuperar o valor raso é útil quando você deseja selecionar elementos com base no conteúdo.  
  
 O exemplo a seguir declara um método de extensão que recupera o valor raso de um elemento. Use o método de extensão em uma consulta para listar todos os elementos que contém um valor calculado.  
  
## <a name="example"></a>Exemplo  
 O seguinte arquivo de texto, Report.xml, é a fonte para esse exemplo.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 Esse exemplo gera a saída a seguir:  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Confira também

- [Eixos do LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
