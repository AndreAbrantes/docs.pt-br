---
title: Selecionar nós usando a navegação XPath
description: Saiba como selecionar nós XML no .NET. Use os métodos Modelo de Objeto do Documento (DOM), permitindo que você use a navegação XPath para consultar informações do DOM.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: b6b68d9351431acc6d9ef20276f51ac4d667d325
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734680"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="8d60b-104">Selecionar nós usando a navegação XPath</span><span class="sxs-lookup"><span data-stu-id="8d60b-104">Select Nodes Using XPath Navigation</span></span>

<span data-ttu-id="8d60b-105">O DOM (Document Object Model) XML contém métodos que permitem que você use a navegação da linguagem XPath para consultar informações no DOM.</span><span class="sxs-lookup"><span data-stu-id="8d60b-105">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="8d60b-106">Você pode usar a linguagem XPath para localizar um único nó específico ou todos os nós que correspondam a alguns critérios.</span><span class="sxs-lookup"><span data-stu-id="8d60b-106">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="8d60b-107">Métodos de seleção XPath</span><span class="sxs-lookup"><span data-stu-id="8d60b-107">XPath Select Methods</span></span>  

 <span data-ttu-id="8d60b-108">As classes DOM fornecem dois métodos de seleção XPath: o método <xref:System.Xml.XmlNode.SelectSingleNode%2A> e o método <xref:System.Xml.XmlNode.SelectNodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d60b-108">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="8d60b-109">O método <xref:System.Xml.XmlNode.SelectSingleNode%2A> retorna o primeiro nó que corresponde aos critérios de seleção.</span><span class="sxs-lookup"><span data-stu-id="8d60b-109">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="8d60b-110">O método <xref:System.Xml.XmlNode.SelectNodes%2A> retorna um <xref:System.Xml.XmlNodeList> que contém os nós correspondentes.</span><span class="sxs-lookup"><span data-stu-id="8d60b-110">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="8d60b-111">O exemplo a seguir usa o método <xref:System.Xml.XmlNode.SelectSingleNode%2A> para selecionar o primeiro nó `book`, no qual o sobrenome do autor atende a critérios específicos.</span><span class="sxs-lookup"><span data-stu-id="8d60b-111">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="8d60b-112">O arquivo bookstore.xml (que é fornecido no final deste tópico) é usado como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="8d60b-112">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="8d60b-113">O exemplo a seguir usa o método <xref:System.Xml.XmlNode.SelectNodes%2A> para selecionar todos os nós de livros em que o preço é maior do que um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="8d60b-113">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="8d60b-114">O preço de cada livro na lista selecionada é reduzido programaticamente em dez por cento.</span><span class="sxs-lookup"><span data-stu-id="8d60b-114">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="8d60b-115">Finalmente, o arquivo atualizado é gravado no console.</span><span class="sxs-lookup"><span data-stu-id="8d60b-115">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="8d60b-116">O arquivo bookstore.xml (que é fornecido no final deste tópico) é usado como o arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="8d60b-116">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="8d60b-117">Os exemplos acima iniciam a consulta XPath no elemento de documento.</span><span class="sxs-lookup"><span data-stu-id="8d60b-117">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="8d60b-118">A definição do ponto de partida para a consulta XPath define o nó de contexto, que é o ponto de partida para a consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="8d60b-118">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="8d60b-119">Se você não deseja começar no elemento de documento, mas a partir do primeiro elemento filho do documento, você pode codificar a instrução de seleção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8d60b-119">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="8d60b-120">Todos os objetos <xref:System.Xml.XmlNodeList> são sincronizados com o documento subjacente.</span><span class="sxs-lookup"><span data-stu-id="8d60b-120">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="8d60b-121">Portanto, se você iterar pela lista de nós e modificar o valor de um nó, esse nó também será atualizado no documento de origem.</span><span class="sxs-lookup"><span data-stu-id="8d60b-121">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="8d60b-122">Observe no exemplo anterior que, quando um nó é modificado no <xref:System.Xml.XmlNodeList> selecionado, o documento subjacente também é modificado.</span><span class="sxs-lookup"><span data-stu-id="8d60b-122">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d60b-123">Quando o documento subjacente é modificado, é aconselhável executar novamente a seleção.</span><span class="sxs-lookup"><span data-stu-id="8d60b-123">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="8d60b-124">Se o nó modificado for um que possa fazer com que o nó seja adicionado à lista de nós quando não tiver sido anteriormente, ou que agora faça com que ele seja removido da lista, não haverá nenhuma garantia de que a lista de nós agora esteja exata.</span><span class="sxs-lookup"><span data-stu-id="8d60b-124">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="8d60b-125">Namespaces em expressões XPath</span><span class="sxs-lookup"><span data-stu-id="8d60b-125">Namespaces in XPath Expressions</span></span>  

 <span data-ttu-id="8d60b-126">As expressões XPath podem incluir namespaces</span><span class="sxs-lookup"><span data-stu-id="8d60b-126">XPath expressions can include namespaces.</span></span> <span data-ttu-id="8d60b-127">A resolução de namespace tem suporte com o uso do <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="8d60b-127">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="8d60b-128">Se a expressão XPath incluir um prefixo, o par de prefixo e URI de namespace deverá ser adicionado a <xref:System.Xml.XmlNamespaceManager>, e <xref:System.Xml.XmlNamespaceManager> será passado ao método <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> ou <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29>.</span><span class="sxs-lookup"><span data-stu-id="8d60b-128">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="8d60b-129">Observe que os exemplos de código acima usam <xref:System.Xml.XmlNamespaceManager> para resolver o namespace do documento bookstore.xml.</span><span class="sxs-lookup"><span data-stu-id="8d60b-129">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d60b-130">Se a expressão XPath não incluir um prefixo, presume-se que o URI do namespace seja o namespace vazio.</span><span class="sxs-lookup"><span data-stu-id="8d60b-130">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="8d60b-131">Se o XML incluir um namespace padrão, você ainda deverá adicionar um prefixo e um URI de namespace a <xref:System.Xml.XmlNamespaceManager>; caso contrário, nenhum nó será selecionado.</span><span class="sxs-lookup"><span data-stu-id="8d60b-131">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="8d60b-132">Arquivo de entrada</span><span class="sxs-lookup"><span data-stu-id="8d60b-132">Input File</span></span>  

 <span data-ttu-id="8d60b-133">A seguir está o arquivo bookstore.xml que é usado como o arquivo de entrada nos exemplos deste tópico:</span><span class="sxs-lookup"><span data-stu-id="8d60b-133">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d60b-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d60b-134">See also</span></span>

- [<span data-ttu-id="8d60b-135">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="8d60b-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
