---
title: Como qualificar o elemento XML e os nomes de atributo XML
description: Este artigo mostra como qualificar os nomes de elementos XML e atributos XML em documentos XML.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 6c29e03d9ce28e5b0abc68a5d7e8d82f4485ac93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83378409"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="212a9-103">Como qualificar o elemento XML e os nomes de atributo XML</span><span class="sxs-lookup"><span data-stu-id="212a9-103">How to qualify XML element and XML attribute names</span></span>

<span data-ttu-id="212a9-104">Os namespaces XML contidos por instâncias da <xref:System.Xml.Serialization.XmlSerializerNamespaces> classe devem estar em conformidade com a especificação do World Wide Web Consortium (W3C) chamada [namespaces em XML](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="212a9-104">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="212a9-105">Os namespaces em XML fornecem um método para qualificar os nomes de elementos XML e atributos XML em documentos XML.</span><span class="sxs-lookup"><span data-stu-id="212a9-105">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="212a9-106">Um nome qualificado é composto por um prefixo e por um nome local separados por dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="212a9-106">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="212a9-107">O prefixo funciona somente como espaço reservado; é mapeado para um URI que especifica um namespace.</span><span class="sxs-lookup"><span data-stu-id="212a9-107">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="212a9-108">A combinação do namespace de URI gerenciado universalmente e o nome local produz um nome que é garantido para ser exclusivo universalmente.</span><span class="sxs-lookup"><span data-stu-id="212a9-108">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="212a9-109">Ao criar uma instância do `XmlSerializerNamespaces` e adicionar os pares de namespace ao objeto, você pode especificar os prefixos usados em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="212a9-109">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="212a9-110">Para criar nomes qualificados em um documento XML</span><span class="sxs-lookup"><span data-stu-id="212a9-110">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="212a9-111">Criar uma instância da classe `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="212a9-111">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="212a9-112">Adicione todos os prefixos e pares de namespace ao `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="212a9-112">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="212a9-113">Aplique o atributo `System.Xml.Serialization` apropriado a cada membro ou classe que o <xref:System.Xml.Serialization.XmlSerializer> deve serializar em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="212a9-113">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

    <span data-ttu-id="212a9-114">Os atributos disponíveis são: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute> e <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="212a9-114">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="212a9-115">Configure a propriedade `Namespace` de cada atributo para um dos valores de namespace do `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="212a9-115">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="212a9-116">Passe o `XmlSerializerNamespaces` para o método `Serialize` do `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="212a9-116">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="212a9-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="212a9-117">Example</span></span>

<span data-ttu-id="212a9-118">O exemplo a seguir cria um `XmlSerializerNamespaces` e adiciona dois prefixos e pares de namespace ao objeto.</span><span class="sxs-lookup"><span data-stu-id="212a9-118">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="212a9-119">O código cria um `XmlSerializer` que é usado para serializar uma instância da classe `Books`.</span><span class="sxs-lookup"><span data-stu-id="212a9-119">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="212a9-120">O código chama o método `Serialize` com o `XmlSerializerNamespaces`, permitindo que o XML contenha namespaces com prefixo.</span><span class="sxs-lookup"><span data-stu-id="212a9-120">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Module Program

    Public Sub Main()
        SerializeObject("XmlNamespaces.xml")
    End Sub

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Module

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book
    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Program
{
    public static void Main()
    {
        SerializeObject("XmlNamespaces.xml");
    }

    public static void SerializeObject(string filename)
    {
        var mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        var myNamespaces = new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        var myBook = new Book();
        myBook.TITLE = "A Book Title";
        var myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        var myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter, myBooks, myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}

public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}
```

## <a name="see-also"></a><span data-ttu-id="212a9-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="212a9-121">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="212a9-122">A ferramenta de definição de esquema XML e a serialização XML</span><span class="sxs-lookup"><span data-stu-id="212a9-122">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="212a9-123">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="212a9-123">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="212a9-124">Classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="212a9-124">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="212a9-125">Atributos que controlam a serialização de XML</span><span class="sxs-lookup"><span data-stu-id="212a9-125">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="212a9-126">Como especificar um nome de elemento alternativo para um fluxo XML</span><span class="sxs-lookup"><span data-stu-id="212a9-126">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="212a9-127">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="212a9-127">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="212a9-128">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="212a9-128">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
