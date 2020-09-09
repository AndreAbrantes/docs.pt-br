---
title: Eventos de LINQ to XML-LINQ to XML
description: Saiba como usar eventos XML para monitorar alterações em uma árvore XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 755aa1a449e873a2c4f5b17d4df3eee7ecfa9969
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551979"
---
# <a name="linq-to-xml-events-linq-to-xml"></a><span data-ttu-id="765da-103">Eventos de LINQ to XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="765da-103">LINQ to XML Events (LINQ to XML)</span></span>

<span data-ttu-id="765da-104">LINQ to XML eventos permitem que você seja notificado quando uma árvore XML é alterada.</span><span class="sxs-lookup"><span data-stu-id="765da-104">LINQ to XML events enable you to be notified when an XML tree is altered.</span></span>

<span data-ttu-id="765da-105">Você pode adicionar eventos a qualquer instância do <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="765da-105">You can add events to any instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="765da-106">O manipulador de eventos em receberá eventos para alterações ao <xref:System.Xml.Linq.XObject> e a qualquer um dos seus descendentes.</span><span class="sxs-lookup"><span data-stu-id="765da-106">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="765da-107">Por exemplo, você pode adicionar um manipulador de eventos à raiz da árvore, e trata todas as alterações na árvore do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="765da-107">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>

<span data-ttu-id="765da-108">Para obter exemplos de eventos de LINQ to XML, consulte <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="765da-108">For examples of LINQ to XML events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>

## <a name="types-and-events"></a><span data-ttu-id="765da-109">Tipos e eventos</span><span class="sxs-lookup"><span data-stu-id="765da-109">Types and events</span></span>

<span data-ttu-id="765da-110">Você usa os seguintes tipos ao trabalhar com eventos:</span><span class="sxs-lookup"><span data-stu-id="765da-110">You use the following types when working with events:</span></span>

|<span data-ttu-id="765da-111">Type</span><span class="sxs-lookup"><span data-stu-id="765da-111">Type</span></span>|<span data-ttu-id="765da-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="765da-112">Description</span></span>|
|----------|-----------------|
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="765da-113">Especifica o tipo de evento quando um evento é gerado para <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="765da-113">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="765da-114">Fornece dados para os eventos de <xref:System.Xml.Linq.XObject.Changing> e de <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="765da-114">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|

<span data-ttu-id="765da-115">Os seguintes eventos são gerados quando você altera uma árvore XML:</span><span class="sxs-lookup"><span data-stu-id="765da-115">The following events are raised when you modify an XML tree:</span></span>

|<span data-ttu-id="765da-116">Evento</span><span class="sxs-lookup"><span data-stu-id="765da-116">Event</span></span>|<span data-ttu-id="765da-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="765da-117">Description</span></span>|
|-----------|-----------------|
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="765da-118">Ocorre antes deste <xref:System.Xml.Linq.XObject> ou alguns dos seus descendentes são indo alterar.</span><span class="sxs-lookup"><span data-stu-id="765da-118">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="765da-119">Ocorre quando <xref:System.Xml.Linq.XObject> alterar ou alguns dos seus descendentes alterado.</span><span class="sxs-lookup"><span data-stu-id="765da-119">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|

## <a name="example-use-events-to-maintain-a-proper-total-when-items-are-changed"></a><span data-ttu-id="765da-120">Exemplo: usar eventos para manter um total adequado quando os itens forem alterados</span><span class="sxs-lookup"><span data-stu-id="765da-120">Example: Use events to maintain a proper total when items are changed</span></span>

<span data-ttu-id="765da-121">Os eventos são úteis quando você deseja manter algumas informações aggregate em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="765da-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="765da-122">Por exemplo, talvez você queira manter um total de faturas que seja a soma dos itens de linha da nota fiscal.</span><span class="sxs-lookup"><span data-stu-id="765da-122">For example, you may want to maintain an invoice total that's the sum of the line items of the invoice.</span></span> <span data-ttu-id="765da-123">Este exemplo usa eventos para manter o total de todos os elementos filho no elemento complexo `Items`.</span><span class="sxs-lookup"><span data-stu-id="765da-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>

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

```vb
Module Module1
    Dim WithEvents items As XElement = Nothing
    Dim total As XElement = Nothing
    Dim root As XElement = _
            <Root>
                <Total>0</Total>
                <Items></Items>
            </Root>

    Private Sub XObjectChanged( _
            ByVal sender As Object, _
            ByVal cea As XObjectChangeEventArgs) _
            Handles items.Changed
        Select Case cea.ObjectChange
            Case XObjectChange.Add
                If sender.GetType() Is GetType(XElement) Then
                    total.Value = CStr(CInt(total.Value) + _
                            CInt((DirectCast(sender, XElement)).Value))
                End If
                If sender.GetType() Is GetType(XText) Then
                    total.Value = CStr(CInt(total.Value) + _
                            CInt((DirectCast(sender, XText)).Value))
                End If
            Case XObjectChange.Remove
                If sender.GetType() Is GetType(XElement) Then
                    total.Value = CStr(CInt(total.Value) - _
                            CInt((DirectCast(sender, XElement)).Value))
                End If
                If sender.GetType() Is GetType(XText) Then
                    total.Value = CStr(CInt(total.Value) - _
                            CInt((DirectCast(sender, XText)).Value))
                End If
        End Select
        Console.WriteLine("Changed {0} {1}", _
                            sender.GetType().ToString(), _
                            cea.ObjectChange.ToString())
    End Sub

    Sub Main()
        total = root.<Total>(0)
        items = root.<Items>(0)
        items.SetElementValue("Item1", 25)
        items.SetElementValue("Item2", 50)
        items.SetElementValue("Item2", 75)
        items.SetElementValue("Item3", 133)
        items.SetElementValue("Item1", Nothing)
        items.SetElementValue("Item4", 100)
        Console.WriteLine("Total:{0}", CInt(total))
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="765da-124">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="765da-124">This example produces the following output:</span></span>

```output
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