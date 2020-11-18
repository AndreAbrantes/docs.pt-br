---
title: Criação de documentos XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: fb92a1fe984014aef9973b821227fbd1c1176a6c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819260"
---
# <a name="xml-document-creation"></a><span data-ttu-id="5015d-102">Criação de documentos XML</span><span class="sxs-lookup"><span data-stu-id="5015d-102">XML Document Creation</span></span>
<span data-ttu-id="5015d-103">Existem duas maneiras de criar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="5015d-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="5015d-104">Uma maneira é criar um **XmlDocument** sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5015d-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="5015d-105">Outra maneira é criar um **XmlDocument** e passar para ele uma XmlNameTable como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5015d-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="5015d-106">O exemplo a seguir mostra como criar um novo **XmlDocument** vazio sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5015d-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="5015d-107">Uma vez criado o documento, você pode carregá-lo com dados de uma cadeia de caracteres, de um fluxo, de uma URL, de um leitor de texto ou de uma classe **XmlReader** derivada usando o método **Load**.</span><span class="sxs-lookup"><span data-stu-id="5015d-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="5015d-108">Existe também outro método de carregamento, o método **LoadXML**, que lê XML de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5015d-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="5015d-109">Para saber mais sobre os vários métodos **Load**, consulte [Ler um documento XML no DOM](reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="5015d-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="5015d-110">Há uma classe chamada **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="5015d-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="5015d-111">Essa classe é uma tabela de objetos atomizados de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5015d-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="5015d-112">Essa tabela fornece uma forma eficiente para que o analisador XML use o mesmo objeto de cadeia de caracteres para todos os nomes repetidos de elementos e de atributos em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="5015d-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="5015d-113">Uma **XmlNameTable** é criada automaticamente quando um documento é criado, como mostrado acima, e carregada com nomes de atributo e de elemento quando o documento é carregado.</span><span class="sxs-lookup"><span data-stu-id="5015d-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="5015d-114">Se você já tiver um documento com uma tabela de nomes, que poderiam ser úteis em outro documento, poderá criar um novo documento usando o método **Load** que tem **XmlNameTable** como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5015d-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="5015d-115">Quando o documento é criado com esse método, ele usa a classe **XmlNameTable** existente com todos os atributos e elementos já carregados para ela de outro documento.</span><span class="sxs-lookup"><span data-stu-id="5015d-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="5015d-116">Ela pode ser usada para comparar nomes de elementos e de atributos de forma mais eficaz.</span><span class="sxs-lookup"><span data-stu-id="5015d-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="5015d-117">Para saber mais sobre a classe **XmlNameTable**, consulte [Comparação de objetos usando XmlNameTable](object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="5015d-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="5015d-118">Para referência, veja <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="5015d-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5015d-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="5015d-119">See also</span></span>

- [<span data-ttu-id="5015d-120">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="5015d-120">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
