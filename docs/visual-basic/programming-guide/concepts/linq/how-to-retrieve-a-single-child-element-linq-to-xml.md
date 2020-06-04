---
title: 'Como: recuperar um único elemento filho (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: ab28ddd960374b22f44ac0c8fc7bddfe0608b8c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397837"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="a072a-102">Como recuperar um único elemento filho (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a072a-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a072a-103">Este tópico explica como recuperar um único elemento filho, considerando o nome do elemento filho.</span><span class="sxs-lookup"><span data-stu-id="a072a-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="a072a-104">Quando você souber que o nome do elemento filho e que há apenas um elemento com esse nome, pode ser conveniente recuperar apenas um elemento, em vez de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="a072a-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="a072a-105">O método <xref:System.Xml.Linq.XContainer.Element%2A> retorna o primeiro filho <xref:System.Xml.Linq.XElement> com o <xref:System.Xml.Linq.XName> especificado.</span><span class="sxs-lookup"><span data-stu-id="a072a-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="a072a-106">Se você quiser recuperar um único elemento filho no Visual Basic, uma abordagem comum é usar a propriedade XML e, em seguida, recuperar o primeiro elemento usando a notação do indexador de matriz.</span><span class="sxs-lookup"><span data-stu-id="a072a-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a072a-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a072a-107">Example</span></span>  
 <span data-ttu-id="a072a-108">O exemplo a seguir demonstra o uso do método <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="a072a-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="a072a-109">Este exemplo usa a árvore XML chamada `po` e localiza o primeiro elemento chamado `Comment`.</span><span class="sxs-lookup"><span data-stu-id="a072a-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="a072a-110">O exemplo do Visual Basic mostra o uso da notação do indexador de matriz para recuperar um único elemento.</span><span class="sxs-lookup"><span data-stu-id="a072a-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="a072a-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a072a-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="a072a-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a072a-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="a072a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a072a-113">Example</span></span>  
 <span data-ttu-id="a072a-114">O exemplo a seguir mostra o mesmo código para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="a072a-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="a072a-115">Para obter mais informações, consulte [visão geral de namespaces (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a072a-115">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a072a-116">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica em um namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="a072a-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="a072a-117">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a072a-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a072a-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="a072a-118">See also</span></span>

- [<span data-ttu-id="a072a-119">Eixos LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a072a-119">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
