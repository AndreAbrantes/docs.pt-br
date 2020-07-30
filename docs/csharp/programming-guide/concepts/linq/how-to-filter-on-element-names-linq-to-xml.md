---
title: Como filtrar em nomes de elementos (LINQ to XML) (C#)
description: Saiba como filtrar o nome do elemento ao chamar um método que retorna IEnumerable de XElement.
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: be660a69b8d860ad907661ce17002379b8842121
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301743"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="432ba-103">Como filtrar em nomes de elementos (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="432ba-103">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="432ba-104">Quando você chamar um dos métodos que <xref:System.Collections.Generic.IEnumerable%601> de retorno de <xref:System.Xml.Linq.XElement>, você pode filtrar no nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="432ba-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="432ba-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="432ba-105">Example</span></span>  
 <span data-ttu-id="432ba-106">Este exemplo retorna uma coleção de descendentes que é filtrada para conter somente descendentes com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="432ba-106">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="432ba-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="432ba-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="432ba-108">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="432ba-108">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="432ba-109">Os outros métodos que <xref:System.Collections.Generic.IEnumerable%601> de retorno de coleções de <xref:System.Xml.Linq.XElement> segue o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="432ba-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="432ba-110">Suas assinaturas são semelhantes a <xref:System.Xml.Linq.XContainer.Elements%2A> e a <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="432ba-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="432ba-111">O seguinte é a lista completa dos métodos semelhantes que tenham assinaturas de método:</span><span class="sxs-lookup"><span data-stu-id="432ba-111">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="432ba-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="432ba-112">Example</span></span>  
 <span data-ttu-id="432ba-113">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="432ba-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="432ba-114">Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="432ba-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="432ba-115">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica em um namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="432ba-115">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="432ba-116">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="432ba-116">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="432ba-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="432ba-117">See also</span></span>

- [<span data-ttu-id="432ba-118">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="432ba-118">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
