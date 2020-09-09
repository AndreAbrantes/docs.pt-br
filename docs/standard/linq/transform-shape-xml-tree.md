---
title: Como transformar a forma de uma árvore XML-LINQ to XML
description: Você pode usar a construção funcional para alterar a forma de um documento XML; ou seja, para manter os dados, mas alterar itens como nomes de elementos, nomes de atributo e hierarquia.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 6b4127571d5a6a9fa8e92079424dd19eaf5a2f29
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551925"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-linq-to-xml"></a><span data-ttu-id="c0b03-103">Como transformar a forma de uma árvore XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c0b03-103">How to transform the shape of an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="c0b03-104">A *forma* de um documento XML refere-se aos seus nomes de elemento, nomes de atributo e às características de sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="c0b03-104">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>

<span data-ttu-id="c0b03-105">Às vezes você precisará alterar a forma de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="c0b03-105">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="c0b03-106">Por exemplo, você pode ter que enviar um documento XML existente para outro sistema que requer nomes diferentes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="c0b03-106">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="c0b03-107">Você pode examinar o documento, excluir e renomeando elementos conforme necessário, mas usando funcionais resultados de compilação em um código mais legível e mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="c0b03-107">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="c0b03-108">Para obter mais informações sobre a construção funcional, consulte [construção funcional](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="c0b03-108">For more information about functional construction, see [Functional construction](functional-construction.md).</span></span>

<span data-ttu-id="c0b03-109">O primeiro exemplo neste artigo altera a organização de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="c0b03-109">The first example in this article changes the organization of an XML document.</span></span> <span data-ttu-id="c0b03-110">Mover elementos complexos de um local na árvore para outro.</span><span class="sxs-lookup"><span data-stu-id="c0b03-110">It moves complex elements from one location in the tree to another.</span></span>

<span data-ttu-id="c0b03-111">O segundo exemplo cria um documento XML cuja forma difere do documento de origem.</span><span class="sxs-lookup"><span data-stu-id="c0b03-111">The second example creates an XML document whose shape differs from that of the source document.</span></span> <span data-ttu-id="c0b03-112">Ele omite alguns elementos, renomeia outros e altera a capitalização dos nomes dos elementos.</span><span class="sxs-lookup"><span data-stu-id="c0b03-112">It omits some elements, renames others, and changes the casing of the element names.</span></span>

## <a name="example-use-embedded-query-expressions-to-change-the-shape-of-an-xml-tree"></a><span data-ttu-id="c0b03-113">Exemplo: usar expressões de consulta inseridas para alterar a forma de uma árvore XML</span><span class="sxs-lookup"><span data-stu-id="c0b03-113">Example: Use embedded query expressions to change the shape of an XML tree</span></span>

<span data-ttu-id="c0b03-114">O exemplo a seguir altera a forma de um arquivo XML usando expressões de consulta inseridas.</span><span class="sxs-lookup"><span data-stu-id="c0b03-114">The following example changes the shape of an XML file using embedded query expressions.</span></span>

<span data-ttu-id="c0b03-115">O documento XML de origem deste exemplo, [arquivo XML de exemplo: Customers e Orders](sample-xml-file-customers-orders.md), contém um `Customers` elemento sob o `Root` elemento que contém todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="c0b03-115">The source XML document for this example, [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="c0b03-116">Também contém um elemento de `Orders` no elemento de `Root` que contém todos os pedidos.</span><span class="sxs-lookup"><span data-stu-id="c0b03-116">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="c0b03-117">O exemplo cria uma nova árvore XML na qual os pedidos de cada cliente estão contidos em um `Orders` elemento dentro do `Customer` elemento.</span><span class="sxs-lookup"><span data-stu-id="c0b03-117">The example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="c0b03-118">O documento original também contém um `CustomerID` elemento no `Order` elemento; esse elemento é omitido da nova árvore.</span><span class="sxs-lookup"><span data-stu-id="c0b03-118">The original document also contains a `CustomerID` element in the `Order` element; this element is omitted from the new tree.</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");
XElement newCustOrd =
    new XElement("Root",
        from cust in co.Element("Customers").Elements("Customer")
        select new XElement("Customer",
            cust.Attributes(),
            cust.Elements(),
            new XElement("Orders",
                from ord in co.Element("Orders").Elements("Order")
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")
                select new XElement("Order",
                    ord.Attributes(),
                    ord.Element("EmployeeID"),
                    ord.Element("OrderDate"),
                    ord.Element("RequiredDate"),
                    ord.Element("ShipInfo")
                )
            )
        )
    );
Console.WriteLine(newCustOrd);
```

 ```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim newCustOrd = _
    <Root>
        <%= From cust In co.<Customers>.<Customer> _
            Select _
            <Customer>
                <%= cust.Attributes() %>
                <%= cust.Elements() %>
                <Orders>
                    <%= From ord In co.<Orders>.<Order> _
                        Where ord.<CustomerID>.Value = cust.@CustomerID _
                        Select _
                        <Order>
                            <%= ord.Attributes() %>
                            <%= ord.<EmployeeID> %>
                            <%= ord.<OrderDate> %>
                            <%= ord.<RequiredDate> %>
                            <%= ord.<ShipInfo> %>
                        </Order> _
                    %>
                </Orders>
            </Customer> _
        %>
    </Root>
Console.WriteLine(newCustOrd)
```

<span data-ttu-id="c0b03-119">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0b03-119">This example produces the following output:</span></span>

```xml
<Root>
  <Customer CustomerID="GREAL">
    <CompanyName>Great Lakes Food Market</CompanyName>
    <ContactName>Howard Snyder</ContactName>
    <ContactTitle>Marketing Manager</ContactTitle>
    <Phone>(503) 555-7555</Phone>
    <FullAddress>
      <Address>2732 Baker Blvd.</Address>
      <City>Eugene</City>
      <Region>OR</Region>
      <PostalCode>97403</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
  <Customer CustomerID="HUNGC">
    <CompanyName>Hungry Coyote Import Store</CompanyName>
    <ContactName>Yoshi Latimer</ContactName>
    <ContactTitle>Sales Representative</ContactTitle>
    <Phone>(503) 555-6874</Phone>
    <Fax>(503) 555-2376</Fax>
    <FullAddress>
      <Address>City Center Plaza 516 Main St.</Address>
      <City>Elgin</City>
      <Region>OR</Region>
      <PostalCode>97827</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
  ...
</Root>
```

## <a name="example-create-a-document-whose-shape-differs-from-that-of-the-source-document"></a><span data-ttu-id="c0b03-120">Exemplo: criar um documento cuja forma difere da do documento de origem</span><span class="sxs-lookup"><span data-stu-id="c0b03-120">Example: Create a document whose shape differs from that of the source document</span></span>

<span data-ttu-id="c0b03-121">Este exemplo renomeia alguns elementos e converte alguns atributos para elementos.</span><span class="sxs-lookup"><span data-stu-id="c0b03-121">This example renames some elements and converts some attributes to elements.</span></span> <span data-ttu-id="c0b03-122">Ele chama `ConvertAddress` , que retorna uma lista de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="c0b03-122">It calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="c0b03-123">O argumento para o método é uma consulta que determina o elemento complexo de `Address` onde o atributo de `Type` tem um valor de `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="c0b03-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span> <span data-ttu-id="c0b03-124">O exemplo usa arquivo XML de exemplo de documento XML [: ordem de compra típica](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="c0b03-124">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
static IEnumerable<XElement> ConvertAddress(XElement add)
{
    List<XElement> fragment = new List<XElement>() {
        new XElement("NAME", (string)add.Element("Name")),
        new XElement("STREET", (string)add.Element("Street")),
        new XElement("CITY", (string)add.Element("City")),
        new XElement("ST", (string)add.Element("State")),
        new XElement("POSTALCODE", (string)add.Element("Zip")),
        new XElement("COUNTRY", (string)add.Element("Country"))
    };
    return fragment;
}

static void Main(string[] args)
{
    XElement po = XElement.Load("PurchaseOrder.xml");
    XElement newPo = new XElement("PO",
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),
        ConvertAddress(
            (from el in po.Elements("Address")
            where (string)el.Attribute("Type") == "Shipping"
            select el)
            .First()
        )
    );
    Console.WriteLine(newPo);
}
```

```vb
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)
    Dim fragment = New List(Of XElement)
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)
    fragment.Add(<ST><%= add.<State>.Value %></ST>)
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)
    Return fragment
End Function

Sub Main()
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")
    Dim newPo As XElement = _
        <PO>
            <ID><%= po.@PurchaseOrderNumber %></ID>
            <DATE><%= CDate(po.@OrderDate) %></DATE>
            <%= _
                ConvertAddress( _
                (From el In po.<Address> _
                Where el.@Type = "Shipping" _
                Select el) _
                .First() _
                ) _
            %>
        </PO>
    Console.WriteLine(newPo)
End Sub
```

<span data-ttu-id="c0b03-125">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0b03-125">This example produces the following output:</span></span>

```xml
<PO>
  <ID>99503</ID>
  <DATE>1999-10-20T00:00:00</DATE>
  <NAME>Ellen Adams</NAME>
  <STREET>123 Maple Street</STREET>
  <CITY>Mill Valley</CITY>
  <ST>CA</ST>
  <POSTALCODE>10999</POSTALCODE>
  <COUNTRY>USA</COUNTRY>
</PO>
```

## <a name="see-also"></a><span data-ttu-id="c0b03-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0b03-126">See also</span></span>

- [<span data-ttu-id="c0b03-127">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0b03-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)