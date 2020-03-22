---
title: Como preencher uma árvore XML com um XmlWriter (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: fecf57eac570a9ca57dd1fe2f7a0b54cd78c33b5
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266996"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="adb0a-102">Como: Preencher uma árvore XML com um XmlWriter (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adb0a-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="adb0a-103">Uma maneira de preencher uma árvore XML é usar <xref:System.Xml.Linq.XContainer.CreateWriter%2A> para criar um <xref:System.Xml.XmlWriter> e escrever no <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="adb0a-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="adb0a-104">A árvore XML é preenchida com todos os nós que são escritos no <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="adb0a-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="adb0a-105">Você normalmente usa este método quando usa [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] com outra classe que espera escrever em um <xref:System.Xml.XmlWriter>, por exemplo, <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="adb0a-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adb0a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="adb0a-106">Example</span></span>  
 <span data-ttu-id="adb0a-107">Um uso possível para <xref:System.Xml.Linq.XContainer.CreateWriter%2A> é ao chamar uma transformação XSLT.</span><span class="sxs-lookup"><span data-stu-id="adb0a-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="adb0a-108">Este exemplo cria uma árvore XML, cria <xref:System.Xml.XmlReader> da árvore XML, cria um novo documento e, em seguida, cria <xref:System.Xml.XmlWriter> para gravar no novo documento.</span><span class="sxs-lookup"><span data-stu-id="adb0a-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="adb0a-109">Ele então chama a transformação XSLT, passando no <xref:System.Xml.XmlReader> e no <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="adb0a-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="adb0a-110">Depois que a transformação for concluída com êxito, a nova árvore XML será preenchida com os resultados da transformação.</span><span class="sxs-lookup"><span data-stu-id="adb0a-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="adb0a-111">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="adb0a-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="adb0a-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="adb0a-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="adb0a-113">Criando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adb0a-113">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
