---
title: Consultas XPath e namespaces
description: Saiba mais sobre as consultas XPath & namespaces. As consultas XPath conhecem os namespaces em um documento XML & podem usar prefixos de namespace para qualificar nomes de atributos de & de elemento.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: a97ff5afef23c361b1f675d2f07f43b3bc5df299
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818382"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="c9399-104">Consultas XPath e namespaces</span><span class="sxs-lookup"><span data-stu-id="c9399-104">XPath Queries and Namespaces</span></span>
<span data-ttu-id="c9399-105">As consultas XPath reconhecem os namespaces em um documento XML e podem usar prefixos de namespace para qualificar nomes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="c9399-105">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="c9399-106">A qualificação de nomes de elemento e atributo com um prefixo de namespace limita os nós retornados por uma consulta XPath somente aos nós que pertencem a um namespace específico.</span><span class="sxs-lookup"><span data-stu-id="c9399-106">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="c9399-107">Por exemplo, se o `books` de prefixo for mapeado para o namespace `http://www.contoso.com/books`, a seguinte consulta XPath `/books:books/books:book` selecionará somente os elementos `book` no namespace `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="c9399-107">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="c9399-108">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="c9399-108">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="c9399-109">Para usar namespaces em uma consulta XPath, um objeto derivado da interface <xref:System.Xml.IXmlNamespaceResolver> como a classe <xref:System.Xml.XmlNamespaceManager> será construído com o URI e o prefixo do namespace que serão incluídos na consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="c9399-109">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="c9399-110">O objeto <xref:System.Xml.XmlNamespaceManager> pode ser usado na consulta das seguintes maneiras.</span><span class="sxs-lookup"><span data-stu-id="c9399-110">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="c9399-111">O objeto <xref:System.Xml.XmlNamespaceManager> é associado a um objeto <xref:System.Xml.XPath.XPathExpression> existente usando o método <xref:System.Xml.XPath.XPathExpression.SetContext%2A> do objeto <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="c9399-111">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="c9399-112">Você também pode compilar um novo objeto <xref:System.Xml.XPath.XPathExpression> usando o método <xref:System.Xml.XPath.XPathExpression.Compile%2A> estático que usa uma cadeia de caracteres representando a expressão XPath e um objeto <xref:System.Xml.XmlNamespaceManager> como parâmetros, e retorna um novo objeto <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="c9399-112">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="c9399-113">O próprio objeto <xref:System.Xml.XmlNamespaceManager> é passado como um parâmetro para um método da classe <xref:System.Xml.XPath.XPathNavigator> de aceitação juntamente com uma cadeia de caracteres que representa a expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="c9399-113">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="c9399-114">Estes são os métodos da classe <xref:System.Xml.XPath.XPathNavigator> que aceitam um objeto derivado da interface <xref:System.Xml.IXmlNamespaceResolver> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c9399-114">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="c9399-115">O namespace padrão</span><span class="sxs-lookup"><span data-stu-id="c9399-115">The Default Namespace</span></span>  
 <span data-ttu-id="c9399-116">No documento XML a seguir, o namespace padrão com um prefixo vazio é usada para declarar o namespace `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="c9399-116">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="c9399-117">O XPath trata o prefixo vazio como o namespace `null`.</span><span class="sxs-lookup"><span data-stu-id="c9399-117">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="c9399-118">Em outras palavras, somente os prefixos mapeados para os namespaces podem ser usados em consultas XPath.</span><span class="sxs-lookup"><span data-stu-id="c9399-118">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="c9399-119">Isso significa que, se você quiser fazer uma consulta em um namespace em um documento XML, mesmo que ele seja o namespace padrão, será necessário definir um prefixo para ele.</span><span class="sxs-lookup"><span data-stu-id="c9399-119">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="c9399-120">Por exemplo, sem definir um prefixo para o documento XML acima, a consulta XPath `/books/book` não retornará nenhum resultado.</span><span class="sxs-lookup"><span data-stu-id="c9399-120">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="c9399-121">Um prefixo deve ser associado para evitar a ambiguidade durante a consulta de documentos com alguns nós que não estão em um namespace e outros que estão em um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="c9399-121">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="c9399-122">O código a seguir define um prefixo para o namespace padrão e seleciona todos os elementos `book` do namespace `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="c9399-122">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9399-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9399-123">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="c9399-124">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="c9399-124">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="c9399-125">Selecionar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c9399-125">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="c9399-126">Avalia as expressões XPath usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c9399-126">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="c9399-127">Nós compatíveis usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c9399-127">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="c9399-128">Tipos de nós reconhecidos com consultas XPath</span><span class="sxs-lookup"><span data-stu-id="c9399-128">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="c9399-129">Expressões XPath compilados</span><span class="sxs-lookup"><span data-stu-id="c9399-129">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
