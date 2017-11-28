---
title: "Como localizar um único descendente usando o método de descendentes (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6dc90262318f5f31c4236318f87393749295a18a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="6f693-102">Como localizar um único descendente usando o método de descendentes (C#)</span><span class="sxs-lookup"><span data-stu-id="6f693-102">How to: Find a Single Descendant Using the Descendants Method (C#)</span></span>
<span data-ttu-id="6f693-103">Você pode usar o método de eixo <xref:System.Xml.Linq.XContainer.Descendants%2A> para rapidamente escrever código para localizar um único elemento nomeado exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="6f693-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="6f693-104">Essa técnica é especialmente útil quando você quer localizar um descendente específico com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="6f693-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="6f693-105">Você pode escrever o código para navegar para o elemento desejado, mas geralmente é mais rápido e fácil escrever código usando o eixo <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f693-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f693-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f693-106">Example</span></span>  
 <span data-ttu-id="6f693-107">Este exemplo usa o operador padrão de consulta <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f693-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <GrandChild1>GC1 Value</GrandChild1>  
  </Child1>  
  <Child2>  
    <GrandChild2>GC2 Value</GrandChild2>  
  </Child2>  
  <Child3>  
    <GrandChild3>GC3 Value</GrandChild3>  
  </Child3>  
  <Child4>  
    <GrandChild4>GC4 Value</GrandChild4>  
  </Child4>  
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="6f693-108">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="6f693-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="6f693-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f693-109">Example</span></span>  
 <span data-ttu-id="6f693-110">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="6f693-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6f693-111">Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="6f693-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
  <aw:Child1>  
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
  </aw:Child1>  
  <aw:Child2>  
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
  </aw:Child2>  
  <aw:Child3>  
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
  </aw:Child3>  
  <aw:Child4>  
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
  </aw:Child4>  
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="6f693-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="6f693-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f693-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f693-113">See Also</span></span>  
 [<span data-ttu-id="6f693-114">Consultas básicas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6f693-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
