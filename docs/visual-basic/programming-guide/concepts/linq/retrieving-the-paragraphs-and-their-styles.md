---
title: Recuperar os parágrafos e seus estilos
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413396"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="95c97-102">Recuperando os parágrafos e seus estilos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95c97-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="95c97-103">Nesse exemplo, nós escrevemos uma consulta que recupera os nós de parágrafo de um documento de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="95c97-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="95c97-104">Também identifica o estilo de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="95c97-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="95c97-105">Essa consulta se baseia na consulta no exemplo anterior, [localizando o estilo de parágrafo padrão (Visual Basic)](finding-the-default-paragraph-style.md), que recupera o estilo padrão da lista de estilos.</span><span class="sxs-lookup"><span data-stu-id="95c97-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="95c97-106">Essa informação é necessária de modo que a consulta pode identificar o estilo dos parágrafos que não têm um estilo definir explicitamente.</span><span class="sxs-lookup"><span data-stu-id="95c97-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="95c97-107">Os estilos de parágrafo são definidos por meio do elemento de `w:pPr` ; se um parágrafo não contém esse elemento, é formatado com o estilo padrão.</span><span class="sxs-lookup"><span data-stu-id="95c97-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="95c97-108">Este tópico explica o significado de algumas partes de consulta, então mostra a consulta como parte de um exemplo completo, que funciona.</span><span class="sxs-lookup"><span data-stu-id="95c97-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c97-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95c97-109">Example</span></span>  
 <span data-ttu-id="95c97-110">A fonte da consulta para recuperar todos os parágrafos em um documento e seus estilos é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="95c97-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="95c97-111">Essa expressão é semelhante à origem da consulta no exemplo anterior, [localizando o estilo de parágrafo padrão (Visual Basic)](finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="95c97-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="95c97-112">A principal diferença é que usa o eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> em vez do eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="95c97-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="95c97-113">A consulta usa o eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> porque em documentos que têm seções, os parágrafos não serão os filhos diretos do elemento do corpo; em vez, os parágrafos serão dois níveis para baixo na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="95c97-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="95c97-114">Usando o eixo de <xref:System.Xml.Linq.XContainer.Descendants%2A> , o código funcionará de mesmo se o documento usa seções.</span><span class="sxs-lookup"><span data-stu-id="95c97-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c97-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95c97-115">Example</span></span>  
 <span data-ttu-id="95c97-116">A consulta usa uma cláusula de `Let` para determinar o elemento que contém o nó de estilo.</span><span class="sxs-lookup"><span data-stu-id="95c97-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="95c97-117">Se não houver nenhum elemento, então `styleNode` é definido como `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="95c97-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="95c97-118">A cláusula de `Let` primeiro usa o eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> para localizar todos os elementos chamados `pPr`, então usa o método de extensão de <xref:System.Xml.Linq.Extensions.Elements%2A> para localizar todos os elementos filho chamados `pStyle`, e finalmente usa o operador padrão de consulta de <xref:System.Linq.Enumerable.FirstOrDefault%2A> para converter a um único.</span><span class="sxs-lookup"><span data-stu-id="95c97-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="95c97-119">Se a coleção estiver vazia, `styleNode` é definido como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="95c97-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="95c97-120">Este é um idioma útil para procurar o nó descendente de `pStyle` .</span><span class="sxs-lookup"><span data-stu-id="95c97-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="95c97-121">Observe que se o nó filho de `pPr` não existir, o código faz ou falhas lançando uma exceção; em vez disso, `styleNode` é definido como `Nothing`, que é o comportamento desejado desta cláusula de `Let` .</span><span class="sxs-lookup"><span data-stu-id="95c97-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="95c97-122">A consulta em uma coleção de um tipo anônimo com dois membros, `StyleName` e `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="95c97-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c97-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95c97-123">Example</span></span>  
 <span data-ttu-id="95c97-124">Este exemplo processa um documento de WordprocessingML, recuperando os nós de parágrafo de um documento de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="95c97-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="95c97-125">Também identifica o estilo de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="95c97-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="95c97-126">Este exemplo cria nos exemplos anteriores neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="95c97-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="95c97-127">A nova consulta é chamada nos comentários no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="95c97-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="95c97-128">Você pode encontrar instruções para criar o documento de origem para este exemplo na [criação do documento Office Open XML de origem (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="95c97-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="95c97-129">Este exemplo usa as classes encontradas no assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="95c97-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="95c97-130">Ele usa tipos no namespace <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="95c97-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="95c97-131">Este exemplo produz a saída a seguir quando aplicada ao documento descrito em [criando o documento Office Open XML de origem (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="95c97-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="95c97-132">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="95c97-132">Next Steps</span></span>  
 <span data-ttu-id="95c97-133">No próximo tópico, [recuperando o texto dos parágrafos (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), você criará uma consulta para recuperar o texto dos parágrafos.</span><span class="sxs-lookup"><span data-stu-id="95c97-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c97-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="95c97-134">See also</span></span>

- [<span data-ttu-id="95c97-135">Tutorial: manipulando conteúdo em um documento do WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95c97-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
