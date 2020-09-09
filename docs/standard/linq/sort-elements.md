---
title: Como classificar elementos-LINQ to XML
description: Saiba como escrever uma consulta que classifica seus resultados.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: c2d7915aacf0c41e99581fa8b5cc397bcaf5c612
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551999"
---
# <a name="how-to-sort-elements-linq-to-xml"></a><span data-ttu-id="12ed8-103">Como classificar elementos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="12ed8-103">How to sort elements (LINQ to XML)</span></span>

<span data-ttu-id="12ed8-104">Você pode classificar seus resultados ao consultar XML.</span><span class="sxs-lookup"><span data-stu-id="12ed8-104">You can sort your results when you query XML.</span></span> <span data-ttu-id="12ed8-105">Este artigo fornece dois exemplos: o primeiro classifica os resultados de XML que *não estão* em um namespace e o segundo faz a mesma classificação, mas para XML que *está* em um namespace.</span><span class="sxs-lookup"><span data-stu-id="12ed8-105">This article provides two examples: the first sorts results for XML that *isn't* in a namespace, and the second does the same sort, but for XML that *is* in a namespace.</span></span>

## <a name="example-write-a-query-that-sorts-its-results"></a><span data-ttu-id="12ed8-106">Exemplo: escrever uma consulta que classifica seus resultados</span><span class="sxs-lookup"><span data-stu-id="12ed8-106">Example: Write a query that sorts its results</span></span>

<span data-ttu-id="12ed8-107">Este exemplo mostra como escrever uma consulta que classifica seus resultados.</span><span class="sxs-lookup"><span data-stu-id="12ed8-107">This example shows how to write a query that sorts its results.</span></span> <span data-ttu-id="12ed8-108">Ele usa arquivo XML de exemplo de documento XML [: dados numéricos](sample-xml-file-numerical-data.md).</span><span class="sxs-lookup"><span data-stu-id="12ed8-108">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> prices =
    from el in root.Elements("Data")
    let price = (decimal)el.Element("Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim prices As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let price = Convert.ToDecimal(el.<Price>.Value) _
    Order By (price) _
    Select price
For Each el As Decimal In prices
    Console.WriteLine(el)
Next
```

<span data-ttu-id="12ed8-109">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12ed8-109">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="example-write-a-query-in-a-namespace-that-sorts-its-results"></a><span data-ttu-id="12ed8-110">Exemplo: gravar uma consulta em um namespace que classifica seus resultados</span><span class="sxs-lookup"><span data-stu-id="12ed8-110">Example: Write a query in a namespace that sorts its results</span></span>

<span data-ttu-id="12ed8-111">O exemplo a seguir mostra a mesma consulta para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="12ed8-111">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="12ed8-112">Ele usa [arquivo XML de exemplo de documento XML: dados numéricos em um namespace](sample-xml-file-numerical-data-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="12ed8-112">It uses XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="12ed8-113">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="12ed8-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace aw = "http://www.adatum.com";
IEnumerable<decimal> prices =
    from el in root.Elements(aw + "Data")
    let price = (decimal)el.Element(aw + "Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim prices As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let price = Convert.ToDecimal(el.<Price>.Value) _
            Order By (price) _
            Select price
        For Each el As Decimal In prices
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

<span data-ttu-id="12ed8-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12ed8-114">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="see-also"></a><span data-ttu-id="12ed8-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="12ed8-115">See also</span></span>

- [<span data-ttu-id="12ed8-116">Classificando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="12ed8-116">Sorting Data (C#)</span></span>](../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="12ed8-117">Classificando dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12ed8-117">Sorting Data (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="12ed8-118">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12ed8-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)