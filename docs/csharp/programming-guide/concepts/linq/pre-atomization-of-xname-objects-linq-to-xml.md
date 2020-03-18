---
title: Pré-atomização de objetos XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591500"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="4925f-102">Pré-atomização de objetos XName (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4925f-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4925f-103">Uma maneira para melhorar o desempenho em LINQ to XML é pré-compilação atomizar objetos de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="4925f-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="4925f-104">a pré-compilação atomização significa que você atribuir uma cadeia de caracteres a um objeto de <xref:System.Xml.Linq.XName> antes de criar a árvore XML usando os construtores de classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4925f-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="4925f-105">Em seguida, em vez de passar uma cadeia de caracteres para o construtor, que usaria a conversão implícita de cadeia de caracteres a <xref:System.Xml.Linq.XName>, você passa o objeto inicializado de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="4925f-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="4925f-106">Isso melhora o desempenho quando você cria uma grande árvore XML em que os nomes específicos são repetidos.</span><span class="sxs-lookup"><span data-stu-id="4925f-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="4925f-107">Para fazer isso, você declarar e inicializar objetos de <xref:System.Xml.Linq.XName> antes que você construa a árvore XML e em seguida, usar objetos de <xref:System.Xml.Linq.XName> em vez de especificar cadeias de caracteres para nomes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="4925f-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="4925f-108">Essa técnica pode produzir ganhos significativos de desempenho se você estiver criando um grande número de elementos ou atributos () com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4925f-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="4925f-109">Você deve testar a pré-compilação atomização com seu cenário para decidir se você usar o.</span><span class="sxs-lookup"><span data-stu-id="4925f-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4925f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4925f-110">Example</span></span>  
 <span data-ttu-id="4925f-111">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="4925f-111">The following example demonstrates this.</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="4925f-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="4925f-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="4925f-113">O exemplo a seguir mostra a mesma técnica onde o documento XML é em um namespace:</span><span class="sxs-lookup"><span data-stu-id="4925f-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="4925f-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="4925f-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="4925f-115">O exemplo a seguir é mais semelhante ao que você provavelmente encontrará no mundo real.</span><span class="sxs-lookup"><span data-stu-id="4925f-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="4925f-116">Nesse exemplo, o conteúdo do elemento é fornecido por uma consulta:</span><span class="sxs-lookup"><span data-stu-id="4925f-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 <span data-ttu-id="4925f-117">O exemplo anterior executa melhor do que o exemplo, em que os nomes não são atomizados passos:</span><span class="sxs-lookup"><span data-stu-id="4925f-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4925f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="4925f-118">See also</span></span>

- [<span data-ttu-id="4925f-119">Objetos XName e XNamespace atomizados (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4925f-119">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
