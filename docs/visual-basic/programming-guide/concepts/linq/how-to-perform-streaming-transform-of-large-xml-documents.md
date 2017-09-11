---
title: "Como: executar o Streaming de transformação de grandes documentos XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 3d954cc9-4b3c-4b47-8132-ff7541cff53b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 730039a85c8c72b9379617cb4b3c019028c3a1e9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-visual-basic"></a><span data-ttu-id="f22fd-102">Como: executar o Streaming de transformação de grandes documentos XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f22fd-102">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>
<span data-ttu-id="f22fd-103">Às vezes você precisa transformar grandes arquivos XML e escrever seu aplicativo de modo que os requisitos de memória do aplicativo sejam previsíveis.</span><span class="sxs-lookup"><span data-stu-id="f22fd-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="f22fd-104">Se você tentar preencher uma árvore XML com um arquivo XML muito grande, seu uso de memória será proporcional ao tamanho do arquivo (isto é, excessivo).</span><span class="sxs-lookup"><span data-stu-id="f22fd-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="f22fd-105">Portanto, você deve usar uma técnica de streaming em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f22fd-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="f22fd-106">As técnicas de streaming são melhor aplicadas em situações onde você precisa processar o documento de origem apenas uma vez e você pode processar os elementos na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="f22fd-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="f22fd-107">Determinados operadores de consulta padrão, como <xref:System.Linq.Enumerable.OrderBy%2A>, iteram sua origem, coletar todos os dados, classificá-los e, em seguida, geram finalmente o primeiro item na sequência.</xref:System.Linq.Enumerable.OrderBy%2A></span><span class="sxs-lookup"><span data-stu-id="f22fd-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="f22fd-108">Observe que se você usar um operador de consulta que materializa sua origem antes de gerar o primeiro item, você não manterá um requisito pequeno de memória para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f22fd-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="f22fd-109">Mesmo se você usar a técnica descrita no [como: transmitir fragmentos XML com acesso a informações de cabeçalho (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), se você tentar montar uma árvore XML que contém o documento transformado, uso será muito grande de memória.</span><span class="sxs-lookup"><span data-stu-id="f22fd-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="f22fd-110">Há duas principais abordagens.</span><span class="sxs-lookup"><span data-stu-id="f22fd-110">There are two main approaches.</span></span> <span data-ttu-id="f22fd-111">Uma abordagem é usar as características de processamento adiado de <xref:System.Xml.Linq.XStreamingElement>.</xref:System.Xml.Linq.XStreamingElement></span><span class="sxs-lookup"><span data-stu-id="f22fd-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="f22fd-112">Outra abordagem é criar um <xref:System.Xml.XmlWriter>e usar os recursos de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para gravar os elementos para <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="f22fd-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="f22fd-113">Este tópico demonstra as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="f22fd-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f22fd-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f22fd-114">Example</span></span>  
 <span data-ttu-id="f22fd-115">O exemplo a seguir cria o exemplo na [como: transmitir fragmentos XML com acesso a informações de cabeçalho (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="f22fd-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="f22fd-116">Este exemplo usa os recursos de execução adiada de <xref:System.Xml.Linq.XStreamingElement>para transmitir a saída.</xref:System.Xml.Linq.XStreamingElement></span><span class="sxs-lookup"><span data-stu-id="f22fd-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="f22fd-117">Este exemplo pode transformar um documento muito grande mantendo um requisito pequeno de memória.</span><span class="sxs-lookup"><span data-stu-id="f22fd-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="f22fd-118">Observe que o eixo personalizado (`StreamCustomerItem`) é escrito especificamente para esperar um documento que tem os elementos `Customer`, `Name` e `Item`, e que esses elementos serão organizados como no documento Source.xml a seguir.</span><span class="sxs-lookup"><span data-stu-id="f22fd-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="f22fd-119">Uma implementação mais robusta, no entanto, seria preparada para analisar um documento inválido.</span><span class="sxs-lookup"><span data-stu-id="f22fd-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="f22fd-120">Veja a seguir o documento de origem, Source.xml:</span><span class="sxs-lookup"><span data-stu-id="f22fd-120">The following is the source document, Source.xml:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root = New XStreamingElement("Root",  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
            )  
        root.Save("Test.xml")  
        Console.WriteLine(My.Computer.FileSystem.ReadAllText("Test.xml"))  
    End Sub  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="f22fd-121">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="f22fd-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="f22fd-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f22fd-122">Example</span></span>  
 <span data-ttu-id="f22fd-123">O exemplo a seguir também se baseia no exemplo em [como: transmitir fragmentos XML com acesso a informações de cabeçalho (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span><span class="sxs-lookup"><span data-stu-id="f22fd-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="f22fd-124">Este exemplo usa o recurso de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para gravar os elementos para <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="f22fd-124">This example uses the capability of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="f22fd-125">Este exemplo pode transformar um documento muito grande mantendo um requisito pequeno de memória.</span><span class="sxs-lookup"><span data-stu-id="f22fd-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="f22fd-126">Observe que o eixo personalizado (`StreamCustomerItem`) é escrito especificamente para esperar um documento que tem os elementos `Customer`, `Name` e `Item`, e que esses elementos serão organizados como no documento Source.xml a seguir.</span><span class="sxs-lookup"><span data-stu-id="f22fd-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="f22fd-127">Uma implementação mais robusta, no entanto, validaria o documento de origem com um XSD ou seria preparada para analisar um documento inválido.</span><span class="sxs-lookup"><span data-stu-id="f22fd-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="f22fd-128">Este exemplo usa o mesmo documento de origem, Source.xml, como o exemplo anterior neste tópico.</span><span class="sxs-lookup"><span data-stu-id="f22fd-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="f22fd-129">Ele também produz exatamente a mesma saída.</span><span class="sxs-lookup"><span data-stu-id="f22fd-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="f22fd-130">Usando <xref:System.Xml.Linq.XStreamingElement>para transmitir a saída que XML é preferencial em relação a gravar a <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XStreamingElement></span><span class="sxs-lookup"><span data-stu-id="f22fd-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim srcTree =  
            From el In New StreamCustomerItem("Source.xml")  
            Select <Item>  
                       <Customer><%= el.Parent.<Name>.Value %></Customer>  
                       <%= el.<Key> %>  
                   </Item>  
  
        Dim xws = New Xml.XmlWriterSettings()  
        xws.OmitXmlDeclaration = True  
        xws.Indent = True  
        Using xw = Xml.XmlWriter.Create("Output.xml", xws)  
            xw.WriteStartElement("Root")  
            For Each el In srcTree  
                el.WriteTo(xw)  
            Next  
            xw.WriteEndElement()  
        End Using  
  
        Dim s = My.Computer.FileSystem.ReadAllText("Output.xml")  
        Console.WriteLine(s)  
    End Sub  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="f22fd-131">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="f22fd-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f22fd-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f22fd-132">See Also</span></span>  
 [<span data-ttu-id="f22fd-133">Avançada LINQ to XML programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f22fd-133">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
