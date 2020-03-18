---
title: Como recuperar um único atributo (LINQ para XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 830a7be24702b6037ac62471060fbe49d8ded598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168707"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="15ec2-102">Como recuperar um único atributo (LINQ para XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="15ec2-102">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="15ec2-103">Este tópico explica como recuperar um único atributo de um elemento, dado o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="15ec2-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="15ec2-104">Isso é útil para gravar as expressões de consulta onde você deseja localizar um elemento que possui um atributo específico.</span><span class="sxs-lookup"><span data-stu-id="15ec2-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="15ec2-105">O método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement> retorna <xref:System.Xml.Linq.XAttribute> com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="15ec2-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15ec2-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15ec2-106">Example</span></span>  
 <span data-ttu-id="15ec2-107">O exemplo a seguir usa o método <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="15ec2-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="15ec2-108">Este exemplo localiza os descendentes na árvore chamada `Phone`, e localiza o atributo chamado `type`.</span><span class="sxs-lookup"><span data-stu-id="15ec2-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="15ec2-109">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="15ec2-109">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="15ec2-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15ec2-110">Example</span></span>  
 <span data-ttu-id="15ec2-111">Se você deseja recuperar o valor do atributo, você pode convertê-lo, exatamente como você faz para com objetos de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="15ec2-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="15ec2-112">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="15ec2-112">The following example demonstrates this.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="15ec2-113">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="15ec2-113">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="15ec2-114">fornece operadores cast explícitos para a classe <xref:System.Xml.Linq.XAttribute> para `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` e `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="15ec2-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15ec2-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15ec2-115">Example</span></span>  
 <span data-ttu-id="15ec2-116">O exemplo a seguir mostra o mesmo código para um atributo que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="15ec2-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="15ec2-117">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="15ec2-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 <span data-ttu-id="15ec2-118">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="15ec2-118">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="15ec2-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="15ec2-119">See also</span></span>

- [<span data-ttu-id="15ec2-120">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="15ec2-120">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
