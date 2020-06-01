---
title: Visão geral do LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: dd41d8607ef3f2e6e6be9a1f3964ef0ae937e2ac
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241832"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="9d0e5-102">Visão geral do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9d0e5-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="9d0e5-103">O LINQ to XML fornece uma interface de programação XML na memória que aproveita a .NET LINQ (Consulta Integrada à Linguagem) Framework.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="9d0e5-104">O LINQ to XML usa os recursos do .NET e pode ser comparado a uma interface de programação XML de Modelo de Objeto do Documento (DOM) atualizada e reprojetada.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="9d0e5-105">O XML tem sido amplamente adotado como um modo de formatar dados em muitos contextos.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="9d0e5-106">Por exemplo, você pode encontrar XML na Web, em arquivos de configuração, em arquivos do Microsoft Office Word e em bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

<span data-ttu-id="9d0e5-107">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é uma abordagem atualizada e redesenhada para a programação com XML.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="9d0e5-108">Ele fornece os recursos de modificação de documentos na memória do Modelo de Objeto do Documento (DOM) e oferece suporte a expressões de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="9d0e5-109">Embora essas expressões de consulta sejam sintaticamente diferentes de XPath, elas oferecem uma funcionalidade semelhante.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="9d0e5-110">Desenvolvedores em LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="9d0e5-110">LINQ to XML Developers</span></span>

<span data-ttu-id="9d0e5-111">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se destina a uma variedade de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-111">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] targets a variety of developers.</span></span> <span data-ttu-id="9d0e5-112">Para um desenvolvedor médio que deseja apenas ter algo concluído, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] torna o XML mais simples ao oferecer uma experiência de consulta que é semelhante ao SQL.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="9d0e5-113">Com apenas um pouco de estudo, os programadores podem aprender a escrever consultas sucintas e eficientes na linguagem de programação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="9d0e5-114">Os desenvolvedores profissionais podem usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para aumentar consideravelmente sua produtividade.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="9d0e5-115">Com o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], eles podem escrever um código menor que seja mais expressivo, mais compacto e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="9d0e5-116">Eles podem usar expressões de consulta de vários domínios de dados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="9d0e5-117">O que é o LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="9d0e5-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="9d0e5-118">é uma interface de programação XML na memória, habilitada para LINQ, que permite trabalhar com XML de dentro das linguagens de programação .NET.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

<span data-ttu-id="9d0e5-119">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é como o DOM (Modelo de Objeto do Documento) no sentido de levar o documento XML para a memória.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-119">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="9d0e5-120">Você pode consultar e modificar o documento e, depois de modificá-lo, pode salvá-lo em um arquivo ou serializá-lo e enviá-lo pela Internet.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="9d0e5-121">Entretanto, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é diferente do DOM: ele proporciona um novo modelo de objeto mais leve e mais simples de se trabalhar, além de aproveitar os recursos de linguagem no C#.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="9d0e5-122">A vantagem mais importante do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é sua integração com LINQ (consulta integrada à linguagem).</span><span class="sxs-lookup"><span data-stu-id="9d0e5-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="9d0e5-123">Essa integração permite que você escreva consultas no documento XML na memória para recuperar coleções de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="9d0e5-124">O recurso de consulta do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é comparável em funcionalidade (embora não em sintaxe) a XPath e XQuery.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="9d0e5-125">A integração do LINQ em C# fornece digitação mais forte, verificação de tempo de compilação e suporte a depurador aprimorado.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-125">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="9d0e5-126">Outra vantagem do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é a capacidade de usar resultados da consulta como parâmetros para construtores de objeto <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute>, o que permite uma abordagem eficiente para a criação de árvores XML.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="9d0e5-127">Essa abordagem, chamada de *construção funcional*, permite que os desenvolvedores transformem com facilidade árvores XML de uma forma em outra.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="9d0e5-128">Por exemplo, você pode ter uma ordem de compra em XML típica, conforme descrito em [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="9d0e5-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="9d0e5-129">Usando o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você poderia executar a consulta a seguir para obter o valor do atributo de número de peça para cada elemento de item na ordem de compra:</span><span class="sxs-lookup"><span data-stu-id="9d0e5-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="9d0e5-130">Isso pode ser regravado no formulário de sintaxe do método:</span><span class="sxs-lookup"><span data-stu-id="9d0e5-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="9d0e5-131">Como outro exemplo, você poderia querer uma lista, classificada por número de peça, dos itens com um valor maior que $ 100.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="9d0e5-132">Para obter essas informações, você poderia executar a seguinte consulta:</span><span class="sxs-lookup"><span data-stu-id="9d0e5-132">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

<span data-ttu-id="9d0e5-133">Outra vez, isso pode ser regravado no formulário de sintaxe do método:</span><span class="sxs-lookup"><span data-stu-id="9d0e5-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="9d0e5-134">Além desses recursos do LINQ, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] o fornece uma interface de programação XML aprimorada.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-134">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="9d0e5-135">Usando o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode:</span><span class="sxs-lookup"><span data-stu-id="9d0e5-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="9d0e5-136">Carregar XML de [arquivos](how-to-load-xml-from-a-file.md) ou [fluxos](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="9d0e5-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="9d0e5-137">Serializar o XML em arquivos ou fluxos.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="9d0e5-138">Crie XML a partir do zero usando a construção funcional.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="9d0e5-139">Consultar o XML usando eixos do tipo XPath.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="9d0e5-140">Manipular a árvore XML na memória usando métodos como <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> e <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="9d0e5-141">Validar árvores XML usando XSD.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="9d0e5-142">Usar uma combinação desses recursos para transformar árvores XML de uma forma em outra.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="9d0e5-143">Criando árvores XML</span><span class="sxs-lookup"><span data-stu-id="9d0e5-143">Creating XML Trees</span></span>

<span data-ttu-id="9d0e5-144">Uma das vantagens mais significativas da programação com [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é que é fácil criar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="9d0e5-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="9d0e5-145">Por exemplo, para criar uma árvore XML pequena, você pode escrever código da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9d0e5-145">For example, to create a small XML tree, you can write code as follows:</span></span>

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
        new XElement("Address",
            new XElement("Street1", "123 Main St"),
            new XElement("City", "Mercer Island"),
            new XElement("State", "WA"),
            new XElement("Postal", "68042")
        )
    )
);
```

<span data-ttu-id="9d0e5-146">Para obter mais informações, consulte [Criando árvores XML (C#)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="9d0e5-146">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d0e5-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d0e5-147">See also</span></span>

- [<span data-ttu-id="9d0e5-148">Referência (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9d0e5-148">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="9d0e5-149">LINQ to XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="9d0e5-149">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="9d0e5-150">LINQ to XML e outras tecnologias XML</span><span class="sxs-lookup"><span data-stu-id="9d0e5-150">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
