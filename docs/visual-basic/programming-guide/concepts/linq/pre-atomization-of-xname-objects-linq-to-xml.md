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
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Pré-atomização de objetos XName (LINQ to XML) (Visual Basic)

Uma maneira para melhorar o desempenho em LINQ to XML é pré-compilação atomizar objetos de <xref:System.Xml.Linq.XName> . A pré-atomização significa que você atribui uma cadeia de caracteres a um objeto <xref:System.Xml.Linq.XName> antes de criar a árvore XML usando os construtores das classes <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute>. Em seguida, em vez de passar uma cadeia de caracteres para o construtor, que usaria a conversão implícita de cadeia de caracteres a <xref:System.Xml.Linq.XName>, você passa o objeto inicializado de <xref:System.Xml.Linq.XName> .

Isso melhora o desempenho quando você cria uma grande árvore XML em que os nomes específicos são repetidos. Para fazer isso, você declarar e inicializar objetos de <xref:System.Xml.Linq.XName> antes que você construa a árvore XML e em seguida, usar objetos de <xref:System.Xml.Linq.XName> em vez de especificar cadeias de caracteres para nomes de elementos e atributos. Essa técnica pode produzir ganhos significativos de desempenho se você estiver criando um grande número de elementos ou atributos () com o mesmo nome.

Você deve testar a pré-compilação atomização com seu cenário para decidir se você usar o.

## <a name="example"></a>{1&gt;Exemplo&lt;1}

O exemplo a seguir demonstra este:

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

Este exemplo gera a seguinte saída:

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

O exemplo a seguir mostra a mesma técnica onde o documento XML é em um namespace:

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

Este exemplo gera a seguinte saída:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

O exemplo a seguir é mais semelhante ao que você provavelmente encontrará no mundo real. Nesse exemplo, o conteúdo do elemento é fornecido por uma consulta:

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

O exemplo anterior executa melhor do que o exemplo, em que os nomes não são atomizados passos:

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a>Consulte também

- [Desempenho (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
- [Objetos XName e XNamespace (LINQ to XML) atomáveis (Visual Basic)](atomized-xname-and-xnamespace-objects-linq-to-xml.md)
