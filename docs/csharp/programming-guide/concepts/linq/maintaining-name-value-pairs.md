---
title: Mantendo pares nome-valor (C#) | Microsoft Docs
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
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fda5e083584a57245a83bdf8c09d31e7ffdb2d5a
ms.lasthandoff: 03/13/2017


---
# <a name="maintaining-namevalue-pairs-c"></a>Mantendo pares nome-valor (C#)
Muitos aplicativos devem manter informações que são melhor armazenadas como pares de valor/nome. Essas informações podem ser informações de configuração ou configurações globais. O [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] contém alguns métodos que facilitam o trabalho de manter um conjunto de pares de valor/nome. É possível manter informações como atributos ou como um conjunto de elementos filho.  
  
 Uma das diferenças entre manter as informações como atributos ou como elementos filho é que os atributos possuem a restrição de que pode existir apenas um atributo com um nome específico para um elemento. Essa limitação não se aplica aos elementos filho.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue e SetElementValue  
 Os dois métodos que facilitam a manutenção de pares nome-valor são <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> e <xref:System.Xml.Linq.XElement.SetElementValue%2A>. Esses dois métodos possuem semântica semelhante.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> pode adicionar, modificar ou remover atributos de um elemento.  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com um nome de um atributo que não existe, o método criará um novo atributo e o adicionará ao elemento especificado.  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com um nome de um atributo existente e com algum conteúdo especificado, o conteúdo do atributo será substituído pelo conteúdo especificado.  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com um nome de um atributo existente e especificar null para o conteúdo, o atributo será removido de seu pai.  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> pode adicionar, modificar ou remover elementos filho de um elemento.  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com um nome de um elemento filho que não existe, o método criará um novo elemento e o adicionará ao elemento especificado.  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com um nome de um elemento existente e algum conteúdo especificado, os conteúdos do elemento serão substituídos pelo conteúdo especificado.  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com um nome de um elemento existente e especificar null para o conteúdo, o elemento será removido de seu pai.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um elemento sem atributos. Ele usa então o método <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> para criar e manter uma lista de pares nome-valor.  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um elemento sem elementos filho. Ele usa então o método <xref:System.Xml.Linq.XElement.SetElementValue%2A> para criar e manter uma lista de pares nome-valor.  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>   
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>   
 [Modificando árvores XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
