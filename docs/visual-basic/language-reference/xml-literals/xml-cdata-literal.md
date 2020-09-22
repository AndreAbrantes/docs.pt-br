---
title: Literal CDATA XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 4447ad6cf0fb251b0d2d1387c109b06d32f69cb8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866097"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="82500-102">Literal CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82500-102">XML CDATA Literal (Visual Basic)</span></span>

<span data-ttu-id="82500-103">Um literal que representa um <xref:System.Xml.Linq.XCData> objeto.</span><span class="sxs-lookup"><span data-stu-id="82500-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82500-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82500-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="82500-105">Partes</span><span class="sxs-lookup"><span data-stu-id="82500-105">Parts</span></span>  

 `<![CDATA[`  
 <span data-ttu-id="82500-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="82500-106">Required.</span></span> <span data-ttu-id="82500-107">Indica o início da seção XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="82500-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="82500-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="82500-108">Required.</span></span> <span data-ttu-id="82500-109">Conteúdo de texto a ser exibido na seção CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="82500-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="82500-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="82500-110">Required.</span></span> <span data-ttu-id="82500-111">Denota o final da seção.</span><span class="sxs-lookup"><span data-stu-id="82500-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82500-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="82500-112">Return Value</span></span>  

 <span data-ttu-id="82500-113">Um objeto <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="82500-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82500-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="82500-114">Remarks</span></span>  

 <span data-ttu-id="82500-115">As seções XML CDATA contêm texto bruto que deve ser incluído, mas não analisado, com o XML que o contém.</span><span class="sxs-lookup"><span data-stu-id="82500-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="82500-116">Uma seção CDATA XML pode conter qualquer texto.</span><span class="sxs-lookup"><span data-stu-id="82500-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="82500-117">Isso inclui caracteres XML reservados.</span><span class="sxs-lookup"><span data-stu-id="82500-117">This includes reserved XML characters.</span></span> <span data-ttu-id="82500-118">A seção XML CDATA termina com a sequência "]] >".</span><span class="sxs-lookup"><span data-stu-id="82500-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="82500-119">Isso implica nos seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="82500-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="82500-120">Você não pode usar uma expressão inserida em um literal XML CDATA porque os delimitadores de expressão inseridos são conteúdo XML CDATA válido.</span><span class="sxs-lookup"><span data-stu-id="82500-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="82500-121">As seções XML CDATA não podem ser aninhadas porque `content` não podem conter o valor "]] >".</span><span class="sxs-lookup"><span data-stu-id="82500-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="82500-122">Você pode atribuir um literal XML CDATA a uma variável ou incluí-lo em um literal de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="82500-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82500-123">Um literal XML pode abranger várias linhas, mas não usa caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="82500-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="82500-124">Isso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82500-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="82500-125">O compilador Visual Basic converte o literal XML CDATA em uma chamada para o <xref:System.Xml.Linq.XCData.%23ctor%2A> Construtor.</span><span class="sxs-lookup"><span data-stu-id="82500-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82500-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82500-126">Example</span></span>  

 <span data-ttu-id="82500-127">O exemplo a seguir cria uma seção CDATA que contém o texto "pode conter \<XML> marcas literais".</span><span class="sxs-lookup"><span data-stu-id="82500-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="82500-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="82500-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="82500-129">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="82500-129">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="82500-130">Literais XML</span><span class="sxs-lookup"><span data-stu-id="82500-130">XML Literals</span></span>](index.md)
- [<span data-ttu-id="82500-131">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82500-131">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
