---
title: Eventos LINQ to XML
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368810"
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="af8a4-102">Eventos de LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af8a4-102">LINQ to XML Events (Visual Basic)</span></span>
<span data-ttu-id="af8a4-103">Eventos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permitem que você seja notificado quando uma árvore XML é modificada.</span><span class="sxs-lookup"><span data-stu-id="af8a4-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="af8a4-104">Você pode adicionar eventos a uma instância de qualquer <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="af8a4-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="af8a4-105">O manipulador de eventos em receberá eventos para alterações ao <xref:System.Xml.Linq.XObject> e a qualquer um dos seus descendentes.</span><span class="sxs-lookup"><span data-stu-id="af8a4-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="af8a4-106">Por exemplo, você pode adicionar um manipulador de eventos à raiz da árvore, e trata todas as alterações na árvore do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="af8a4-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="af8a4-107">Para exemplos de eventos de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], consulte <xref:System.Xml.Linq.XObject.Changing> e <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="af8a4-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="af8a4-108">Tipos e eventos</span><span class="sxs-lookup"><span data-stu-id="af8a4-108">Types and Events</span></span>  
 <span data-ttu-id="af8a4-109">Você usa os seguintes tipos ao trabalhar com eventos:</span><span class="sxs-lookup"><span data-stu-id="af8a4-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="af8a4-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="af8a4-110">Type</span></span>|<span data-ttu-id="af8a4-111">Description</span><span class="sxs-lookup"><span data-stu-id="af8a4-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="af8a4-112">Especifica o tipo de evento quando um evento é gerado para <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="af8a4-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="af8a4-113">Fornece dados para os eventos de <xref:System.Xml.Linq.XObject.Changing> e de <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="af8a4-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="af8a4-114">Os seguintes eventos são gerados quando você altera uma árvore XML:</span><span class="sxs-lookup"><span data-stu-id="af8a4-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="af8a4-115">Evento</span><span class="sxs-lookup"><span data-stu-id="af8a4-115">Event</span></span>|<span data-ttu-id="af8a4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="af8a4-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="af8a4-117">Ocorre antes deste <xref:System.Xml.Linq.XObject> ou alguns dos seus descendentes são indo alterar.</span><span class="sxs-lookup"><span data-stu-id="af8a4-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="af8a4-118">Ocorre quando <xref:System.Xml.Linq.XObject> alterar ou alguns dos seus descendentes alterado.</span><span class="sxs-lookup"><span data-stu-id="af8a4-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af8a4-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="af8a4-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="af8a4-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="af8a4-120">Description</span></span>  
 <span data-ttu-id="af8a4-121">Os eventos são úteis quando você deseja manter algumas informações aggregate em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="af8a4-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="af8a4-122">Por exemplo, você pode querer mantém um total de fatura que é a soma das linhas de item de fatura.</span><span class="sxs-lookup"><span data-stu-id="af8a4-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="af8a4-123">Este exemplo usa eventos para manter o total de todos os elementos filho no elemento complexo `Items`.</span><span class="sxs-lookup"><span data-stu-id="af8a4-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="af8a4-124">Código</span><span class="sxs-lookup"><span data-stu-id="af8a4-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="af8a4-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="af8a4-125">Comments</span></span>  
 <span data-ttu-id="af8a4-126">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="af8a4-126">This code produces the following output:</span></span>  
  
```console  
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
  
## <a name="see-also"></a><span data-ttu-id="af8a4-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="af8a4-127">See also</span></span>

- [<span data-ttu-id="af8a4-128">Programação de LINQ to XML avançada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af8a4-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
