---
title: A pré-compilação atomização de XName objetos (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: c0e75afa797d2b20f32fc55e6c19d0c1593d174c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740783"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="dca84-102">Pré-atomização de objetos XName (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dca84-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="dca84-103">Uma maneira para melhorar o desempenho em LINQ to XML é pré-compilação atomizar objetos de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="dca84-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="dca84-104">A pré-atomização significa que você atribui uma cadeia de caracteres a um objeto <xref:System.Xml.Linq.XName> antes de criar a árvore XML usando os construtores das classes <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dca84-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="dca84-105">Em seguida, em vez de passar uma cadeia de caracteres para o construtor, que usaria a conversão implícita de cadeia de caracteres a <xref:System.Xml.Linq.XName>, você passa o objeto inicializado de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="dca84-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="dca84-106">Isso melhora o desempenho quando você cria uma grande árvore XML em que os nomes específicos são repetidos.</span><span class="sxs-lookup"><span data-stu-id="dca84-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="dca84-107">Para fazer isso, você declarar e inicializar objetos de <xref:System.Xml.Linq.XName> antes que você construa a árvore XML e em seguida, usar objetos de <xref:System.Xml.Linq.XName> em vez de especificar cadeias de caracteres para nomes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="dca84-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="dca84-108">Essa técnica pode produzir ganhos significativos de desempenho se você estiver criando um grande número de elementos ou atributos () com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="dca84-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>

<span data-ttu-id="dca84-109">Você deve testar a pré-compilação atomização com seu cenário para decidir se você usar o.</span><span class="sxs-lookup"><span data-stu-id="dca84-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>

## <a name="example"></a><span data-ttu-id="dca84-110">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="dca84-110">Example</span></span>

<span data-ttu-id="dca84-111">O exemplo a seguir demonstra este:</span><span class="sxs-lookup"><span data-stu-id="dca84-111">The following example demonstrates this:</span></span>

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

<span data-ttu-id="dca84-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="dca84-112">This example produces the following output:</span></span>

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

<span data-ttu-id="dca84-113">O exemplo a seguir mostra a mesma técnica onde o documento XML é em um namespace:</span><span class="sxs-lookup"><span data-stu-id="dca84-113">The following example shows the same technique where the XML document is in a namespace:</span></span>

```vb
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim root1 As XName = aw + "Root"
Dim data As XName = aw + "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XAttribute(XNamespace.Xmlns + "aw", aw),
                          New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

<span data-ttu-id="dca84-114">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="dca84-114">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

<span data-ttu-id="dca84-115">O exemplo a seguir é mais semelhante ao que você provavelmente encontrará no mundo real.</span><span class="sxs-lookup"><span data-stu-id="dca84-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="dca84-116">Nesse exemplo, o conteúdo do elemento é fornecido por uma consulta:</span><span class="sxs-lookup"><span data-stu-id="dca84-116">In this example, the content of the element is supplied by a query:</span></span>

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"
  
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root2 As New XElement(root1, From i In Enumerable.Range(1, 100000)
                                 Select New XElement(data, New XAttribute(ID, i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```  

<span data-ttu-id="dca84-117">O exemplo anterior executa melhor do que o exemplo, em que os nomes não são atomizados passos:</span><span class="sxs-lookup"><span data-stu-id="dca84-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a><span data-ttu-id="dca84-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dca84-118">See also</span></span>

- [<span data-ttu-id="dca84-119">Desempenho (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dca84-119">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)
- [<span data-ttu-id="dca84-120">Objetos XName e XNamespace (LINQ to XML) atomáveis (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dca84-120">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>](atomized-xname-and-xnamespace-objects-linq-to-xml.md)
