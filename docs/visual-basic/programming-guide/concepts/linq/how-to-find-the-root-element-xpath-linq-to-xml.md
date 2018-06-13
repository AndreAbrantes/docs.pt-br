---
title: 'Como: localizar o elemento raiz (XPath-LINQ para XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: 112be85e8af8fbe31f62ef91db04de72a3793082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641073"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="67ca1-102">Como: localizar o elemento raiz (XPath-LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67ca1-102">How to: Find the Root Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="67ca1-103">Este tópico mostra como obter o elemento raiz com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67ca1-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="67ca1-104">A expressão XPath é:</span><span class="sxs-lookup"><span data-stu-id="67ca1-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="67ca1-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67ca1-105">Example</span></span>  
 <span data-ttu-id="67ca1-106">Este exemplo localiza o elemento raiz.</span><span class="sxs-lookup"><span data-stu-id="67ca1-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="67ca1-107">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="67ca1-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 <span data-ttu-id="67ca1-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="67ca1-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="67ca1-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67ca1-109">See Also</span></span>  
 [<span data-ttu-id="67ca1-110">LINQ to XML para XPath usuários (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67ca1-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
